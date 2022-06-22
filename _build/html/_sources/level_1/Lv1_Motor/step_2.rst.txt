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

| 3D 펜의 버튼을 눌러 모터를 회전 시켜볼 계획입니다. 코딩 맛보기에서 버튼을 사용하기 위해 만들었던 코드 블록들을 다시 준비합니다.
|


.. image:: ../../images/Lv1/Chapter_4/Step3_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 시작 블록으로 이동합니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_3.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`시작하기 버튼을 클릭했을 때` 를 가져옵니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step3_4.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 흐름 블록으로 이동합니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step5_5.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`계속 반복하기` 블록을 가져옵니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step2_1.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`만약 참 (이)라면 ~` 블록을 :blackbold:`계속 반복하기` 블록 안에 이동시켜줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step2_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 하드웨어 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step2_3.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`A 버튼이 눌렸는가?` 블록을 :blackbold:`만일 참 (이)라면 ~` 에서 `참` 부분에 이동시켜줍니다.
| :blackbold:`●` 버튼이 눌렸으면 아래 블록을 실행하게 합니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step2_4.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 먼저 모터를 On, Off 하는 블록부터 만들어 보겠습니다. :blackbold:`모터 활성화` 블록을 이동시킵니다.
| :blackcircle:`●` :blackbold:`모터 활성화` 블록은 모터를 On 해주는 블록입니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step2_5.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`모터를 반시계 방향으로 설정` 블록을 가져옵니다.
| :blackcircle:`●` 이 블록은 모터가 회전하는 방향을 설정해줍니다. 시계, 반시계 중 원하는 방향을 설정합니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step2_6.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`모터 속도를 255으로 설정` 블록을 가져옵니다.
| :blackcircle:`●` 이 블록은 모터의 회전 속도를 설정합니다 최소 0 에서 최대 255까지 설정할 수 있습니다.
|
|

.. image:: ../../images/Lv1/Chapter_5/Step2_7.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`시작하기` 버튼을 누르고 3D 펜이서 A 버튼이 눌러 봅니다.
|

|
| :blackcircle:`●` 모터가 움직이나요? 그렇다면 다양한 방법으로 모터를 움직여 봅시다.
|
| :blackcircle:`1.` B 버튼을 누르면, 모터가 정지
| :blackcircle:`2.` C 버튼을 누르면, 모터가 반대 방향으로 회전
| :blackcircle:`3.` D 버튼을 누르면, 모터 속도가 절반으로 줄어들기
| 