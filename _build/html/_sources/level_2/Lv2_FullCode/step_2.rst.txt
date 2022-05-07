예열 상태 표시
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

| 온도에 대해서 알아본 것과 디스플레이를 함께 적용하여 :blackbold:`예열을 하고, 예열 상태를 디스플레이로 보여주도록` 구현하는 것이 목표입니다.
|

| 먼저 현재 상태가 예열중인지 아닌지를 판단하는 변수가 필요함으로 bool 변수를 코드에 추가합니다.
| 또한 전원을 On 하였을 경우에 "cremaker" 문자가 표시되도록 하면 다음과 같은 코드가 됩니다.

.. code-block:: c++
    :emphasize-lines: 3
    :linenos: 

    #include "ssd1306.h" // 라이브러리 포함

    bool isPressedBtn = false; // 버튼이 눌러졌는지 확인하는 bool 변수
    bool isHeating = false; // 온도가 목표보다 높은지 확인하는 bool 변수

    void setup() 
    {
        // put your setup code here, to run once:
        pinMode(8,INPUT_PULLUP);   // A 버튼 
        pinMode(7,INPUT_PULLUP);   // B 버튼 
        pinMode(11,INPUT_PULLUP);  // C 버튼 
        pinMode(12,INPUT_PULLUP);  // D 버튼 

        pinMode(5,OUTPUT);         // 모터 활성화
        pinMode(6,OUTPUT);         // 모터 방향
        pinMode(10,OUTPUT);        // 모터 속도

        pinMode(9,OUTPUT);         // 열선

        ssd1306_128x32_i2c_init(); // 32로 변경
        ssd1306_fillScreen(0x00);  // 화면 초기화
        ssd1306_setFixedFont(ssd1306xled_font6x8); // 폰트 설정
        ssd1306_flipHorizontal(1); // x 화면 대칭 회전
        ssd1306_flipVertical(1);   // y 화면 대칭 회전

        // "cremaker" 문자표시
        ssd1306_printFixedN (15, 0, "cremaker", STYLE_NORMAL, FONT_SIZE_2X); 
    }

    void loop() 
    {
        // put your main code here, to run repeatedly:

    }

| 
| 위의 코드를 아래 기능이 작동되도록 코드륵 작성해봅니다.
| 1. C 버튼을 누르면 예열이 되도록 하고, 디스플레이에 Heating 표시
| 2. D 버튼을 누르면 예열이 멈추게 하고, 디스플레이에 OFF 표시
| 3. 온도는 60도를 유지
|
| 온도 관련 함수, 코드들은 :ref:`여기 <targetL2C9S2_2_5>` 에서 확인하세요.
| 버튼이 길게 눌러질 때 디스플레이가 :ref:`흐려지는 것을 방지하는 코드 <targetL2C10S1_0>` 를 확인하세요.
| Heating과 OFF 문자의 위치는 원하는 위치로 설정합니다. (다만 너무 구석이면 글자가 짤릴 수 있습니다.)
|
| 작성후 잘 동작하는지 확인하고, 아래 코드와 비교합니다.

.. toggle::

    .. code-block:: c++
        :linenos: 

        #include "ssd1306.h" // 라이브러리 포함

        bool isPressedBtn = false; // 버튼이 눌러졌는지 확인하는 bool 변수
        bool isHeating = false; // 온도가 목표보다 높은지 확인하는 bool 변수
        int tempValueA0 = 0; // A0 신호 값 저장용

        void setup() 
        {
            // put your setup code here, to run once:
            pinMode(8,INPUT_PULLUP);   // A 버튼 
            pinMode(7,INPUT_PULLUP);   // B 버튼 
            pinMode(11,INPUT_PULLUP);  // C 버튼 
            pinMode(12,INPUT_PULLUP);  // D 버튼 

            pinMode(5,OUTPUT);         // 모터 활성화 핀
            pinMode(6,OUTPUT);         // 모터 방향 핀
            pinMode(10,OUTPUT);        // 모터 속도 핀

            pinMode(9,OUTPUT);         // 열선

            digitalWrite(5, HIGH);     // 모터 활성화

            ssd1306_128x32_i2c_init(); // 32로 변경
            ssd1306_fillScreen(0x00);  // 화면 초기화
            ssd1306_setFixedFont(ssd1306xled_font6x8); // 폰트 설정
            ssd1306_flipHorizontal(1); // x 화면 대칭 회전
            ssd1306_flipVertical(1);   // y 화면 대칭 회전

            // "cremaker" 문자표시
            ssd1306_printFixedN (15, 0, "cremaker", STYLE_NORMAL, FONT_SIZE_2X); 
        }

        void loop() 
        {
            // put your main code here, to run repeatedly:
            if(!isPressedBtn) // isPressedBtn이 false면 아래 코드 실행
            {                
                digitalWrite(9, LOW); // 예열 종료
                delay(5);

                if(digitalRead(11)==LOW)
                {
                    isPressedBtn = true;

                    ssd1306_fillScreen(0x00);  // 화면 초기화
                    // 예열 중일 경우 Heating 표시
                    ssd1306_printFixedN (0, 0, "Heating", STYLE_NORMAL, FONT_SIZE_2X);
                }
            }
            else // isPressedBtn이 true면 아래 코드 실행
            {
                tempValueA0 = analogRead(A0); // 아날로그 신호 값을 tempValueA0 저장

                digitalWrite(9, HIGH); // 예열 시작
                delay(1);
                tempValueA0 = analogRead(A0); // 아날로그 신호 값을 tempValueA0 저장
                if(!isHeating)
                {
                    digitalWrite(9, LOW); // 예열 종료
                }

                if(tempValueA0 < 981) // 온도 60도 유지
                {
                    digitalWrite(9, LOW); // 예열 종료
                    delay(5);

                    isHeating = false;
                }
                else
                {
                    digitalWrite(9, HIGH); // 예열 시작
                    delay(5); 

                    isHeating = true;
                }


                if(digitalRead(12)==LOW)
                {
                    isPressedBtn = false;

                    ssd1306_fillScreen(0x00);  // 화면 초기화
                    // 예열 중이 아닐 경우 OFF 표시
                    ssd1306_printFixedN (0, 0, "OFF", STYLE_NORMAL, FONT_SIZE_2X);  
                }
            }
        }

        