메인 케이스 상단 디자인
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. raw:: html

    <style> 
    .orangecircle {color:#ff5300; font-size:20px} 
    .blackcircle {color:black; font-size:20px} 
    .bluecircle {color:#3172f4; font-size:20px}
    .redcircle {color:red; font-size:20px}
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
.. role:: redcircle
.. role:: skybluecircle
.. role:: yellowcircle
.. role:: subtitle
.. role:: subtitlesmall
.. role:: blackbold
.. role:: redbold

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_1.jpg
   :width: 800
   :align: center

|
| 네 번째로 진행해볼 부품은 3D 펜의 메인 케이스중 하단부품입니다.
| 디자인은 위와 같습니다. 4개의 부품 중에 가장 복잡해보입니다만 시작해보면 크게(?) 어렵진 않습니다.
| 시작해보겠습니다.
| 

| :subtitle:`Step.1`

| FreeCad 프로그램을 실행해줍니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Box_1.png
   :width: 800
   :align: center

| 
| :orangecircle:`●` :blackbold:`새로 만들기` 버튼을 눌러줍니다.
| 

| :subtitle:`Step.2`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Box_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 화면이 바뀌면 상단의 :blackbold:`Start` 버튼을 :blackbold:`Part Design` 으로 변경해줍니다.
|

| :subtitle:`Step.3`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_2.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` x,y,z 축과 만나는 선을 그릴 때는 먼저 선을 다른 곳에 그리고, '점을 선에 일치' 버튼으로 붙여줍니다.
| :blackcircle:`●` 작성 후 스케치를 빠져나옵니다.
|

| :subtitle:`Step.4`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_3.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 회전 버튼을 눌러줍니다.
| :yellowcircle:`●` 축 항목을 '절대좌표계 Y축' 으로 변경해줍니다.
| :bluecircle:`●` 각도 항목을 180°로 입력합니다.
| :redcircle:`●` 작업을 편하게 하기 위해 Reverse 항목을 체크하여, 아래쪽으로 회전되도록 합니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.5`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_4.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 다시 XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 왼편, 오른편은 서로 대칭입니다.
| :blackcircle:`●` 작성 후 스케치를 빠져나옵니다.
|

| :subtitle:`Step.6`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_5.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목 3.75mm 를 입력합니다.
| :bluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.7`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_6.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XZ 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
|

| :subtitle:`Step.8`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_7.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 <hoverxref:extrude>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 78mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.9`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_8.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 다시 XZ 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
|

| :subtitle:`Step.10`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_9.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 <hoverxref:extrude>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 8mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.11`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_10.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 다시 XZ 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
|

| :subtitle:`Step.12`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_11.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 8mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
|

|
| 여기에서는 튜브가 들어가는 공간을 만들어 줘야 합니다. 기울어진 홈이 있기 때문에 선과 평면을 만들어 줘야 합니다.
| 

| :subtitle:`Step.13`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_12.png
   :width: 800
   :align: center

|
| :blackcircle:`●` YZ 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
|

| :subtitle:`Step.14`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_13.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`평면 생성 <hoverxref:generatePlane>` 버튼을 눌러줍니다.
| :bluecircle:`●` 그림과 같이 가운데 원형 모양을 선택해줍니다.
|

| :subtitle:`Step.15`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_14.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 평면이 뒤로 살짝 이동하도록 왼쪽 창의 항목 중 In Z-direction 을 -5mm 로 입력합니다.
| :bluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.16`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_15.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 생성한 평면에 스케치를 생성해주고, 그림과 같이 스케치를 작성합니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
|

| :subtitle:`Step.17`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_16.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :bluecircle:`●` Length 항목은 46.5mm 를 입력해줍니다.
|

| :subtitle:`Step.18`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_17.png
   :width: 800
   :align: center

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_17_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` Direction/edge 항목은 select reference.. 로 변경해줍니다.
| :bluecircle:`●` step.13에서 만든 선을 선택합니다.
| :yellowcircle:`●` 잘 보이지 않는다면, 보기 - 그리기 스타일 - 와이어 프레임을 선택해줍니다.
| :skybluecircle:`●` 방향이 달라서 적용이 안된 것 처럼 보일 수 있으니 Reverse 항목을 체크해줍니다.
| :blackcircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.19`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_18.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 작업 편의를 위해 평면을 숨겨줍니다.
| :orangecircle:`●` 생성된 평면을 선택합니다.
| :yellowcircle:`●` 보기 - 표시 여부 - 선택영역 숨기기를 선택해줍니다.
|

| :subtitle:`Step.20`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_19.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XZ 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.21`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_20.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 <hoverxref:extrude>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 4mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

|
| 노즐은 온도가 높게 올라가기 때문에, 노즐쪽에 열기를 빠져나갈 수 있는 통로를 만들어 줍니다.
|

| :subtitle:`Step.22`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_21.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.23`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_22.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 20mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.24`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_23.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` Y축을 기준으로 좌우 대칭입니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.25`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_24.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 <hoverxref:extrude>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 2.25mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

|
| 이제는 모터가 들어갈 공간과 필라멘트가 투입할 수 있는 부분을 모델링 해보겠습니다.
|

| :subtitle:`Step.26`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_25.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` Y축을 기준으로 좌우 대칭입니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.27`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_26.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 20mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.28`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_27.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` Y축을 기준으로 좌우 대칭입니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.29`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_28.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 9.2mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.30`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_29.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` Y축을 기준으로 좌우 대칭입니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.31`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_30.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 1.2mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.32`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_31.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` Y축을 기준으로 좌우 대칭입니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.33`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_32.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 20mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.34`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_33.png
   :width: 800
   :align: center

| 
| :orangecircle:`●` :hoverxref:`평면 생성 <hoverxref:generatePlane>` 버튼을 눌러줍니다.
| :yellowcircle:`●` 모형의 뒷면을 선택해줍니다.
| :bluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.35`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_34.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 방금 생성한 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.36`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_35.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 30mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.37`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_36.png
   :width: 800
   :align: center

|
| :blackcircle:`●` XY 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` Y축을 기준으로 좌우 대칭입니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.38`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_37.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 15mm 를 입력합니다.
| :yellowcircle:`●` 2nd Length 항목은 -11mm 를 입력합니다.
| :bluecircle:`●` 확인 버튼을 눌러줍니다.
| 

|
| 여기까지 모터와 필라멘트 투입구를 마무리 하였습니다. 이제 부품을 조립함에 있어서 메인케이스 상단과 하단을 연결시켜주는 부분을 만들어 보도록 하겠습니다.
|

| :subtitle:`Step.39`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_38.png
   :width: 800
   :align: center

|
| :blackcircle:`●` Step.34에서 생성한 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.40`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_39.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 <hoverxref:extrude>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 5mm 를 입력합니다.
| :bluecircle:`●` 방향이 다르다면 Reverse 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.41`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_40.png
   :width: 800
   :align: center

|
| :blackcircle:`●` Step.34에서 생성한 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 파란선은 보조선입니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 


| :subtitle:`Step.42`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_41.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 73.5mm 를 입력합니다.
| :yellowcircle:`●` 2nd Length 항목은 -5mm 를 입력합니다.
| :bluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.43`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_42.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 작업 편의를 위해 평면을 숨겨줍니다.
| :orangecircle:`●` 생성된 평면을 선택합니다.
| :yellowcircle:`●` 보기 - 표시 여부 - 선택영역 숨기기를 선택해줍니다.
|

|
| 메인 케이스의 상단, 하단을 연결 시켜주는 부분까지 모델링도 했습니다. 이제는 모델링의 뾰족한 부분을 모따기로 다듬어 주도록 합니다.
|

| :subtitle:`Step.44`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_43.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 두 개의 모서리 부분을 선택해줍니다. 2개 이상 선택시 ctrl 키를 누른 상태에서 클릭합니다.
| :orangecircle:`●` :hoverxref:`모따기 <hoverxref:chamfer>` 버튼을 눌러줍니다.
| :bluecircle:`●` 크기를 2.2mm 로 입력합니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.45`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_44.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 두 개의 모서리 부분을 선택해줍니다. 2개 이상 선택시 ctrl 키를 누른 상태에서 클릭합니다.
| :orangecircle:`●` :hoverxref:`모따기 <hoverxref:chamfer>` 버튼을 눌러줍니다.
| :bluecircle:`●` 크기를 0.5mm 로 입력합니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| :blackcircle:`●` 모따기 중 치수 관련 에러가 나타날 수 있습니다. 치수를 변경해줍니다.
|

| :subtitle:`Step.46`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_45.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 세 개의 모서리 부분을 선택해줍니다. 2개 이상 선택시 ctrl 키를 누른 상태에서 클릭합니다.
| :orangecircle:`●` :hoverxref:`모따기 <hoverxref:chamfer>` 버튼을 눌러줍니다.
| :bluecircle:`●` 크기를 0.5mm 로 입력합니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.47`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_46.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 안쪽의 필라멘트가 투입되는 모서리 부분을 선택해줍니다.
| :orangecircle:`●` :hoverxref:`모따기 <hoverxref:chamfer>` 버튼을 눌러줍니다.
| :bluecircle:`●` 크기를 0.5mm 로 입력합니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.48`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_47.png
   :width: 800
   :align: center

|
| :blackcircle:`●` YZ 평면에 위와 같은 스케치를 작성해 줍니다.
| :blackcircle:`●` 스케치 그리기 전 View section 기능을 사용해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
| 

| :subtitle:`Step.49`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_48.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :hoverxref:`돌출 컷 <hoverxref:extrudeCut>` 버튼을 눌러줍니다.
| :yellowcircle:`●` Length 항목은 10mm 를 입력합니다.
| :bluecircle:`●` symmetric to plane 항목을 체크해줍니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

| :subtitle:`Step.50`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX4_49.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 두 개의 모서리 부분을 선택해줍니다. 2개 이상 선택시 ctrl 키를 누른 상태에서 클릭합니다.
| :orangecircle:`●` :hoverxref:`모따기 <hoverxref:chamfer>` 버튼을 눌러줍니다.
| :bluecircle:`●` 크기를 1mm 로 입력합니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| 

|
| 모서리 부분도 전부 모따기를 해주었습니다.
| 네 번쨰 부품인 메인 케이스 하단 모델링도 완성이 되었습니다.
| 어려웠다면 어렵고, 쉽다면 쉬울 수 있었는 모델링이었습니다.
| 이 모형들을 실제로 3D 프린터로 출력하면, 부품으로 사용이 될 수 있습니다.
|