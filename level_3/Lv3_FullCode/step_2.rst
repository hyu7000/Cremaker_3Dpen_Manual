온도 표시
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

| 온도에 대해서 알아본 것과 디스플레이를 함께 적용하여 :blackbold:`온도와 현재 설정을 디스플레이로 보여주도록` 구현하는 것이 목표입니다.
|

| 먼저 필요한 온도 테이블 배열을 추가하도록 하겠습니다. 

.. code-block:: c++
        :linenos: 

        #include "ssd1306.h" // 라이브러리 포함

        #define BTN_A       8     // A버튼
        #define BTN_B       7     // B버튼
        #define BTN_C       11    // C버튼
        #define BTN_D       12    // D버튼

        #define MOTOR_EN    5     // 모터 활성화 핀
        #define MOTOR_DIR   6     // 모터 방향 핀
        #define MOTOR_SPEED 10    // 모터 속도 핀

        #define HEATER_EN   9     // 열선 핀

        #define TEMP_IN     A0    // 온도 읽는 핀

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

        }

| 이어서 디스플레이에 글자를 표시하는 코드를 작성해야 합니다. 이 코드는 작성해놓으면 자주 사용될것 같으니 함수로 만들어 줍니다.

.. code-block:: c++
    :linenos: 

    void showTextToScreen(int x, int y, String text)
    {
        text = text + "\n";
        char ch[10];
        text.toCharArray(ch,text.length());
        ssd1306_printFixedN(x, y, ch, STYLE_NORMAL, FONT_SIZE_2X);
    }

| 디스플레이의 어디 부분에 표시될지를 x, y로 결정하고, 문자는 text 변수로 설정합니다.
|
| 위 코드에 이 함수를 추가하고, 온도를 읽고 디스플레이에 표시하는 코드를 작성해봅니다.
| 아래 코드에서는 온도를 읽는 부분도 함수로 추가하였습니다.

.. toggle::

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

        String strToShow; // 디스플레이에 보여줄 문자열을 저장하는 변수

        int curTemp = 0; // 현재온도

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
         * checkA0 함수로 온도를 읽고, 정확한 온도로 계산 후 
         * 결과 값을 화면에 표시하고 반환하는 함수
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

                    strToShow = String(result);

                    showTextToScreen(0,0,strToShow);
                            
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
            curTemp = getTemperature();
        }

|
| getTemperature 로 온도를 계산하는 함수를 따로 만들었기 때문에 마지막 loop 함수는 간단해 졌습니다.
| 온도 챕터에서 작업했던 코드와 마찬가지로 온도측정 함수를 따로 작성하고, bool isHigherTemp 변수를 추가하였습니다.
| 아래는 업로드를 한 결과 입니다.
|

.. toggle::
    
    .. image:: ../../images/Lv3/Chapter_11/Step2_1.gif
        :width: 600
        :align: center

    |
    | 위 영상과 같이 숫자가 너무 빨리 바뀌고, 일정하지 않은 점이 있습니다. 

| loop의 2개의 함수를 50ms 마다 1번씩 작동하도록 작성해봅니다.
|

.. toggle::

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

        String strToShow; // 디스플레이에 보여줄 문자열을 저장하는 변수

        bool isHeating = false; // 온도가 목표보다 높은지 확인하는 bool 변수

        int curTemp = 0; // 현재온도

        long timeInterval = millis(); // 50ms 에 1회씩 작동하기 위한 시간 변수

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

                    strToShow = String(result);

                    showTextToScreen(0,0,strToShow);
                            
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

    | 아직도 빠르긴 하지만 그나마 알아볼 수 있는 정도가 되었습니다.