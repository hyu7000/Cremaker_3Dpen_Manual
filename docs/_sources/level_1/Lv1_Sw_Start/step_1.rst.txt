Step.1 설치
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

| 이제 실제로 조립된 3D 펜을 작동시켜 볼 차례입니다. 레벨 1에서 구현할 동작은 모터(기어)를 회전시키는 것과 온도를 확인하고, 재료를 밀어내는 것까지 진행됩니다. 
| 위의 작업들을 가능하게 하려면, SW 코딩을 해야합니다. 어떤 버튼을 누르면 어떻게 작동하라라는 과정을 지시해줘야 하는 과정입니다.
| 
| 레벨1 SW 코딩은 네이버에서 제공하는 엔트리 서비스를 이용합니다. 한글이기도 하고, 깔끔하게 되어 있기 때문입니다.
| 네이버 엔트리는 네이버에서 제공하는 코딩 교육용 프로그램입니다.
| 네이버 엔트리의 주소는 https://playentry.org/ 와 같습니다. 링크를 통해 네이버 엔트리로 이동합니다.
|
| ※ 권장 브라우저는 크롬입니다. 
| ※ 모바일로는 어려움이 있습니다.
|

.. image:: ../../images/Lv1/Chapter_4/0_Mouse_Sign.jpg
   :width: 600
   :align: center

|
| ※ 위 그림는 마우스의 동작을 기호로 나타낸 것입니다. 이 기호는 앞으로도 계속 사용되기 때문에 한번 살펴보시길 바랍니다.


.. image:: ../../images/Lv1/Chapter_4/Step1_1.png
   :width: 600
   :align: center

|
| :orangecircle:`●` 네이버 엔트리에 접속하면 위와 같은 화면이 나옵니다. 여기에서 네이버 엔트리를 시작하려면, 만들기 버튼을 눌러 줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step1_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 위와 같이 나타날 것인데, 우리는 아두이노를 사용할 것이기 때문에 시작하기전에 프로그램 몇개를 설치해줘야 합니다. 아래쪽 하드웨어를 클릭해줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step1_3.png
   :width: 450
   :align: center

|
| :orangecircle:`●` 여기에서 연결 프로그램 다운로드를 눌러줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step1_4.png
   :width: 600
   :align: center

|
| :orangecircle:`●` 아마 이걸 보시는 분의 대부분은 컴퓨터가 윈도우일 것이라 생각합니다. 
| :orangecircle:`●` 윈도우 버전을 다운로드 해줍니다. (Mac이면 macOS를 다운로드)
|
|

.. image:: ../../images/Lv1/Chapter_4/Step1_5.png
   :width: 500
   :align: center

|
| :orangecircle:`●` 설치파일을 실행하면, 다음과 같은 화면이 나타납니다. '다음' 버튼을 눌러줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step1_6.png
   :width: 500
   :align: center

|
| :orangecircle:`●` 이어서 '설치' 버튼을 눌러줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step1_7.png
   :width: 500
   :align: center

|
| :orangecircle:`●` 설치가 완료되면, '다음' 버튼을 눌러줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step1_7.png
   :width: 500
   :align: center

|
| :orangecircle:`●` 이어서 '마침' 버튼을 눌러줍니다.