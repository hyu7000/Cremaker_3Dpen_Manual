Step.2 온도 측정 하기
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. raw:: html

    <style> 
    .orangecircle {color:#ff5300; font-size:20px} 
    .blackcircle {color:black; font-size:20px} 
    .bluecircle {color:#3172f4; font-size:20px}
    .skybluecircle {color:#00FFFF; font-size:20px}
    .yellowcircle {color:#fbbc05; font-size:20px}
    .subtitle {color:black; font-weight:bold; font-size:28px}
    .blackbold {color:black; font-weight:bold;}
    .redbold {color:red; font-weight:bold;}
    </style>

.. role:: orangecircle
.. role:: blackcircle
.. role:: bluecircle
.. role:: skybluecircle
.. role:: yellowcircle
.. role:: subtitle
.. role:: blackbold
.. role:: redbold


| 이제 실제로 신호 값이 1006 근처라면, 온도를 60도로 표기해보는 과정을 진행하려 합니다.
| 각각의 온도를 실시간으로 측정해 볼 수 있지만 과정이 매우 복잡해지기 때문에 하나의 온도 값을 예를 들어 진행하겠습니다.
| 저희가 해볼 방법으로는 온도표에서 60도일때 신호값이 1006 임으로 신호값이 1005~1007사이에 있으면 60도로 인식하게 끔 해보겠습니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_1.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 정지하기 버튼을 누르고, :blackbold:`신호 값 를 온도센서 신호 값 (으)로 정하기` 블록을 분리시켜 줍니다.
| :orangecircle:`●` 흐름 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_2.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`계속 반복하기` 블록을 이동시켜줍니다.
| :blackcircle:`●` 온도측정은 계속되어야 함으로 계속 반복하는 블록을 사용되어야 좋습니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_3.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`신호 값 를 온도센서 신호 값 (으)로 정하기` 블록을 :blackbold:`계속 반복하기` 블록 안으로 이동시켜줍니다.
| :blackcircle:`●` 지금까지의 블록은 신호 값을 한번이 아니라 계속 측정하게 되어 있습니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_4.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 자료 블록으로 이동합니다.
| :yellowcircle:`●` :blackbold:`변수 만들기` 버튼을 클릭합니다.
|
|


.. image:: ../../images/Lv1/Chapter_6/Step2_4_2.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 변수 이름을 '온도 값'으로 입력하고, 확인 버튼을 누릅니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_4_3.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 블록을 다시 눌러 블록 리스트로 이동합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_4_4.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`변수 온도 값 보이기` 블록을 :blackbold:`변수 신호 값 보이기` 아래로 이동시켜줍니다.
| :yellowcircle:`●` :blackbold:`온도 값 를 10 (으)로 정하기` 블록을 :blackbold:`신호 값 를 온도센서 신호 값 (으)로 정하기` 블록 아래로 이동시켜줍니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_4_5.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`10 온도 계산` 블록을 :blackbold:`온도 값을 10 (으)로 정하기` 블록의 10 부분에 이동시켜줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_4_6.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`온도센서 신호 값` 블록을 :blackbold:`10 온도 계산` 블록의 10부분에 이동시켜줍니다.
|
| 

.. image:: ../../images/Lv1/Chapter_6/Step2_4_7.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`시작하기` 버튼을 누르면, 신호값이 나타나고, 계산된 온도값을 확인할 수 있습니다.
| :blackcircle:`●` :blackbold:`신호 값 를 온도센서 신호 값 (으)로 정하기` 블록은 신호 값 변수에 해당 값을 저장하게 합니다.
| :blackcircle:`●` 이 저장된 값을 왼편에 표시된 신호 값에 나타납니다.
|
|
