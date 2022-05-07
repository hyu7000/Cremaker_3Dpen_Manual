재료별 리스트
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

| 온도를 디스플레이에 표시하는 것 까지 완료하였습니다. 이제는 :blackbold:`설정 온도를 재료별로 리스트를 만들고, 버튼을 누르면 설정바뀌고 화면에 표시하는 코드를 작성하는 것` 이 목표입니다.
| 먼저 재료별로 온도, 속도 항목을 포함할 수 있는 구조체를 선언과 초기화를 해주는 코드를 추가합니다.
|

.. code-block:: c++
        :linenos:

        int material_index = 0; // 재료 구조체 배열의 위치를 가리키는 인덱스
        int setTemperature = 0; // 설정된 온도
        int setMotorSpeed  = 0; // 설정된 모터 속도

        struct setting {
            int temperature;
            int motorSpeed;
            char* materialName;
        };

        struct setting materials[] = {{0, 0, "OFF"}, {60, 100, "PCL"}, {200, 90,"PLA"}};

| 구조체에는 서로 다른 자료형을 포함할 수 있습니다. 따라서 구조체 배열을 통해 
| OFF 일 경우 설정온도와 속도가 0 
| PCL 재료일 경우 온도는 50, 속도는 100
| PLA 재료일 경우 온도는 200, 속도는 90
| 으로 설정이 입력된 것입니다.

|
| 필요한 변수들도 추가로 작성되었습니다. 구조체의 값을 저장할 전역변수를 선언하였습니다. 
| 위의 코드를 이전 스텝의 코드에 추가하면, 아래와 같습니다.
|

.. code-block:: c++
        :linenos:

        #include "ssd1306.h" // 라이브러리 포함

        #define BTN_A           8     // A버튼
        #define BTN_B           7     // B버튼
        #define BTN_C           11    // C버튼
        #define BTN_D           12    // D버튼

        #define MOTOR_EN        5     // 모터 활성화 핀
        #define MOTOR_DIR       6     // 모터 방향 핀
        #define MOTOR_SPEED     10    // 모터 속도 핀

        #define HEATER_EN       9     // 열선 핀

        #define TEMP_IN         A0    // 온도 읽는 핀

        #define VALUE_TEMPTB    0     // 온도 테이블의 신호 값 인덱스
        #define CELSIUS_TEMPTB  1     // 온도 테이블의 온도 값 인덱스        

        #define MATERIAL_COUNT  3     // material 구조체 배열의 갯수

        String strToShow; // 디스플레이에 보여줄 문자열을 저장하는 변수

        bool isHeating = false; // 온도가 목표보다 높은지 확인하는 bool 변수

        int curTemp = 0; // 현재온도

        long timeInterval  = millis(); // 50ms 에 1회씩 작동하기 위한 시간 변수

        int material_index = 0; // 재료 구조체 배열의 위치를 가리키는 인덱스
        int setTemperature = 0; // 설정된 온도
        int setMotorSpeed  = 0; // 설정된 모터 속도

        // 온도, 속도, 재료명을 포함한 구조체 선언
        struct setting {
            int temperature;
            int motorSpeed;
            char* materialName;
        };

        struct setting materials[] = {{0, 0, "OFF"}, {60, 100, "PCL"}, {200, 90,"PLA"}};

        /*
         *  온도 테이블 배열
         *  첫번째 항목은 신호 값, 두번째 항목은 온도 값
         */
        int temptable[23][2] = {
            {1023,0},
            {1008,10},
            {994,20},
            {990,30},
            {985,40},
            {983,50},
            {981,60},
            {978,70},
            {975,80},
            {965,90},
            {959,100},
            {952,110},
            {948,120},
            {941,130},
            {932,140},
            {920,150},
            {908,160},
            {890,170},
            {875,180},
            {845,190},
            {820,200},
            {790,210},
            {765,220}
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
         * 아날로그 A0 핀의 신호 값을 디지털 9번핀(열선)이 HIGH인 상태에서 체크하도록 하는 함수
         */
        int checkA0()
        {
            int tempValueA0 = 0;

            digitalWrite(9, HIGH); // 예열 시작
            delay(1);

            tempValueA0 = analogRead(A0); // 아날로그 신호 값을 tempValueA0 저장

            if(!isHeating)
            {
                digitalWrite(9, LOW); // 예열 종료
            }

            return tempValueA0;
        }

        /*
         * 온도를 읽고, 정확한 온도로 계산 후 결과 값을 화면에 표시하고 반환하는 함수
         * VALUE_TEMPTB = 0, CELSIUS_TEMPTB = 1 으로 온도표의 각 항목을 지시함
         */
        int getTemperature()
        {  
            float ratioTemp;
            float tempADU = checkA0();
            int result;
            
            for(int i=1; i<23; i++){
                if(tempADU >= temptable[i][VALUE_TEMPTB])
                {      
                    ratioTemp = (tempADU - temptable[i][VALUE_TEMPTB])/(temptable[i-1][VALUE_TEMPTB] - temptable[i][VALUE_TEMPTB]);

                    result = temptable[i][CELSIUS_TEMPTB] - ratioTemp*(temptable[i][CELSIUS_TEMPTB] - temptable[i-1][CELSIUS_TEMPTB]);

                    strToShow = String(result);

                    showTextToScreen(0,16,strToShow);
                            
                    return result;
                }
            }

            return ;
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

                timeInterval = millis();
            }
        }

