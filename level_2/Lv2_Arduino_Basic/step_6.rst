배열
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

| 배열은 여러개의 변수들을 나열한 것입니다.
| 예를들어 학교의 반에 학생들의 수학 점수들을 1번 학생부터 끝번 학생까지 나열한 것이 배열이라 보시면 됩니다.
| 먼저 배열도 변수처럼 선언을 해야합니다.
| 

| :subtitlesmall:`배열의 선언`
| 배열의 선언을 하는 방법은 변수를 선언하는 것과 유사합니다.
|

.. image:: ../../images/Lv2/Chapter_6/Step6_1.jpg
   :width: 600
   :align: center

|
| 배열은 변수의 선언과 비슷하지만 배열의 이름 옆에 길이를 작성해줍니다. 각각의 배열은 10개의 변수를 가진 배열이 됩니다.
| 또한 배열의 이름도 :ref:`변수의 이름 규칙 <targetL2C6S2_1>` 에 맞게 작성해야합니다.
|

| :subtitlesmall:`배열의 초기화`
| 배열의 초기화도 마찬가지로 변수의 초기화랑 유사합니다.
|

.. image:: ../../images/Lv2/Chapter_6/Step6_2.jpg
   :width: 600
   :align: center

|
| 배열의 초기화도 2가지 방식이 있습니다. 선언과 동시에 초기화, 혹은 선언 이후 초기화를 할 수 있습니다.
| 선언과 동시에 초기화를 할 경우에는 여러 항목을 동시에 할 수 있지만, 선언 이후에 초기화를 하려면, 각각 따로 따로 초기화를 진행해야합니다.
| 
| 값을 초기화, 저장하거나 값을 확인하는 것을 접근한다 합니다.
| 배열의 첫 항목은 '배열이름[0]' 으로 접근합니다. int level[3]은 3개의 int형 변수의 배열입니다.
| level[0]에 접근을 하게 되면, level 배열의 첫번째 항목에 접근이 됩니다.
| level[1]에 접근을 하게 되면, level 배열의 두번째 항목에 접근이 됩니다. 
|
| ※실제 코드에서는 :blackbold:`한글 사용이 불가능` 합니다. 한글로 표시한 것은 이해를 돕기 위함입니다.
|
| 아래 코드에서는 a에 어떤 값이 저장될지 생각해보세요.
|

.. code-block:: c++

    int a;
    int b[5] = { 10, 9, 8, 7, 6 };
    a = b[3];

| 정답

.. toggle::

    | a 변수에는 7 이 저장되었습니다.

|
| :subtitlesmall:`2차원 배열`
| 배열은 응용이 될 수 있습니다. 예를 들어 :blackbold:`3명의 학생을 순서대로 영어, 수학 점수를 함께 배열로 나타내고 싶다` 면 배열로 어떻게 나타내야 할까요?
|

.. image:: ../../images/Lv2/Chapter_6/Step6_3.jpg
   :width: 700
   :align: center

|
| 2차원 배열을 이용하는 방법이 있습니다. 물론 2차 말고도 3,4~ 이어질 수 있습니다만, 아주 큰 차원의 배열을 다룰 일이 드뭅니다.
| 2차원 배열에 접근하는 방법도 1차원 배열과 동일합니다.

.. image:: ../../images/Lv2/Chapter_6/Step6_4.jpg
   :width: 600
   :align: center

|
| int 형 변수 a에 score 변수에 있는 2번쨰 학생의 수학 점수(90점)를 저장하고 싶다면, 두번째 배열의, 두번째 항목에 접근해야 합니다.
| 접근하려면 첫번째 항목이 숫자 0 으로 시작되니 score[1][1]와 같이 접근해야 90 이라는 숫자에 접근할 수 있습니다.
|
| 아래 코드에서는 a에 어떤 값이 저장될지 생각해보세요.
|

.. code-block:: c++

    boolean a = true;
    int score[3][2] = { {65, 52}, {72, 80}, {45, 90} };
    a = score[1][1] < score[2][1];

| 정답

.. toggle::

    | a 변수에는 false 이 저장되었습니다.

