.. _targetL2C10S1_0:

디스플레이 화면 변경
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

| 디스플레이에 표시되는 문자들을 변경해야 될 경우가 있습니다. :blackbold:`디스플레이를 다룰 때 발생할 수 있는 문제를 피할수 있도록` 코드를 구현해보도록 하겠습니다.

| 먼저 이전에 작성했던 코드들에서 C 버튼을 누르면 'ON' 이 디스플레이에 표시되고, D 버튼을 누르면 'OFF' 가 디스플레이에 표시되도록 해보겠습니다.

.. code-block:: c++
    :linenos: 

    #include "ssd1306.h" // 라이브러리 포함

    void setup() 
    {
        // put your setup code here, to run once:
        pinMode(11,INPUT_PULLUP);  // C 버튼 
        pinMode(12,INPUT_PULLUP);  // D 버튼 

        ssd1306_128x32_i2c_init(); // 32로 변경
        ssd1306_fillScreen(0x00);  // 화면 초기화
        ssd1306_setFixedFont(ssd1306xled_font6x8); // 폰트 설정
        ssd1306_flipHorizontal(1); // x 화면 대칭 회전
        ssd1306_flipVertical(1);   // y 화면 대칭 회전
    }

    void loop() 
    {
        // put your main code here, to run repeatedly:
        if(digitalRead(11)==LOW)
        {
            // 화면에 ON 표시
            ssd1306_printFixedN (0, 0, "ON", STYLE_NORMAL, FONT_SIZE_2X);                 
        }
        else if(digitalRead(12)==LOW) 
        {
            // 화면에 OFF 표시
            ssd1306_printFixedN (0, 0, "OFF", STYLE_NORMAL, FONT_SIZE_2X);
        }
    }

| 위 처럼 C 버튼과 D 버튼이 눌려질 때마다 디스플레이 화면이 바뀌도록 하였습니다.
| 실제로 적용하면, 아래와 같은 문제가 발생합니다.
| 

.. image:: ../../images/Lv3/Chapter_10/Remaining_Text.gif
   :width: 600
   :align: center

|
| 이런 문제를 해결하려면, 글자를 변경하고자 하는 순간에 화면을 초기화 해주어야 합니다. (10줄 함수 참고)
| 적용하면 다음과 같습니다.

.. code-block:: c++
    :linenos: 

    #include "ssd1306.h" // 라이브러리 포함

    void setup() 

        // put your setup code here, to run once:
        pinMode(11,INPUT_PULLUP);  // C 버튼 
        pinMode(12,INPUT_PULLUP);  // D 버튼 

        ssd1306_128x32_i2c_init(); // 32로 변경
        ssd1306_fillScreen(0x00);  // 화면 초기화
        ssd1306_setFixedFont(ssd1306xled_font6x8); // 폰트 설정
        ssd1306_flipHorizontal(1); // x 화면 대칭 회전
        ssd1306_flipVertical(1);   // y 화면 대칭 회전
    }

    void loop() 
    {
        // put your main code here, to run repeatedly:
        if(digitalRead(11)==LOW)
        {
            ssd1306_fillScreen(0x00);  // 화면 초기화
            // 화면에 ON 표시
            ssd1306_printFixedN (0, 0, "ON", STYLE_NORMAL, FONT_SIZE_2X);                 
        }
        else if(digitalRead(12)==LOW) 
        {
            ssd1306_fillScreen(0x00);  // 화면 초기화
            // 화면에 OFF 표시
            ssd1306_printFixedN (0, 0, "OFF", STYLE_NORMAL, FONT_SIZE_2X);
        }
    }

| 하지만 이 경우에도 약~간의 문제가 있습니다. 버튼을 길게 누르면 화면이 이상해지는 것을 볼 수있습니다.

.. image:: ../../images/Lv3/Chapter_10/Blinking.gif
   :width: 600
   :align: center

|
| 버튼을 1초 누르고 있는 동안에도 여러번의 화면 초기화와 디스플레이에 문자 표시가 반복되면서, 흐릿하게 보이는 증상입니다.
| 이 증상을 해결하는 방법이 여러가지가 있지만, 레벨2에서는 간단한 방법으로 해결해 보겠습니다.
|
| bool 값을 추가하고 이 값을 이용하는 방법입니다. 
| :blackbold:`처음 버튼을 누를때 이 bool 변수 값이 바뀌고, 손에서 떼기 전까지는 값을 유지` 하도록 코드를 작성해보세요. 약간의 난이도가 있을 수 있습니다.
|
| 작성하고 업로드하여 정상적으로 작동하는지 확인하고, 아래 코드와 비교해봅니다.

.. toggle::

    .. code-block:: c++
        :linenos: 

        #include "ssd1306.h" // 라이브러리 포함

        bool isPushed = false; // 버튼 상태 확인용

        void setup() 
        {
            // put your setup code here, to run once:
            pinMode(11,INPUT_PULLUP);  // C 버튼 
            pinMode(12,INPUT_PULLUP);  // D 버튼 

            ssd1306_128x32_i2c_init(); // 32로 변경
            ssd1306_fillScreen(0x00);  // 화면 초기화
            ssd1306_setFixedFont(ssd1306xled_font6x8); // 폰트 설정
            ssd1306_flipHorizontal(1); // x 화면 대칭 회전
            ssd1306_flipVertical(1);   // y 화면 대칭 회전
        }

        void loop() 
        {
            // put your main code here, to run repeatedly:
            if(digitalRead(11)==LOW)
            {
                if(!isPushed)
                {
                    ssd1306_fillScreen(0x00);  // 화면 초기화
                    // 화면에 ON 표시
                    ssd1306_printFixedN (0, 0, "ON", STYLE_NORMAL, FONT_SIZE_2X);

                    isPushed = true;                 
                }
            }
            else if(digitalRead(12)==LOW) 
            {
                if(!isPushed)
                {
                    ssd1306_fillScreen(0x00);  // 화면 초기화
                    // 화면에 OFF 표시
                    ssd1306_printFixedN (0, 0, "OFF", STYLE_NORMAL, FONT_SIZE_2X);

                    isPushed = true;
                }
            }
            else
            {
                isPushed = false;
            }
        }