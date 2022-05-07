.. _targetUploadFw:

업로드하기
===============================================
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

| 아두이노 프로그램으로 보드에 소스를 업로드 해보는 과정입니다.
|
| 먼저 아두이노라는 프로그램을 다운받으셔야 합니다. https://www.arduino.cc/ 에 접속합니다.
| ※ 현재 설치 과정은 2022.04.14 날짜 기준입니다.
|
| 설치가 이미 되어 있는 분들은 :ref:`여기 <targetUpload>` 로 이동합니다.
|

.. image:: /images/UploadFW/Step1_1.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 상단 메뉴중 SOFTWARE를 클릭합니다.
|
|

.. image:: /images/UploadFW/Step1_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 오른편의 Winodws Win 7 and newer 를 클릭합니다.
| :blackcircle:`●` macOS, Linux 를 사용하신다면, 종류에 맞게 클릭하시면 됩니다.
|
|

.. image:: /images/UploadFW/Step1_3.png
   :width: 800
   :align: center

|
| :orangecircle:`●` JUST DOWNLOAD 를 클릭합니다. 
| :blackcircle:`●` 버튼처럼 생기지 않아서 헷갈릴 수 있습니다. CONTRIBUTE & DOWNLOAD는 기부와 함께 다운로드를 뜻합니다.
|
|

.. image:: /images/UploadFW/Step1_4.png
   :width: 400
   :align: center

|
| :blackcircle:`●` 설치파일을 실행합니다.
| :orangecircle:`●` 나오는 창에서 :blackbold:`I Agree` 버튼을 클릭합니다.
|
|

.. image:: /images/UploadFW/Step1_5.png
   :width: 400
   :align: center

|
| :orangecircle:`●` 이어서 :blackbold:`Next` 버튼을 클릭합니다.
|
|

.. image:: /images/UploadFW/Step1_6.png
   :width: 400
   :align: center

|
| :orangecircle:`●` 이어서 :blackbold:`Install` 버튼을 클릭합니다.
|
|

.. image:: /images/UploadFW/Step1_7.png
   :width: 400
   :align: center

|
| :orangecircle:`●` 설치가 완료되면, :blackbold:`Close` 버튼을 클릭합니다.
|
|

.. _targetUpload:

:download:`코드 파일 </codefile/Cremaker3DPen.zip>`

|
| :blackcircle:`●` 위의 코드 파일을 다운로드 받습니다.
|
|

.. image:: /images/UploadFW/Step1_8.png
   :width: 400
   :align: center

|
| :orangecircle:`●` 다운로드 받은 뒤, 파일에 마우스 오른쪽 클릭 후 압축을 풀어줍니다.
|
|

.. image:: /images/UploadFW/Step1_9.png
   :width: 250
   :align: center

|
| :blackcircle:`●` 이후 Cremaker3DPen 파일을 실행합니다.
|
|

.. image:: /images/UploadFW/Step1_10.png
   :width: 600
   :align: center

|
| :orangecircle:`●` 잠시 팝업이 나타나는데 여기서 :blackbold:`확인` 버튼을 눌러줍니다.
|
|

.. image:: /images/UploadFW/Step1_11.png
   :width: 600
   :align: center

|
| :orangecircle:`●` 메뉴 중 툴-라이브러리 관리를 클릭합니다.
| :blackcircle:`●` 라이브러리에 관련된 설명은 레벨 1 범위에서는 다루지 않습니다만. 간단히 설명드리면, 누군가 미리 만들어 놓은 코드들이라고 보시면 됩니다.
| :blackcircle:`●` 디스플레이를 켜고 조절하는 코드들을 다운로드 해볼 겁니다.
|
|

.. image:: /images/UploadFW/Step1_12.png
   :width: 600
   :align: center

|
| :yellowcircle:`●` 검색창에 SSD1306 을 입력합니다.
| :bluecircle:`●` 검색 결과에서 SSD1306 이름이고, by Alexey Dynda 로 표시된 부분을 찾아줍니다.
| :orangecircle:`●` 오른편의 설치 버튼을 눌러줍니다.
| :blackcircle:`●` 디스플레이 관련 코드가 설치되었습니다. 설치는 어렵지 않습니다.
|
|

.. .. image:: /images/UploadFW/Step1_13.png
..    :width: 600
..    :align: center

.. |
.. | :blackcircle:`●` 이제 시간과 관련된 코드를 다운로드 해보려 합니다.
.. | :yellowcircle:`●` 검색창에 everytimer 를 입력합니다.
.. | :blackcircle:`●` 검색 결과에서 everytimer 이름이고, by Alessio Leoncini 로 표시된 부분을 찾아줍니다.
.. | :orangecircle:`●` 오른편의 설치 버튼을 눌러줍니다.
.. |

| 이제 필요한 코드들은 모두 다운로드 받았습니다. 이제 업로드만 남아 있습니다.
|
|

.. image:: /images/UploadFW/Step1_14.png
   :width: 600
   :align: center

|
| :blackcircle:`●` 보드의 종류를 선택을 해야 합니다.
| :orangecircle:`●` 메뉴중 툴을 클릭합니다.
| :bluecircle:`●` 보드 항목을 클릭합니다.
| :yellowcircle:`●` Arduino Nano 를 선택해줍니다.
|
|

.. image:: /images/UploadFW/Step1_14_2.png
   :width: 600
   :align: center

|
| :blackcircle:`●` 보드의 프로세서도 선택합니다.
| :orangecircle:`●` 메뉴중 툴을 클릭합니다.
| :bluecircle:`●` 프로세서 항목을 클릭합니다.
| :yellowcircle:`●` ATmega328P (Old bootloader) 를 선택해줍니다.
|
|

.. image:: /images/UploadFW/Step1_15.png
   :width: 600
   :align: center

|
| :blackcircle:`●` 이제는 USB 포트를 선택해야 합니다. 포트 번호는 USB 소켓 위치에 따라 다릅니다.
| :orangecircle:`●` 메뉴중 툴을 클릭합니다.
| :bluecircle:`●` 포트 항목을 클릭합니다.
| :yellowcircle:`●` 현재 활성화된 포트를 클릭합니다.
| ※다른 USB 연결된 것이 있으면 포트가 여러개 일 수 있습니다.
|
|

.. image:: /images/UploadFW/Step1_16.png
   :width: 600
   :align: center

|
| :orangecircle:`●` 마지막으로 왼편 상단의 업로드 버튼을 눌러줍니다.
|
|

| 혹여나 정상적으로 업로드가 되지 않았다면, 현재 실행중인 프로그램을 모두 종료하고 진행해봅니다.