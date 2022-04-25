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


| 이제 실제로 신호 값이 981 근처라면, 온도를 60도로 표기해보는 과정을 진행하려 합니다.
| 각각의 온도를 실시간으로 측정해 볼 수 있지만 과정이 매우 복잡해지기 때문에 하나의 온도 값을 예를 들어 진행하겠습니다.
| 저희가 해볼 방법으로는 온도표에서 60도일때 신호값이 981 임으로 신호값이 978~984사이에 있으면 60도로 인식하게 끔 해보겠습니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_1.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 정지하기 버튼을 누르고, :blackbold:`신호 값 를 아날로그 A0 번 센서값 (으)로 정하기` 블록을 분리시켜 줍니다.
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
| :yellowcircle:`●` :blackbold:`신호 값를 아날로그 A0 번 센서값 (으)로 정하기` 블록을 :blackbold:`계속 반복하기` 블록 안으로 이동시켜줍니다.
| :blackcircle:`●` 지금까지의 블록은 신호 값을 한번이 아니라 계속 측정하게 되어 있습니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_4.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`만약 참 (이)라면 ~ 아니면 ~` 블록을 이동시켜줍니다.
| :blackcircle:`●` 이 블록은 신호 값이 978~984 사이일때 온도값을 60으로 저장하기 위해 조건을 붙이는 블록입니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_5.jpg
   :width: 600
   :align: center

|
| 여기에서 참과 거짓에 대해서 알아보고 넘어가겠습니다. 이전에 보았던 달리기 1등 학생 변수입니다.
| 이 학생이 홍길동인지 검사를 하고 결과에 따라 참, 거짓이 결정됩니다. 
| 맞는 값이나 문장이 나오면 참, 값이 다르거나 틀린 문장이 나오면 거짓이 됩니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_6.jpg
   :width: 600
   :align: center

|
| :blackbold:`만약 참 (이)라면 ~ 아니면 ~` 의 블록은 다음과 같이 그려질 수 있습니다.
| 참일 경우와 거짓일 경우의 작업이 각각 다르게 할 수 있습니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_7.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`참 그리고 참` 블록을 :blackbold:`만일 참(이)라면 ~ 아니면 ~` 블록중에 :blackbold:`참` 부분으로 이동시켜 줍니다.
| :blackcircle:`●` :blackbold:`참 그리고 참`` 블록은 왼쪽과 오른쪽이 모두 참이어야 :blackbold:`참` 으로 인식합니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_8.jpg
   :width: 700
   :align: center

|
| :blackbold:`참 그리고 참` 과 같은 형태는 왼쪽 조건과 오른쪽 조건이 둘다 만족해야 합니다.
| 그림처럼 홍길동은 달리기와 턱걸이 모두 1등해야 1점을 얻을 수 있습니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_9.jpg
   :width: 700
   :align: center

|
| :blackbold:`참 또는 참` 과 같은 형태는 왼쪽 조건과 오른쪽 조건중 하나만 만족해도 참 입니다.
| 그림처럼 홍길동은 달리기, 턱걸이 중 하나만 1등해도 1점을 얻을 수 있습니다.
| 
|

.. image:: ../../images/Lv1/Chapter_6/Step2_10.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`10≥10` 블록과 :blackbold:`10≤10` 블록을 각각 :blackbold:`참` 부분으로 이동시켜 줍니다.
| :blackcircle:`●` 이 부분에는 ‘신호 값이 978~984 사이일때 참이다’ 라고 인식하려 합니다.
| :blackcircle:`●` ‘978 < 신호 값’은 현재 신호값이 978 보다 큰가? 와
| :blackcircle:`●` ‘984 > 신호 값’은 현재 신호값이 984 보다 작은가? 를 동시에 확인하게 합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_11.png
   :width: 800
   :align: center

|
| :blackcircle:`●` :blackbold:`아날로그 A0 번 센서값` 을 그림과 같이 각각 넣어주고, 숫자를 978, 984 변경시켜 줘야합니다.
| :orangecircle:`●` 하드웨어 블록을 클릭합니다.
| :yellowcircle:`●` :blackbold:`아날로그 A0 번 센서값` 블록을 :blackbold:`10≥10` 블록과 :blackbold:`10≤10` 블록의 오른쪽 칸에 이동시켜줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_12.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 신호 값이 978~984 사이라면 온도 값을 60이라는 것을 알려줘야 하기 때문에 변수를 하나 더 만들어야 합니다.
| :orangecircle:`●` 자료 블록을 클릭합니다.
| :yellowcircle:`●` :blackbold:`변수 만들기` 를 눌러줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_13.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 변수 이름을 :blackbold:`온도 값` 으로 입력합니다.
| :yellowcircle:`●` :blackbold:`확인` 버튼을 누릅니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_14.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 다음으로 나오는 화면은, 변수 속성등이 나옵니다. 이 부분은 설정을 변경하지 않고, 다시 블록으로 이동합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step2_15.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`온도 값 를 10 (으)로 정하기` 블록을 :blackbold:`만일 ~(이)` 아래로 이동시켜줍니다.
| :orangecircle:`●` :blackbold:`온도 값 를 10 (으)로 정하기` 블록의 숫자 10을 60으로 변경해줍니다.
| :blackcircle:`●` 신호 값이 978~984 사이라면 온도 값을 60으로 표시 하도록 블록을 구성하였습니다.
|
| 이제 가열 하는 블록을 만들어 실제로 온도를 높여 봅니다.
|
|