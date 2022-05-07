디스플레이 문자 표시_2
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
    
| 정해진 문자를 디스플레이에 표시를 하는 것은 간단합니다. 3D 펜이 온도가 계속해서 변경되는 것을 표시를 하려면 조금 문제가 생깁니다.
|
| 아래와 같은 예제를 보겠습니다.

.. code-block:: c++
    :linenos:

    #include "ssd1306.h" // 라이브러리 포함

    String str = "cremaker"; // 문자열 선언

    void setup()
    {
        /* Replace the line below with ssd1306_128x32_i2c_init() if you need to use 128x32 display */
        ssd1306_128x64_i2c_init();
        ssd1306_fillScreen(0x00);
        ssd1306_setFixedFont(ssd1306xled_font6x8);
        ssd1306_printFixedN (0, 32, str, STYLE_BOLD, FONT_SIZE_2X); //문자열을 매개변수로 전달
    }


    void loop()
    {
    }

| 위와 같은 코드를 컴파일을 하면 다음과 같은 에러가 나타납니다.
|
| :redbold:`cannot convert 'String' to 'const char*' for argument '3'`
|
| 이 에러는 3번째 매개변수에서 String에서 const char*로 변환이 안된다는 뜻입니다. * 기호는 포인터개념이 있어야 함으로 여기에서 설명드리진 않고
| 겉으로는 같은 문자열을 취급하지만 자료형이 달라 사용을 못합니다.
| String을 사용하려면, String을 char 배열 형태로 바꿔주어야 합니다. 물론 char 를 사용하는 것이 메모리도 적게먹고 번거롭게 하지 안하도 되지만, 메모리 주소등과 같은 복잡한 개념을 이해하고 있어야 하기 때문에 String을 사용합니다.
| 

.. image:: ../../images/Lv2/Chapter_10/Step2_2.jpg
   :width: 600
   :align: center

| 
| toCharArray 함수를 사용하여 String을 char[] 로 변경해줍니다. 이 함수를 적용하면 다음과 같습니다.

.. code-block:: c++
    :linenos:

    char ch[20]; // 문자 배열의 선언
    String str = "cremaker"; // 문자열 선언
    str.toCharArray(ch, str.length()); // 문자열을 문자 배열에 저장

| 
| 위 코드는 사용예시입니다. str.length()는 str 변수 문자열의 길이를 반환합니다. 
| 이제 첫번째 예제에 toCharArray 함수를 적용해보겠습니다.
|

.. code-block:: c++    
    :emphasize-lines: 8
    :linenos:

    #include "ssd1306.h" // 라이브러리 포함

    char ch[20];
    String str = "cremaker"; // 문자열 선언

    void setup()
    {
        str = str + "\n";
        str.toCharArray(ch, str.length());

        /* Replace the line below with ssd1306_128x32_i2c_init() if you need to use 128x32 display */
        ssd1306_128x64_i2c_init();
        ssd1306_fillScreen(0x00);
        ssd1306_setFixedFont(ssd1306xled_font6x8);
        ssd1306_printFixedN (0, 32, ch, STYLE_BOLD, FONT_SIZE_2X); //문자열을 매개변수로 전달
    }


    void loop()
    {
    }

| 8줄의 코드는 삽입된 이유는, 해당 코드 없이 업로드를 하면 마지막 문자가 짤려서 표시됩니다. 문자배열 끝에 \n가 포함되어야 마지막 문자가 짤리지 않고 전체가 디스플레이에 표시가 됩니다.