|
| 구조체 선언과 초기화를 하였고, getTemperature 함수의 온도가 표시되는 좌표 위치도 조정하였습니다.
| 이어서 materials 의 값들을 디스플레이에 표시해보도록 하고 
| materials 의 현재 인덱스의 값을 디스플레이에 표시해주는 함수를 만들어 보겠습니다.
| ※ 작성된 코드가 길기 때문에 추가할 함수만 따로 작성합니다.
|

.. code-block:: c++
        :linenos:

        // 업데이트가 필요한지 확인하는 bool 변수 생성
        bool isNeedUpdateScreen = true;

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
            // 목표 속도는 좌표 80, 0 에 표시
            // 목표 온도는 좌표 52, 16 에 표시
            // 온도 단위인 °C는 좌표 91, 16 에 표시
            strToShow = materials[index].materialName;
            showTextToScreen(0,0, strToShow);

            strToShow = String(setMotorSpeed) + "%";
            showTextToScreen(80,0, strToShow);

            strToShow = "/" + String(setTemperature);
            showTextToScreen(52,16,strToShow);

            // 화면을 계속해서 업데이트 하지 않도록 방지하는 bool 변수 변경
            isNeedUpdateScreen = false;
        }

|
| 위 함수는 isNeedUpdate 변수가 true 일 때마다 화면의 문자들을 현재의 값으로 변경해줍니다.
| materials 구조체에서 현재 index의 값을 목표 온도, 목표 속도 변수에 저장합니다.
| isNeedUpdate 는 버튼을 누를 때마다 변경되게 해야합니다. 따라서 버튼을 누르면 isNeedUpdate 변수와 updateMaterial 함수의 index 매개변수로 전달될 변수를 변경해주어야 합니다.
| C, D 버튼을 누를 때 마다 변경하도록 합니다.
|

.. code-block:: c++
        :linenos:    

        // 버튼이 눌러져 있는지 확인하는 bool 변수 생성
        bool isPressedC_BTN, isPressedD_BTN;

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
                }
            }
            else
            {
                // C, D 버튼 모두 눌리지 않을 경우, 변수 값 변경
                isPressedC_BTN = false;
                isPressedD_BTN = false;
            }
            
        }

|
| 버튼이 눌러졌는지 체크하는 함수를 작성하였습니다. 추후 A,B 버튼에 대한 코드도 작성이 되겠지만, 이번 단계에서는 C,D 버튼에 해당되는 코드만 작성하였습니다.
| 버튼이 눌러져 있는 경우에도 계속해서 코드가 실행되면 안되니, bool 변수를 추가하였습니다.
| 또한 구조체의 배열 인덱스를 증감시키고, isNeedUpdateScreen 변수의 값을 변경시켜, loop의 코드가 반복수행 하면서 디스플레이를 업데이트 시킵니다.
|
| 그렇다면, 코드를 합치고, 이번 단계에서의 최종 코드를 작성해보겠습니다.

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
        int setMotorSpeed  = 0;        // 설정된 모터 속도        

        // 온도, 속도, 재료명을 포함한 구조체 선언
        struct setting {
            int temperature;
            int motorSpeed;
            char* materialName;
        };

        struct setting materials[] = {{0, 0, "OFF"}, {60, 100, "PCL"}, {200, 90,"PLA"}};

        /*
         *  온도 테이블 배열
         *  첫번째 항목은 신호 값, 두번째 항목은 온도 값
         */
        int temptable[23][2] = {
            {1023,0},
            {1008,10},
            {994,20},
            {990,30},
            {985,40},
            {983,50},
            {981,60},
            {978,70},
            {975,80},
            {965,90},
            {959,100},
            {952,110},
            {948,120},
            {941,130},
            {932,140},
            {920,150},
            {908,160},
            {890,170},
            {875,180},
            {845,190},
            {820,200},
            {790,210},
            {765,220}
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
         * 아날로그 A0 핀의 신호 값을 디지털 9번핀(열선)이 HIGH인 상태에서 체크하도록 하는 함수
         */
        int checkA0()
        {
            int tempValueA0 = 0;

            digitalWrite(9, HIGH); // 예열 시작
            delay(1);

            tempValueA0 = analogRead(A0); // 아날로그 신호 값을 tempValueA0 저장

            if(!isHeating)
            {
                digitalWrite(9, LOW); // 예열 종료
            }

            return tempValueA0;
        }

        /*
         * 온도를 읽고, 정확한 온도로 계산 후 결과 값을 화면에 표시하고 반환하는 함수
         * VALUE_TEMPTB = 0, CELSIUS_TEMPTB = 1 으로 온도표의 각 항목을 지시함
         */
        int getTemperature()
        {  
            float ratioTemp;
            float tempADU = checkA0();
            int result;
            
            for(int i=1; i<23; i++){
                if(tempADU >= temptable[i][VALUE_TEMPTB])
                {      
                    ratioTemp = (tempADU - temptable[i][VALUE_TEMPTB])/(temptable[i-1][VALUE_TEMPTB] - temptable[i][VALUE_TEMPTB]);

                    result = temptable[i][CELSIUS_TEMPTB] - ratioTemp*(temptable[i][CELSIUS_TEMPTB] - temptable[i-1][CELSIUS_TEMPTB]);

                    strToShow = String(result);

                    showTextToScreen(0,16,strToShow);
                            
                    return result;
                }
            }

            return ;
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
            // 목표 속도는 좌표 80, 0 에 표시
            // 목표 온도는 좌표 52, 16 에 표시
            // 온도 단위인 °C는 좌표 91, 16 에 표시
            strToShow = materials[index].materialName;
            showTextToScreen(0,0, strToShow);

            strToShow = String(setMotorSpeed) + "%";
            showTextToScreen(80,0, strToShow);

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

                timeInterval = millis();
            }
        }