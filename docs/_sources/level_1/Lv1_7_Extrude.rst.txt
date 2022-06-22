필라멘트 압출하기
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

| 이제 버튼을 누르면 필라멘트가 압출되도록 해보려 합니다.
| 먼저 필라멘트가 압출될려면 온도가 예열된 상태여야 하기 때문에 온도가 목표온도에 도달했는지 부터 확인하는 블록이 필요합니다.
| 온도가 올라가지 않은 상태에서는 모터 작동이 안되고, 온도가 올라간 상태에서만 모터 작동이 되어야 합니다.
| 이 조건을 블록으로 만들어 봅니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_1.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 흐름 블록으로 이동합니다.
| :yellowcircle:`●` :blackbold:`만일 참 (이)라면` 블록을 :blackbold:`만일 참 (이)라면 ~ 아니면 ~` 블록의 아래에 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 판단 블록으로 이동합니다.
| :yellowcircle:`●` :blackbold:`10>10` 블록을 :blackbold:`만일 참 (이)라면` 블록의 아래에 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_3.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 자료 블록으로 이동합니다.
| :yellowcircle:`●` :blackbold:`온도 값 값` 블록을 :blackbold:`10>10` 블록의 왼편에 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_4.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`온도 값 값 > 10` 블록의 오른편 값을 55로 입력합니다.
| :blackcircle:`●` 온도 값을 55 이상으로 설정하는 이유는 60도를 유지를 하려 하지만 60도 이하로 내려갈 수 있기 때문에 여유롭게 모터가 움직이도록 하려고 약간 낮게 움직였습니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_5.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 흐름 블록으로 이동합니다.
| :yellowcircle:`●` :blackbold:`만일 참 (이)라면 ~ 아니면 ~` 블록을 :blackbold:`만일 온도값 값 > 55 (이)라면` 블록의 안쪽에 이동시켜줍니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_6.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 하드웨어 블록으로 이동합니다.
| :yellowcircle:`●` :blackbold:`A 버튼이 눌렸는가` 블록을 :blackbold:`만일 참 (이)라면` 블록의 참 부분에 이동시켜줍니다.
| :blackcircle:`●` 여기까지는 온도가 55도 이상이고, A버튼이 눌릴때에만 작동하도록 준비가 되었습니다. 각각의 칸에 모터 작동코드를 넣어주면 됩니다.
|
|


.. image:: ../images/Lv1/Chapter_7/Step1_7.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`모터 활성화`, :blackbold:`모터를 반시계 방향으로 설정`, :blackbold:`모터 속도를 255으로 설정` 블록을 :blackbold:`만일 A버튼이 눌렸는가 (이)라면 ~ 아니면 ~` 블록의 아래에 이동시켜줍니다.
| :blackcircle:`●` 여기까지의 코드는 A 버튼을 누르면 모터가 작동을 하고, 한번 눌리면 버튼을 떼어도 모터가 작동됩니다. A 버튼이 눌린 상태에만 작동하려면 모터 정지 블록을 만들어야 합니다.
|
|

.. image:: ../images/Lv1/Chapter_7/Step1_8.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`모터 활성화` 블록을 :blackbold:`~아니면 ~` 에 이동시켜줍니다.
| :blackcircle:`●` 이어서 활성화를 비활성화로 변경시켜줍니다.
|

| 지금까지의 블록 순서는 온도, 신호 값을 받아오고, 온도가 60도 를 유지하도록 합니다.
| 온도가 60도 근처가 되면, 모터를 작동할 수 있게 합니다. A 버튼이 눌린 상태에서만 모터가 회전합니다.
|
| 충분히 온도가 오르고, A 버튼을 누르면, 필라멘트가 들어갈 수 있게 됩니다. 이때에는 3D 펜 처럼 사용이 가능합니다. 
| 이제 필라멘트를 제거하는 기능을 추가해야 합니다. 아래와 같은 기능이 작동되도록 코드를 작성해봅니다.
| 
| 1. B 버튼을 누르면 필라멘트가 제거되는 방향으로 회전 동작
| 2. A 버튼이 눌린 상태에는 B 버튼을 눌러도 작동하지 않음
| 3. B 버튼이 눌린 상태에서도 A 버튼이 작동되지 않도록 함
|
| 작성이 완료되면, 아래 버튼을 눌러 코드를 비교해봅니다.
|

.. toggle::

   .. image:: ../images/Lv1/Chapter_7/Step1_9.jpg
      :width: 800
      :align: center

   | :blackcircle:`●` :blackbold:`참 (이)가 아니다` 블록은 판단 블록에 있으며, 참과 거짓을 바꿔주는 블록입니다.

