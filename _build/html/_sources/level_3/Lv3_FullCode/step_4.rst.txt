예열 및 디스플레이 표시
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. raw:: html

    <style> 
    .orangecircle {color:#ff5300; font-size:20px} 
    .blackcircle {color:black; font-size:20px} 
    .bluecircle {color:#3172f4; font-size:20px}
    .skybluecircle {color:#00FFFF; font-size:20px}
    .yellowcircle {color:#fbbc05; font-size:20px}
    .subtitle {color:black; font-weight:bold; font-size:28px}
    .subtitlesmall {color:black; font-weight:bold; font-size:24px}
    .blackbold {color:black; font-weight:bold;}
    .redbold {color:red; font-weight:bold;}
    </style>

.. role:: orangecircle
.. role:: blackcircle
.. role:: bluecircle
.. role:: skybluecircle
.. role:: yellowcircle
.. role:: subtitle
.. role:: subtitlesmall
.. role:: blackbold
.. role:: redbold

| 재료별로 재료명, 목표온도, 목표속도를 디스플레이에 표시하는 것을 완성하였습니다. 이 단계에서는 :blackbold:`목표온도가 설정되면, 현재온도와 비교하고 차이가 있으면 예열하는 것을 구현` 하는 것이 목표입니다.
| 
| ※ 지금부터는 전체코드를 계속해서 보여주는 것은 코드가 길기 때문에 작성된 코드에서 추가될 부분만 설명드리겠습니다.
|
| 예열이 되게 하는 방법은 PID 제어를 적용하여, 온도유지를 원활하게 하도록 하겠습니다.
| PID 제어의 코드는 :ref:`온도 챕터 <targetL3C9S4_0>` 에 설명되어 있습니다.
|

.. code-block:: c++
    :linenos:

    float Kp=36, Ki=2.5, Kd=0.625, dT = 0.05;
    int16_t error, previousError = 0; // 오차 변수
    float integral, derivaitve = 0;   // 적분 미분 변수

    /*
     * pid 계산을 하고, 결과값을 HEATER_EN 핀에 적용
     */
    void getPIDoutput(int targetTemp, int actualValue)
    {            
        float outputValue;
            
        //설정온도에 도달하기 10도 전일때부터 PID 제어 시작
        if(curTemp < setTemperature - 10)
        {
            outputValue = 255;
        }
        else
        {
            // 에러 값 저장 
            error      = targetTemp - actualValue;

            // 적분 값 저장
            integral   = integral + (float)error*dT;

            // 미분 값 저장
            derivaitve = ((float)error - (float)previousError)/dT;
            previousError = error;

            // PID 계산
            outputValue = Kp*error + Ki*integral + Kp*derivaitve;

            // output 값이 0~255 범위를 벗어나면 최대, 최소 값을 대신 저장
            if(outputValue > 255)
            {
                outputValue = 255;
            }
            else if(outputValue <0)
            {
                outputValue = 0;
            }

            // outputValue 가 0이라면 예열이 되지 않음으로, isHeating 변수를 false로 저장
            if(outputValue == 0)
            {
                isHeating = false;
            }
            else
            {
                isHeating = true;
            }
        }
        // 계산된 결과값을 디지털 9번핀에 analogWrite 로 입력
        analogWrite(HEATER_EN,outputValue);
    }

|
| 코드 자체는 온도 챕터에서 배웠던 것과 유사합니다.
| 추가해야될 코드는 예열온도를 디스플레이에 표시하는 것 입니다.
|
| targetTemp가 변경될 때 마다 integral 값은 0으로 리셋해주어야 정확한 값을 얻을 수 있습니다.
| 
| 설정 온도를 표시하는 것은 큰 문제가 없습니다만, 현재 온도를 표시하는 것은 문제가 있습니다.
| 이전 단계에서 현재 온도를 표시하는 좌표를 0,16 이라고 설정하였습니다.
| 이 좌표 자체는 낮은 온도에서 높은 온도로 예열하는 경우에는 문제가 되지 않습니다.
| 반대로 높은 온도에서 낮은 온도로 냉각할 경우 아래와 문제가 발생합니다.
|

.. image:: ../../images/Lv3/Chapter_11/Step4_1.gif
   :width: 600
   :align: center

|
| 위의 그림은 105도에서 97도까지 냉각될 때, 현재 코드로 문제가 발생하는 부분입니다.
| 자리수가 달라서 100에서 99로 변경될 때 맨 뒤의 0이 지워지지 않습니다.
| 이 문제를 해결하는 방법은 여러가지가 있지만, 여기에서는 간단하게 해결해보겠습니다.
| 아마 여유가 있으시면, 해결방법을 스스로 찾아보시기 바립니다.
| 

.. toggle::

    .. image:: ../../images/Lv3/Chapter_11/Step4_2.gif
        :width: 600
        :align: center

    | 우리는 위와 같이 문제를 해결해보려 합니다. 2자리수일 때 앞에 숫자 0을 붙여주는 방법입니다.
    | 이를 한번에 해결해주는 함수도 있지만, 간단하게 하지 않고, 위 문제를 해결하는 코드를 작성해봅니다.

| 
| 숫자가 100 이하일 경우, 10 이하일 경우에 따라 문자열에 저장하기전 0을 추가해주는 방법입니다.

.. code-block:: c++
    :linenos:

    // result 는 int형 변수
    // strToShow 는 String형 변수
    if(result < 10)
    {
        strToShow = "00" + String(result);
    }
    else if(result < 100)
    {
        strToShow = "0" + String(result);
    }
    else
    {
        strToShow = String(result);
    }

    // 디스플레이에 strToShow 를 표시
    showTextToScreen(0,16,strToShow);

|
| result < 10 를 확인하는 조건을 먼저 확인을 해야 합니다. result < 100 의 조건에는 result < 10 이어도 참이 될 수 있기 때문입니다.
| String(result) 는 result 의 값을 문자열로 변경해주는 함수입니다.
| 이 코드는 getTemperature 함수에 포함되야 합니다.
|
| 이번 단계에서 PID 제어와 디스플레이에 현재온도를 표시해주는 코드를 추가하여 전체 코드를 작성합니다.


.. code-block:: c++
        :linenos:

        #include "ssd1306.h" // 라이브러리 포함

        #define BTN_A           8      // A버튼
        #define BTN_B           7      // B버튼
        #define BTN_C           11     // C버튼
        #define BTN_D           12     // D버튼

        #define MOTOR_EN        5      // 모터 활성화 핀
        #define MOTOR_DIR       6      // 모터 방향 핀
        #define MOTOR_SPEED     10     // 모터 속도 핀

        #define HEATER_EN       9      // 열선 핀

        #define TEMP_IN         A0     // 온도 읽는 핀

        #define VALUE_TEMPTB    0      // 온도 테이블의 신호 값 인덱스
        #define CELSIUS_TEMPTB  1      // 온도 테이블의 온도 값 인덱스        

        #define MATERIAL_COUNT  3      // material 구조체 배열의 갯수

        String strToShow;              // 디스플레이에 보여줄 문자열을 저장하는 변수

        bool isHeating = false; // 온도가 목표보다 높은지 확인하는 bool 변수
        bool isNeedUpdateScreen = true;      // 업데이트가 필요한지 확인하는 bool 변수 생성
        bool isPressedC_BTN, isPressedD_BTN; // 버튼이 눌러져 있는지 확인하는 bool 변수 생성

        int curTemp = 0; // 현재온도

        long timeInterval  = millis(); // 50ms 에 1회씩 작동하기 위한 시간 변수

        int material_index = 0;        // 재료 구조체 배열의 위치를 가리키는 인덱스
        int setTemperature = 0;        // 설정된 온도   

        // 온도, 속도, 재료명을 포함한 구조체 선언
        struct setting {
            int temperature;
            char* materialName;
        };

        struct setting materials[] = {{0, "OFF"}, {60, "PCL"}, {200, "PLA"}};

        /*
         *  온도 테이블 배열
         *  첫번째 항목은 신호 값, 두번째 항목은 온도 값
         */
        int temptable[23][2] = {
            {1023,0},
            {1022,10},
            {1020,20},
            {1016,30},
            {1011,40},
            {1009,50},
            {1006,60},
            {1004,70},
            {1000,80},
            {990,90},
            {983,100},
            {976,110},
            {972,120},
            {964,130},
            {955,140},
            {942,150},
            {929,160},
            {910,170},
            {895,180},
            {864,190},
            {839,200},
            {800,210},
            {744,220}
        };

        /*
         * 입력받은 문자를 디스플레이 좌표에 표시         
         */
        void showTextToScreen(int x, int y, String text)
        {
            text = text + "\n";
            char ch[10];
            text.toCharArray(ch,text.length());
            ssd1306_printFixedN(x, y, ch, STYLE_NORMAL, FONT_SIZE_2X);
        }

        /*
         * 온도를 읽고, 정확한 온도로 계산 후 결과 값을 화면에 표시하고 반환하는 함수
         * VALUE_TEMPTB = 0, CELSIUS_TEMPTB = 1 으로 온도표의 각 항목을 지시함
         */
        int getTemperature()
        {  
            float ratioTemp;
            float tempADU = analogRead(A0);
            int result;
            
            for(int i=1; i<23; i++){
                if(tempADU >= temptable[i][VALUE_TEMPTB])
                {      
                    ratioTemp = (tempADU - temptable[i][VALUE_TEMPTB])/(temptable[i-1][VALUE_TEMPTB] - temptable[i][VALUE_TEMPTB]);

                    result = temptable[i][CELSIUS_TEMPTB] - ratioTemp*(temptable[i][CELSIUS_TEMPTB] - temptable[i-1][CELSIUS_TEMPTB]);

                    if(result < 10)
                    {
                        strToShow = "00" + String(result);
                    }
                    else if(result < 100)
                    {
                        strToShow = "0" + String(result);
                    }
                    else
                    {
                        strToShow = String(result);
                    }

                    showTextToScreen(0,16,strToShow);
                            
                    return result;
                }
            }

            return ;
        }

        float Kp=36, Ki=2.5, Kd=0.625, dT = 0.05;
        int16_t error, previousError = 0; // 오차 변수
        float integral, derivaitve = 0;   // 적분 미분 변수

        /*
        * pid 계산을 하고, 결과값을 HEATER_EN 핀에 적용
        */
        void getPIDoutput(int targetTemp, int actualValue)
        {            
            float outputValue;

            //설정온도에 도달하기 10도 전일때부터 PID 제어 시작            
             if(curTemp < setTemperature - 10)
            {
                outputValue = 255;
            }
            else
            {
                // 에러 값 저장 
                error      = targetTemp - actualValue;

                // 적분 값 저장
                integral   = integral + (float)error*dT;

                // 미분 값 저장
                derivaitve = ((float)error - (float)previousError)/dT;
                previousError = error;

                // PID 계산
                outputValue = Kp*error + Ki*integral + Kp*derivaitve;

                // output 값이 0~255 범위를 벗어나면 최대, 최소 값을 대신 저장
                if(outputValue > 255)
                {
                    outputValue = 255;
                }
                else if(outputValue <0)
                {
                    outputValue = 0;
                }

                // outputValue 가 0이라면 예열이 되지 않음으로, isHeating 변수를 false로 저장
                if(outputValue == 0)
                {
                    isHeating = false;
                }
                else
                {
                    isHeating = true;
                }
            }
            // 계산된 결과값을 디지털 9번핀에 analogWrite 로 입력
            analogWrite(HEATER_EN,outputValue);
        }

        /*
         * 버튼이 눌러졌는지 확인하고, 해당버튼에 맞는 코드 실행
         */
        void checkBtnPressed()
        {
            // C버튼이 눌리고, D버튼이 눌리지 않았을 경우 실행
            if(!digitalRead(BTN_C) && digitalRead(BTN_D))
            {
                // C 버튼이 눌러져 있으면(isPressedC_BTN 가 true), 아래 코드 건너뜀
                if(!isPressedC_BTN)
                {
                    // 구조체 배열의 인덱스로 사용될 변수 값 1 증가
                    material_index++;
                    if(material_index > MATERIAL_COUNT-1)
                    {
                        material_index = 0;
                    }        

                    // 디스플레이 업데이트를 할 수 있도록 변수 변경
                    isNeedUpdateScreen = true;

                    // 버튼 상태 변수 변경
                    isPressedC_BTN = true;

                    // 적분 값 리셋
                    integral = 0;
                }
            }
            // D버튼이 눌리고, C버튼이 눌리지 않았을 경우 실행
            else if(digitalRead(BTN_C) && !digitalRead(BTN_D))
            {
                // D 버튼이 눌러져 있으면(isPressedD_BTN 가 true), 아래 코드 건너뜀
                if(!isPressedD_BTN)
                {
                    // 구조체 배열의 인덱스로 사용될 변수 값 1 감소
                    material_index--;
                    if(material_index < 0)
                    {
                        material_index = MATERIAL_COUNT-1;
                    }

                    // 디스플레이 업데이트를 할 수 있도록 변수 변경
                    isNeedUpdateScreen = true;

                    // 버튼 상태 변수 변경
                    isPressedD_BTN = true;

                    // 적분 값 리셋
                    integral = 0;
                }
            }
            else
            {
                // C, D 버튼 모두 눌리지 않을 경우, 변수 값 변경
                isPressedC_BTN = false;
                isPressedD_BTN = false;
            }
            
        }

        /*
         * 화면에 표시될 재료명, 목표속도, 목표온도를 업데이트
         */
        void updateMaterial(int index)
        {   
            // isNeedUpdate 변수가 false 이면 함수를 종료함
            if(!isNeedUpdateScreen) return;

            // 목표 온도, 속도 항목에 현재 인덱스의 구조체 값을 저장
            setTemperature = materials[index].temperature;
            setMotorSpeed  = materials[index].motorSpeed;

            // 화면 클리어
            ssd1306_clearScreen();

            // 화면에 목표 온도, 재료 명, 속도를 표시
            // 재료명은 좌표 0,0 에 표시
            // 목표 온도는 좌표 52, 16 에 표시
            strToShow = materials[index].materialName;
            showTextToScreen(0,0, strToShow);

            strToShow = "/" + String(setTemperature);
            showTextToScreen(52,16,strToShow);

            // 화면을 계속해서 업데이트 하지 않도록 방지하는 bool 변수 변경
            isNeedUpdateScreen = false;
        }

        void setup() 
        {
            pinMode(BTN_A, INPUT_PULLUP);  
            pinMode(BTN_B, INPUT_PULLUP);  
            pinMode(BTN_C, INPUT_PULLUP);  
            pinMode(BTN_D, INPUT_PULLUP);  

            pinMode(MOTOR_EN, OUTPUT);         
            pinMode(MOTOR_DIR, OUTPUT); 
            pinMode(MOTOR_SPEED, OUTPUT);        

            pinMode(HEATER_EN, OUTPUT); 

            digitalWrite(MOTOR_EN, HIGH); // 모터 활성화

            ssd1306_128x32_i2c_init(); // 32로 변경
            ssd1306_fillScreen(0x00);  // 화면 초기화
            ssd1306_setFixedFont(ssd1306xled_font6x8); // 폰트 설정
            ssd1306_flipHorizontal(1); // x 화면 대칭 회전
            ssd1306_flipVertical(1);   // y 화면 대칭 회전
        }

        void loop() 
        {
            if(millis() - timeInterval > 50)
            {
                curTemp = getTemperature();
                updateMaterial(material_index);
                checkBtnPressed();
                getPIDoutput(setTemperature, curTemp);

                timeInterval = millis();
            }
        }