Step.2 모터 작동 시키기
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

.. image:: ../../images/Lv1/Chapter_5/Step1_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 시작 블록을 클릭합니다.
| :yellowcircle:`●` :blackbold:`q 키를 눌렀을 때` 블록을 드래그하여 이동시켜 줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step1_3.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 하드웨어 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step1_4.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 먼저 모터를 On, Off 하는 블록부터 만들어 보겠습니다. :blackbold:`디지털 0번 핀 켜기` 블록을 이동시킵니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step1_5.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`디지털 0번 핀 켜기` 를 숫자 0을 5로 변경시켜줍니다.
| :blackcircle:`●` 디지털 5번 핀은 모터의 On,Off를 담당하는 부분에 연결되어 있기 때문입니다. 이 부분은 제작하는 사람이 결정하는 것이라 숫자에는 크게 신경안쓰셔도 됩니다.
| :blackcircle:`●` 디지털 5번 핀이 켜지면 모터가 작동준비를 하게 되고, 끄기를 선택하면, 방향, 속도가 정해져도 작동하지 않습니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step1_6.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 이제 두번째 부분인 회전 방향을 담당하는 블록도 만들어 주기 위해 :blackbold:`디지털 0번 핀 켜기` 블록을 하나 더 이동시켜줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step1_7.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`디지털 0번 핀 켜기` 를 숫자 0을 6으로 변경시켜줍니다. 디지털 6번 핀은 모터의 방향을 결정합니다. 키고 끄는 것에 따라 반시계, 시계 방향으로 회전합니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step1_8.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 마지막으로 속도를 결정하는 블록을 만들기 위해 :blackbold:`디지털 3 번 핀을 255 (으)로 정하기` 블록을 이동시켜줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step1_9.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`디지털 3 번 핀을 255 (으)로 정하기` 에서 숫자 3을 10으로 변경해줍니다.
| :blackcircle:`●` 이어서 뒷편에 있는 255는 속도를 뜻합니다. 0~255까지 사용할 수 있으며, 255는 최대 속도, 0은 최소 속도가 되겠습니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step1_10.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`시작하기` 버튼을 누른 뒤에 Q 버튼을 눌러 모터의 움직임을 확인해 봅니다.
|
|

|
| :blackcircle:`●` 모터가 움직이나요? 그렇다면 다양한 방법으로 모터를 움직여 봅시다.
|
| :blackcircle:`1.` 모터가 정지하는 블록
| :blackcircle:`2.` 모터가 반시계 방향으로 회전하는 블록
| :blackcircle:`3.` 모터가 시계 방향으로 회전하는 블록-속도 느리게 해보기
| 