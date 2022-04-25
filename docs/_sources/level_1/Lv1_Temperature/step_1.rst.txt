Step.1 온도 측정 원리
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

| 3D 펜에는 온도를 읽는 온도센서가 있습니다. 센서는 저항으로 이루어져 있으며, 온도가 바뀌면 저항 값이 변합니다. 이 바뀌는 특징으로 온도를 파악합니다.

| 먼저 온도 표입니다.

+-----------+--------------+
| 실제 온도 | 아날로그 값  |
+===========+==============+
| 10        | 1008         |
+-----------+--------------+
| 20        | 994          |
+-----------+--------------+
| 30        | 990          |
+-----------+--------------+
| 40        | 985          |
+-----------+--------------+
| 50        | 983          |
+-----------+--------------+
| 60        | 981          |
+-----------+--------------+
| 70        | 978          |
+-----------+--------------+
| 80        | 975          | 
+-----------+--------------+
| 90        | 965          |
+-----------+--------------+
| 100       | 959          |
+-----------+--------------+
| 110       | 952          |
+-----------+--------------+
| 120       | 948          |
+-----------+--------------+
| 130       | 941          |
+-----------+--------------+
| 140       | 932          |
+-----------+--------------+
| 150       | 920          |
+-----------+--------------+
| 160       | 908          |
+-----------+--------------+
| 170       | 890          |
+-----------+--------------+
| 180       | 875          |
+-----------+--------------+
| 190       | 845          |
+-----------+--------------+
| 200       | 820          |
+-----------+--------------+
| 210       | 790          |
+-----------+--------------+
| 220       | 765          |
+-----------+--------------+

| 복잡해 보이나요? 
| 위 표를 기준으로 아날로그 값이 981로 나타난다면 현재 온도가 60도 라고 측정하면 됩니다.
| 그렇다면 이제 아날로그 값을 측정해봅니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_1.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 시작 블록을 클릭합니다.
| :yellowcircle:`●` :blackbold:`시작하기 버튼을 클릭하였을 때` 를 이동시킵니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 자료 블록을 클릭합니다. 여기에서 변수를 만들어야 합니다. 
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_3.jpg
   :width: 600
   :align: center

| 
| ※ 잠시 변수에 대해 설명을 하자면, 변수 라는 단어의 뜻은 '변하는 수' 입니다. 
| SW 코딩에서는 이 변수에 숫자 뿐만 아니라 값을 저장할 수 있습니다. 
| 예를 들어, 사진처럼 :blackbold:`달리기 1등 학생` 이라는 이름으로 변수를 만들었다고 가정합니다. 
| 이 변수에는 달리기 경주마다 1등하는 학생의 이름이 저장되어야 될 겁니다. 값을 저장하고, 
| 매번 달리기 경주마다 1등이 변경되었는지 확인합니다. 변경되면 :blackbold:`달리기 1등 학생` 의 변수에 새로운 학생의 이름을 저장합니다.
| 이처럼 변수에는 값이 저장될 수 있습니다.

.. image:: ../../images/Lv1/Chapter_6/Step1_4.jpg
   :width: 600
   :align: center

|
| 또 다른 기능으로는 변수를 확인하는 과정입니다.
| 달리기 1등 학생이 누구인지? 확인할 때 :blackbold:`달리기 1등 학생` 변수에 저장된 값을 불러옵니다.
| 또 1등학생이 홍길동이 맞는지 확인할 때에도 변수에 저장된 값을 불러와 확인합니다.
| 이처럼 변수에 저장된 값을 불러올 때에도 사용됩니다.
|
| 즉 변수는 저장과 불러오기가 가능한 값 입니다.

|
| 다시 3D 펜으로 돌아와 우리는 여기에서 아날로그 값을 저장할 변수를 만들기 위해 변수 블록으로 이동했습니다.
|

.. image:: ../../images/Lv1/Chapter_6/Step1_5.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`변수 만들기` 버튼을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_6.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 변수를 만드는 부분이 나오는데, 여기에서 변수 이름을 ‘신호 값’으로 입력합니다.
| :yellowcircle:`●` 이어서 확인 버튼을 눌러줍니다.
| ※ 이 이름은 정해진 것은 아니며, 여러분들 편한대로 지으셔도 됩니다. 다만 여기에서는 보드에서 오는 아날로그 신호를 측정해볼 것이기 때문에 ‘신호 값’이라고 표현하였습니다. 온도 표에서 아날로그 값에 해당되는 변수입니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_7.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 다음으로 나오는 화면은, 변수 속성등이 나옵니다. 이 부분은 설정을 변경하지 않고, 다시 블록으로 이동합니다.
| :yellowcircle:`●` 이어서 확인 버튼을 눌러줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_8.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 자료 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_9.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`변수 신호 값 보이기` 블록을 이동시켜 줍니다.
| :orangecircle:`●` 이어서 :blackbold:`신호 값 를 10(으)로 정하기` 블록을 순서대로 이동시켜 줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_10.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 하드웨어 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_11.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 여기에서 :blackbold:`아날로그 A0 번 센서값` 블록을 :blackbold:`신호 값 를 10 (으)로 정하기` 블록에 숫자 10 부분에 위치시킵니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_12.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 이어서 시작버튼을 눌러줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step1_13.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 버튼을 누르고 나면, 왼쪽편 화면에 ‘신호 값’이 표시되는 것을 볼 수 있습니다. 지금은 1022 신호값을 받고 있습니다. 이는 온도테이블을 다시 보면 10도 이하임을 알 수 있습니다.
|
|