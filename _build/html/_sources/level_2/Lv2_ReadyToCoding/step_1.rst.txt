아두이노 설치
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. raw:: html

    <style> 
    .orangecircle {color:#ff5300; font-size:20px} 
    .blackcircle {color:black; font-size:20px} 
    .bluecircle {color:#3172f4; font-size:20px}
    .skybluecircle {color:#00FFFF; font-size:20px}
    .yellowcircle {color:#fbbc05; font-size:20px}
    .subtitle {color:black; font-weight:bold; font-size:28px}
    .subtitlesmall {color:black; font-weight:bold; font-size:24px}
    .blackbold {color:black; font-weight:bold;}
    .redbold {color:red; font-weight:bold;}
    </style>

.. role:: orangecircle
.. role:: blackcircle
.. role:: bluecircle
.. role:: skybluecircle
.. role:: yellowcircle
.. role:: subtitle
.. role:: subtitlesmall
.. role:: blackbold
.. role:: redbold

| 아두이노를 설치하고 간단한 설정을 하는 과정입니다.
|
| 먼저 아두이노라는 프로그램을 다운받으셔야 합니다. https://www.arduino.cc/ 에 접속합니다.
| ※ 현재 과정은 2022.04.14 날짜 기준입니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/0_Mouse_Sign.jpg
   :width: 600
   :align: center

|
| ※ 위 그림는 마우스의 동작을 기호로 나타낸 것입니다. 이 기호는 앞으로도 계속 사용되기 때문에 한번 살펴보시길 바랍니다.

.. image:: ../../images/UploadFW/Step1_1.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 상단 메뉴중 SOFTWARE를 클릭합니다.
|
|

.. image:: ../../images/UploadFW/Step1_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 오른편의 Winodws Win 7 and newer 를 클릭합니다.
| :blackcircle:`●` macOS, Linux 를 사용하신다면, 종류에 맞게 클릭하시면 됩니다.
|
|

.. image:: ../../images/UploadFW/Step1_3.png
   :width: 800
   :align: center

|
| :orangecircle:`●` JUST DOWNLOAD 를 클릭합니다. 
| :blackcircle:`●` 버튼처럼 생기지 않아서 헷갈릴 수 있습니다. CONTRIBUTE & DOWNLOAD는 기부와 함께 다운로드를 뜻합니다.
|
|

.. image:: ../../images/UploadFW/Step1_4.png
   :width: 400
   :align: center

|
| :blackcircle:`●` 설치파일을 실행합니다.
| :orangecircle:`●` 나오는 창에서 :blackbold:`I Agree` 버튼을 클릭합니다.
|
|

.. image:: ../../images/UploadFW/Step1_5.png
   :width: 400
   :align: center

|
| :orangecircle:`●` 이어서 :blackbold:`Next` 버튼을 클릭합니다.
|
|

.. image:: ../../images/UploadFW/Step1_6.png
   :width: 400
   :align: center

|
| :orangecircle:`●` 이어서 :blackbold:`Install` 버튼을 클릭합니다.
|
|

.. image:: ../../images/UploadFW/Step1_7.png
   :width: 400
   :align: center

|
| :orangecircle:`●` 설치가 완료되면, :blackbold:`Close` 버튼을 클릭합니다.
|
|

.. image:: ../../images/UploadFW/Step1_8.png
   :width: 300
   :align: center

|
| :blackcircle:`●` 이후 바탕화면에 아두이노 아이콘을 더블클릭하여 실행합니다.
|
|

| 실제 코딩을 하기전 라이브러리 라는 것을 설치해야 합니다.
| 라이브러리는 말 그대로 누군가 먼저 작성해놓은 것들의 모음입니다.
| 디스플레이에 숫자를 나타내는 것이나 시간을 제어하는 것들을 좀 더 편하게 쓰기 위해, 제조사측에서 제공해주거나 혹은
| 일반 사용자들이 개발하기도 합니다.
| 이 3D 펜을 사용함에 있어서 2가지 라이브러리를 설치해야합니다.
|
|

.. image:: ../../images/UploadFW/Step1_11.png
   :width: 600
   :align: center

|
| :orangecircle:`●` 메뉴 중 툴-라이브러리 관리를 클릭합니다.
| :blackcircle:`●` 디스플레이를 켜고 조절하는 라이브러리를 다운로드 해볼 겁니다.
|
|

.. image:: ../../images/UploadFW/Step1_12.png
   :width: 600
   :align: center

|
| :yellowcircle:`●` 검색창에 SSD1306 을 입력합니다.
| :bluecircle:`●` 검색 결과에서 SSD1306 이름이고, by Alexey Dynda 로 표시된 부분을 찾아줍니다.
| :orangecircle:`●` 오른편의 설치 버튼을 눌러줍니다.
| :blackcircle:`●` 디스플레이 관련 코드가 설치되었습니다. 설치는 어렵지 않습니다.
|
|

.. image:: ../../images/Lv1/Chapter_4/Step2_2.png
   :width: 600
   :align: center

|
| :blackcircle:`●` USB 케이블을 이용하여, 컴퓨터와 3D 펜의 보드를 연결시켜줍니다.
|
|

| 이제 코딩을 할 준비가 완료되었습니다. 다음 단계로 갑니다.