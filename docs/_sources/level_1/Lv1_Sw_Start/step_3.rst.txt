Step.3 LED 껏다켜기_1
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

| 먼저 엔트리에 대해 살짝 알아볼겸 간단하게 LED를 껏다 켜는 과정을 진행해봅니다.
| 이는 엔트리와 SW 코딩에 관한 이해를 높이는데 도움이 됩니다.

|
| 이번 SW 코딩의 목표 : 
| :blackbold:`LED 가 껐다가 켜지는 것이 계속 반복되는 동작을 만들어 보기`
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_1.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 첫 번째로 화면에 있는 :blackbold:`시작하기 버튼을 클릭했을 때` 블록과 아래 블록들을 드래그하여 왼편이나 오른쪽 아래 휴지통으로 이동시켜, 지워줍니다. 
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 시작 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_3.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`시작하기 버튼을 클릭했을 때` 블록을 오른쪽으로 이동시켜 줍니다. 이 블록 아래쪽에는 화살표가 있습니다. 이 것의 의미는 :blackbold:`시작하기` 버튼을 누르면 아래 블록을 실행하라라는 뜻입니다.
| :blackcircle:`●` 이제 아래에 붙일 버튼을 찾아봅니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_4.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 흐름 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_5.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`10번 반복하기` 블록을 드래그 하여. :blackbold:`시작하기 버튼을 클릭했을 때` 버튼 아래에 놓아줍니다.
| :blackcircle:`●` 이제 시작버튼을 누르면 무언가 10번 반복을 합니다. 아직 ‘무언가’가 없기 때문에 넣어줘야 합니다.
| :blackcircle:`●` 숫자 10은 원하는 숫자로 변경할 수 있습니다. 반복횟수 10을 지우고 원하는 숫자를 입력하면 됩니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_6.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 하드웨어 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_7.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`디지털 0 번 핀 켜기` 블록 2개를 :blackbold:`10번 반복하기` 블록 안에 넣어줍니다.
| :blackcircle:`●` 블록은 하나씩 2번 이동시켜 주면 됩니다.
| :blackcircle:`●` :blackbold:`디지털 0 번 핀 켜기` 블록은 디지털 핀의 신호를 주겠다는 뜻입니다. 신호를 주게 되면, 약간의 전류가 흐를 수 있게 됩니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_8.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`디지털 0` 이라고 되어 있는 부분을 13으로 변경시켜 줍니다.
| :blackcircle:`●` 2개의 블록 모두 변경 시켜줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_9.png
   :width: 600
   :align: center

|
| :blackcircle:`●` 아두이노 보드에는 13개의 디지털 핀이 있으며, 디지털 13번핀은 LED에 연결되어 있습니다.
| :blackcircle:`●` 이 LED 전구를 껏다 켰다 작동시켜볼 계획입니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_10.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`켜기` 이라고 되어 있는 부분을 :blackbold:`끄기` 로 변경시켜 줍니다.
| :blackcircle:`●` 여기까지 블록을 완성시키면, :blackbold:`시작하기` 버튼을 누르면 13핀에 연결된 전구가 꺼졋다 켜졌다를 10회 반복하게 되게끔 만들었습니다.
| :blackcircle:`●` :blackbold:`시작하기` 버튼을 누르고 작동이 제대로 하는지 확인합니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_11.gif
   :width: 500
   :align: center

|
| :blackcircle:`●` 아마도 위와 같이 작동하지 않을 겁니다. 어디가 잘못된 것일까요?
| :blackcircle:`●` 영상 이미지와 여러분이 만든 블록간의 차이가 무엇인지 한번 살펴보세요.
| :blackcircle:`●` 충분히 생각해보셨다면, 다음 과정으로 이동합니다.
