모터 작동
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

| 이제 드디어 마지막 단계입니다.
|
| 모터를 작동시키려면, 먼저 예열이 되어 있어야 합니다. 또한 설정온도(60도)에 도달했는지도 확인해야 합니다.
| :blackbold:`예열 상태와 온도를 확인하고, 조건에 따라 모터를 작동되도록` 구현해보는 것이 목표입니다.
|

| 다음과 같은 기능을 수행하는 코드를 작성해봅니다.
|
| 1. 예열 상태가 OFF 일 경우에는 A,B 버튼을 눌러도 모터 작동하지 않음
| 2. 예열 상태에서 온도가 60도 근처일 경우 A,B 버튼을 누르면 작동하도록 동작
| ※ 60도 근처일 때 신호 값은 :blackbold:`979< 신호값 <983` 사이로 설정
| 3. bool 변수를 사용하여 온도가 60도 근처일 경우를 판단하도록 작성
| 4. 온도가 60도 근처에 도달 할 경우, 디스플레이에 OK 표시
| 5. 예열을 하지 않거나, 온도가 60도 근처가 아닐 경우 디스플레이에 OFF 표시
| 6. A,B 버튼에 따라 모터는 서로 다른 방향으로 회전하도록 동작
| 7. 모터의 회전속도는 시계, 반시계 모두 150으로 설정
|
| 작성후 잘 동작하는지 확인하고, 아래 코드와 비교합니다.

.. toggle::

    .. code-block:: c++
        :emphasize-lines: 4, 63, 64, 65, 66, 67, 68, 69, 70, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89
        :linenos: 

        #include "ssd1306.h" // 라이브러리 포함

        bool isPressedBtn = false; // 버튼이 눌러졌는지 확인하는 bool 변수
        bool is60Deg = false; // 온도 도달 상태 확인용
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
                    delay(5); // 약간의 대기시간 추가

                    isHeating = true;
                }

                if(tempValueA0>979 && tempValueA0<983) // 온도가 60도에 도달했는지 확인
                {                   
                    if(is60Deg == false)
                    {
                        ssd1306_fillScreen(0x00);  // 화면 초기화
                        // 예열 중일 경우 Heating 표시
                        ssd1306_printFixedN (0, 0, "OK", STYLE_NORMAL, FONT_SIZE_2X);

                        is60Deg = true;
                    }                    
                }
                else
                {
                    if(is60Deg == true)
                    {
                        is60Deg = false;

                        ssd1306_fillScreen(0x00);  // 화면 초기화
                        // 60도 근처가 아닐시 OFF 표시
                        ssd1306_printFixedN (0, 0, "OFF", STYLE_NORMAL, FONT_SIZE_2X);  
                    }
                }

                if(is60Deg) // 온도가 도달된 상태라면, 모터가 움직일 수 있음
                {
                    if(digitalRead(8)==LOW) // A 버튼 눌렸을 경우
                    {
                        digitalWrite(6,LOW);
                        analogWrite(10,150); //모터 속도 150 설정
                    }
                    else if(digitalRead(7)==LOW) // B 버튼 눌렸을 경우
                    {
                        digitalWrite(6,HIGH);
                        analogWrite(10,150); //모터 속도 150 설정
                    }
                    else
                    {
                        digitalWrite(6,LOW);
                        analogWrite(10,0); //모터 속도 0 설정
                    }
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

|