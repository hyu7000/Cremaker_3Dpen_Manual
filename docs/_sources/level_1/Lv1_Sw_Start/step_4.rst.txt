Step.3 LED 껏다켜기_2
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

| 차이점은 영상 이미지에서 나오는 과정은 LED 전구가 일정시간마다 꺼지고 켜지고를 반복한다는 점입니다.
| 
| 우리는 :blackbold:`시간` 이라는 부분을 설정하지 않았습니다. 아두이노 보드는 1초에 엄청 많은 수를 계산하기 때문에 10회 정도는 눈깜짝할 사이에 지나갑니다.
| 이제 시간을 추가해봅니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step4_1.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 흐름 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step4_2.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`2초 기다리기` 블록을 :blackbold:`디지털 13번 핀 켜기, 끄기` 각각의 블록 아래로 이동시켜줍니다.
| :blackcircle:`●` 블록을 이동시키고 나면, 이제서야 :blackbold:`시작하기` 버튼을 누르면, 전구가 켜지고 2초후 꺼지고 2초후 다시 켜지는 것을 10회 반복하게 됩니다.
|
|

|
| :blackcircle:`1.` LED 전구가 1초 마다 켜지고 꺼지도록 블록을 만들어 볼 것.
| :blackcircle:`2.` 스페이스키를 누를 경우에 LED 전구가 켜지고 엔터키를 누를 경우에 LED 전구가 꺼지도록 블록을 만들어 볼 것.