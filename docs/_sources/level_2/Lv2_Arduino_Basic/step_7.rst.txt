함수
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

| 함수라고 하면, 처음보는 단어이신 분도 있고, 많이 보신 분들도 있을 겁니다.
| 함수를 이해하고, 잘 사용하게 되면, 코드가 간단해지고, 반복적인 일을 덜어줍니다.
| 아래 이미지를 보여드리고, 차근 차근 설명드리겠습니다.


.. _targetL2C6S7_1:


.. image:: ../../images/Lv2/Chapter_6/Step7_1.jpg
   :width: 500
   :align: center

|
| 그림처럼 함수는 어떤 값을 넣으면, 결과 값을 반환하는 기능을 합니다.
| 여기서 함수에 넣어주는 변수 a,b를 :blackbold:`매개변수` 라고 합니다.
| 아두이노에서 함수는 정의를 해주어야 사용할 수 있습니다.
|

| :subtitlesmall:`함수 정의`

.. image:: ../../images/Lv2/Chapter_6/Step7_2.jpg
   :width: 600
   :align: center

|
| 오른쪽을 보시면, 더하기라는 함수 이름이 있습니다. 뭔지 모르지만 a와 b를 더하고, 그 계산된 값을 반환하는 것 같습니다. 함수 이름처럼 a와 b를 더한 값을 반환하는 함수입니다.
| 이처럼 함수가 어떤 동작을 하는지 코드로 작성하는 것을 함수를 정의한다고 표현합니다.
|
| ※실제 코드에서는 :blackbold:`한글 사용이 불가능` 합니다. 한글로 표시한 것은 이해를 돕기 위함입니다.

.. _targetL2C6S7_2_2 to paragraph:


| :subtitlesmall:`함수의 자료형`
| 마찬가지로 함수도 변수와 마찬가지로 자료형이 있습니다. 
| 함수의 자료형은 반환(return)하는 결과값의 자료형과 동일해야 합니다.
| 오른쪽에 계산값이 int 형으로 정하였기 때문에, 함수의 자료형도 int가 되어야 합니다.
|
| 다만, 우리가 이전에 봤던 함수중에 void 자료형을 기억하실 겁니다. 
| 아래는 LED를 껏다 켜고 할 때 사용했던 코드입니다. 마찬가지로 함수이지만, :blackbold:`결과값 반환이 없기 때문에 자료형이 void` 로 되어 있습니다.
| void는 '아무것도 없는, 빈 공간'을 뜻 합니다.

.. code-block:: c++
   :linenos:

   void loop() {
      digitalWrite(LED_BUILTIN, HIGH);   
      delay(1000);                       
      digitalWrite(LED_BUILTIN, LOW);    
      delay(1000);                       
   }

|
| :subtitlesmall:`매개변수`
| 다시 돌아와서, 함수에는 매개변수가 있습니다. 이는 함수이름 옆 괄호에 있는 변수들입니다. 외부에서 전달되는 값들이 대입되어, 함수 내부에서 사용됩니다.
| 매개변수는 여러 개가 될 수 있으며, 없을 수 도 있습니다. 필수 요소가 아니기 때문에, 매개변수가 없는 함수도 정상적인 함수입니다.

|
| :subtitlesmall:`함수의 사용`
| 그렇다면, 정의된 함수는 어떻게 사용하는지? 에 대한 궁금증이 생기실 겁니다.
| 위의 :blackbold:`더하기` 함수가 정의되어 있으면, 아래와 같이 사용됩니다.
|

.. image:: ../../images/Lv2/Chapter_6/Step7_3.jpg
   :width: 700
   :align: center

|
| int 형 변수 c,d,e가 각각 선언과 초기화되어 있는 상태입니다. e변수에 :blackbold:`더하기(c,d)` 함수가 적혀있습니다. 
| 이렇게 함수 이름과 변수 c,d가 매개변수로 되도록 작성되면, 함수의 정의로 이동되어 :blackbold:`더하기(c,d)가 더하기(10,5)` 가 되어 함수가 실행됩니다. 
| 매개변수가 10,5로 되어 있으니, 함수 내부에 있는 a,b 도 모두 변경됩니다.
| 결과값으로 10과 5가 더해진 값이 반환됩니다. 이렇게 함수이름과 매개변수를 입력하는 것을 :blackbold:`함수를 호출` 한다고 합니다.

| ※실제 코드에서는 :blackbold:`한글 사용이 불가능` 합니다. 한글로 표시한 것은 이해를 돕기 위함입니다.
|
| 아래 코드에서는 a에 어떤 값이 저장될지 생각해보세요.

.. code-block:: c++
   :linenos:

    float a = 0; //float은 정수와 소수를 포함하는 실수형입니다.
    int b = 4;

    float area(int r)
    {
      float pi = 3.14;

      return r*r*pi;
    }

    a = area(b);

.. toggle::

   | a 변수에는 50.24 이 저장되었습니다.
   | area 뜻은 면적으로 반지름이 주어졋을 때 원 넓이를 구하는 함수입니다.


|
| :subtitlesmall:`지역 변수, 전역 변수`
| 함수를 배웠으니 변수에 대해서 하나 더 알고 가야 할 것이 있습니다. 바로 지역변수와 전역변수입니다.
| :blackbold:`지역변수는 함수내에서만 사용가능` 하며, :blackbold:`전역변수는 코드 전체에서 사용` 할 수 있습니다.
| 위에 작성된 코드를 살짝 변경하였습니다.

.. code-block:: c++
   :linenos:
   :emphasize-lines: 1, 2, 3, 7

    float a = 0; //float은 정수와 소수를 포함하는 실수형입니다.
    float b = 0;
    int c = 4;

    float area()
    {
      float pi = 3.14;

      return c*c*3.14; //c는 전역변수임으로 함수내에서 사용 가능
    }

    a = area();

    b = pi; //pi는 지역변수로 함수 밖에서는 에러를 발생

| a,b는 함수 밖 코드에서 작성되었기 때문에 전역변수입니다. 
| pi는 함수 안에서 작성되었기 때문에 지역변수입니다.
| 반면 c는 전역변수임으로 area 함수내에서도 사용되는 것을 볼 수 있습니다.
|
| 아래에서는 어디에서 에러가 발생할지 생각해보세요.

.. code-block:: c++
   :linenos:

   float a = 0;
   float b = 65;
   float c = 72;
   float n = 2;

   float avg(float math, float english)
   {
      float total = math + english;

      return total/n;
   }

   a = math + english;

.. toggle::

   | 에러가 발생하는 라인은 13번줄 입니다.

|