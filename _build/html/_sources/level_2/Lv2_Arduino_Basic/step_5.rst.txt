반복문
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

| 어떤 조건이 계속 참이면, 특정 코드를 계속해서 반복하게 하는 것이 반복문입니다.
| 구조는 아래 그림과 같습니다.
| 레벨2에서는 모든 반복문을 살펴보기보다 주로 많이 사용되는 것을 위주로 설명합니다.

.. image:: ../../images/Lv2/Chapter_6/Step5_1.jpg
   :width: 600
   :align: center

|
| 반복문이 시작되면, 초기값을 설정합니다. 이어서 조건을 확인합니다. 조건이 '참'이면, 코드를 실행하고, 횟수를 증가 시키거나 감소시킵니다. 이어서 다시 조건을 확인하고, 다시 코드를 실행하는 과정을 반복합니다.
| 이후 조건이 '거짓'이 되면, 반복문을 종료합니다.
| 코드로 변경하면 다음과 같습니다.
|
| ※실제 코드에서는 :blackbold:`한글 사용이 불가능` 합니다. 한글로 표시한 것은 이해를 돕기 위함입니다.
|

.. image:: ../../images/Lv2/Chapter_6/Step5_2.jpg
   :width: 600
   :align: center

|
| 반복문은 for문이라고도 표시되며, 괄호에는 (초기값 설정;조건;값 증감)으로 구성됩니다. 보통 조건에는 초기값과 관련되어 있습니다. 그림처럼 초기값인 횟수가 5보다 작은 경우에만 반복하게 되어 있습니다. 그리고 코드를 실행하면, 횟수가 1증가 함으로,
| 이 반복문의 경우는 코드를 총 5회까지 반복 실행합니다.
|
| 아래 코드에서는 최종적으로 a에 어떤 값이 저장될지 생각해보세요.
| ※참고로 i++ 는 i=i+1 과 같은 기능을 수행합니다.
|

.. code-block:: c++

   int a = 0;
   for(int i = 0; i<4 ;i++)
   {
    a = a + i;
   }

| 정답

.. toggle::

    | a 변수에는 6 이 저장되었습니다.
