디스플레이 표시
+++++++++++++++++++

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

| 3D 펜의 디스플레이에 문자를 표시해보려 합니다. 디스플레이는 여러 제품에도 사용됩니다. 폰, TV, 컴퓨터부터 작은 부품들까지 사용됩니다.
| 디스플레이에는 현재 기계, 제품의 상태를 알려줄 수 있습니다. 3D펜에서는 현재 온도가 설정온도에 도달했는지, 냉각중인지, 가열중인지를 표시되도록 하는 것이 목표입니다.
| 
| ※엔트리에서는 원하는 문자를 표시하는 것은 무리가 있으며, 정해진 문자만 표시가 가능합니다.
| 레벨2에서는 원하는 문자를 표시하는 과정이 포함되어 있습니다.
| 
| 

.. image:: ../images/Lv1/Chapter_7/Step1_9.jpg
    :width: 800
    :align: center

|
| 여기까지 블록이 만들지 않았다면, 위 그림대로 만들어 줍니다. 직접 다른 방식으로 작성하였고, 기능이 동일하게 작동한다면, 똑같이 만들지 않아도 됩니다.
|
| 

.. image:: ../images/Lv1/Chapter_8/Step1_1.png
    :width: 800
    :align: center

|
| :blackcircle:`●` 온도 값이 55 이상인 경우 디스플레이에서 OK를 표시하고, 아닌 경우 Heating 을 표시하려 합니다.
| :blackcircle:`●` 현재는 블록이 :blackbold:`만일 온도 값 > 55 (이)라면` 이기 때문에 변경해주어야 합니다.
| :yellowcircle:`●` :blackbold:`만일 온도 값 > 55 (이)라면` 블록을 잠시 빼둡니다.
|
|

.. image:: ../images/Lv1/Chapter_8/Step1_2.png
    :width: 800
    :align: center

|
| :orangecircle:`●` 흐름 블록으로 이동합니다.
| :yellowcircle:`●` :blackbold:`만일 참 (이)라면 ~ 아니면 ~` 블록을 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_8/Step1_3.png
    :width: 800
    :align: center

|
| :orangecircle:`●` 기존에 빼둔 블록들의 부분들을 방금 옮긴 블록으로 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_8/Step1_4.png
    :width: 800
    :align: center

|
| :orangecircle:`●` 하드웨어 블록으로 이동합니다.
| :yellowcircle:`●` :blackbold:`ok를 화면에 표시` 블록을 :blackbold:`만일 온도 값 > 55 (이)라면 ~` 아래에 하나를 이동시켜줍니다.
| :yellowcircle:`●` 다른 하나는 :blackbold:`아니면 ~` 블록에 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_8/Step1_5.png
    :width: 800
    :align: center

|
| :orangecircle:`●` 두번째로 옮겨준 :blackbold:`ok를 화면에 표시` 블록을 heating으로 변경해줍니다.
|
|


| 이제 시작하기 버튼을 눌러 작동상태를 확인하면, 디스플레이에 heating 이 표시되고, 이후 온도가 올라가면, ok가 표시됩니다.
|
|
| 여기까지 진행하느라 수고하셨습니다. 네이버 엔트리로 배워보는 과정은 여기가 마지막입니다. 이제 다음으로 실제 코드를 업로드를 해보고 직접 3D 펜을 사용해보시길 바랍니다.
| 실제 코드를 업로드하는 방법은 엔트리 하드웨어에서 :blackbold:`실사용 펌웨어` 를 업로드 해주시면 됩니다.
| :blackbold:`실사용 펌웨어` 를 업로드 후에는 usb 케이블을 제거하고 사용할 수 있습니다.
| 

.. image:: ../images/Lv1/Chapter_8/Step1_6.png
    :width: 800
    :align: center


