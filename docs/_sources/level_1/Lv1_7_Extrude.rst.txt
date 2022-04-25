필라멘트 연결하기
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

| 이제 필라멘트를 연결해보려 합니다.
| 필라멘트는 온도가 올라간 상태에서 모터로 밀어내야 노즐 쪽에서 나옵니다.
| 따라서 온도가 올라가지 않은 상태에서는 모터 작동이 안되고, 온도가 올라간 상태에서만 모터 작동이 되어야 합니다.
| 이 조건을 블록으로 만들어 봅니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_1.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 모터 작동시키기와 온도 읽기에서 만들었던 블록들을 가져옵니다. 
| :blackcircle:`●` 혹여나 지웠다면 다시 만들어 보세요.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`q 키를 눌렀을 때` 블록을 마우스 오른쪽 클릭합니다.
| :yellowcircle:`●` 메뉴 중 코드 복사&붙여넣기를 클릭합니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_3.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 복사된 블록을 오른편으로 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_4.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`q 키를 눌렀을 때` 블록에서 q를 클릭합니다.
| :yellowcircle:`●` 원하는 키를 선택해줍니다. 그림에서는 w를 선택했습니다. 
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_5.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`디지털 6번 핀 켜기` 블록에서 켜기를 클릭합니다.
| :yellowcircle:`●` 끄기로 변경해줍니다.
|
|

| 여기까지하면 q와 w를 누르면 모터가 정회전, 역회전을 하게끔 됩니다. 여기에서 온도가 60도에 도달했을 때 모터가 움직일 수 있게 해야합니다.
|

.. image:: ../images/Lv1/Chapter_7/Step1_6.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 흐름 블록을 클릭합니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_7.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`만약 참 (이)라면 ~` 블록을 :blackbold:`q키를 눌럿을 때` 와 :blackbold:`w키를 눌럿을 때` 아래에 각각 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_8.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`디지털 5번 핀 켜기` 블록을 드래그하여, :blackbold:`만일 참 (이)라면` 블록에 이동시켜줍니다.
| :blackcircle:`●` 두 군데 모두 같은 작업을 진행합니다.
|

| 이제 '참'에 해당되는 부분이 온도가 60도에 도달했는지 여부를 넣어주면 됩니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_9.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 판단 블록을 클릭합니다.
| 
|

.. image:: ../images/Lv1/Chapter_7/Step1_10.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`10 = 10` 블록을 :blackbold:`만일 참 (이)라면` 블록의 '참'에 이동시켜줍니다.
| :blackcircle:`●` 두 군데 모두 같은 작업을 진행합니다.
| 
|

.. image:: ../images/Lv1/Chapter_7/Step1_11.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 자료 블록을 클릭합니다.
| 
|


.. image:: ../images/Lv1/Chapter_7/Step1_12.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`온도 값 값` 블록을 :blackbold:`10 = 10` 블록의 오른편으로 이동시켜줍니다.
| :blackcircle:`●` 두 군데 모두 이동시켜 줍니다.
| :orangecircle:`●` :blackbold:`10 = 온도 값 값` 블록의 왼쪽 값을 60으로 변경시켜줍니다.
| 
| 현재 q, w 키를 누르면, 온도값이 60인지 확인하고, 60이라면 모터를 작동하도록 블록을 코딩하였습니다.
| 실제로 :blackbold:`시작하기` 버튼을 눌러 작동을 확인합니다.
|
| 여기까지 진행하느라 수고하셨습니다. 네이버 엔트리로 배워보는 과정은 여기가 마지막입니다. 이제 다음으로 실제 코드를 업로드를 해보고 직접 3D 펜을 사용해보시길 바랍니다.
| 업로드하는 방법은 :ref:`여기 <targetUploadFw>` 를 클릭해주세요.
| 