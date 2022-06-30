필라멘트 투입구 디자인
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


| 3D 펜의 부품 4개를 모델링 해보려 합니다. 가장 쉬운 모델부터 어려운 모델순으로 진행하도록 하겠습니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_1.jpg
   :width: 800
   :align: center

|
| 디자인 해볼 형상과 도면입니다. 도면의 단위는 mm 입니다.

|
| 첫 번째는 3D 펜에서 조립했던 필라멘트 투입구를 디자인 해보려 합니다.
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

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_3.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :스케치 생성 버튼을 누르고, XZ 평면을 선택해줍니다.
|

| :subtitle:`Step.4`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_4.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 원을 중심에 그릴 것이기 때문에, 원 버튼을 누르고, 중심에 마우스를 가져갑니다.
| :blackcircle:`●` 마우스를 중심에 가져가면 점 일치 아이콘이 나타납니다.
| :blackcircle:`●` 클릭을 하여 원을 그려주면, 축의 교차점에 원이 중심이 되고 원이 그려집니다.
|

| :subtitle:`Step.5`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_5.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 원의 지름은 7mm로 정해줍니다.
| :blackcircle:`●` 지름 설정은 Constrain arc or circle 을 사용합니다.
| 

| :subtitle:`Step.6`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_6.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 작은 원을 하나 더 추가하여 지름을 4.6mm로 설정해줍니다.
| :orangecircle:`●` 닫기 버튼을 누르고 스케치를 빠져나갑니다.
|

| :subtitle:`Step.7`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_7.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 돌출 버튼을 눌러줍니다.
| :yellowcircle:`●` 왼편의 창에서 Length를 56mm 로 설정해줍니다.
| :bluecircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.8`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_8.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 평면 생성 버튼을 눌러줍니다.
| :yellowcircle:`●` 돌출된 끝의 원형 면을 선택해줍니다.
| :bluecircle:`●` 확인 버튼을 눌러줍니다.
| :blackcircle:`●` 생성된 평면에서 스케치를 작성할 계획입니다.
|

| :subtitle:`Step.9`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_9.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 스케치 생성 버튼을 눌러줍니다.
| :yellowcircle:`●` 만들어진 평면을 선택해줍니다.
|

| :subtitle:`Step.10`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_10.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 사각형 버튼을 눌러줍니다.
| :yellowcircle:`●` 그림과 같이 사각형을 그려줍니다.
|

| :subtitle:`Step.11`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_11.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 수평 거리 설정 버튼을 눌러줍니다.
| :blackcircle:`●` 사각형의 상단 직선을 클릭하고, 11.4mm 를 입력해줍니다.
|

| :subtitle:`Step.12`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_12.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 수직 거리 설정 버튼을 눌러줍니다.
| :blackcircle:`●` 사각형의 옆 직선을 클릭하고, 9.15mm 를 입력해줍니다.
|

| :subtitle:`Step.13`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_13.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 수평 거리 설정 버튼을 눌러줍니다.
| :bluecircle:`●` 중심점을 먼저 선택해줍니다.
| :yellowcircle:`●` 사각형의 꼭지점을 이어서 선택해주고, 길이를 5.7mm 를 입력해줍니다.
| :blackcircle:`●` 입력이 완료되면 사각형이 좌우로 중심에 맞춰집니다.
|

| :subtitle:`Step.14`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_14.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 수평 거리 설정 버튼을 눌러줍니다.
| :bluecircle:`●` 중심점을 먼저 선택해줍니다.
| :yellowcircle:`●` 사각형의 아래부분 꼭지점을 이어서 선택해주고, 길이를 6.85mm 를 입력해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
|

| :subtitle:`Step.15`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_15.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 원 버튼을 선택해줍니다.
| :bluecircle:`●` 중심을 기준으로 지름 4.6mm 원을 그려줍니다.
|

| :subtitle:`Step.16`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_16.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 돌출 버튼을 선택해줍니다.
| :bluecircle:`●` Length는 7mm로 입력해줍니다.
| :yellowcircle:`●` 확인 버튼을 눌러줍니다.
| :skybluecircle:`●` 평면 밖으로 돌출 된다면, Reversed 항목을 눌러주세요.
|

| :subtitle:`Step.17`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_17.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 스케치 생성 버튼을 눌러줍니다.
| :yellowcircle:`●` 생성된 평면을 선택해줍니다.
|

| :subtitle:`Step.18`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_18.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 원 버튼을 눌러줍니다.
| :bluecircle:`●` 중심에 지름 4.6mm 인 원을 그려줍니다.
|

| :subtitle:`Step.19`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_19.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 사각형 버튼을 눌러줍니다.
| :bluecircle:`●` 그려진 도형의 상단쯤에 그려줍니다.
|

| :subtitle:`Step.20`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_20.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 수직 거리 설정 버튼을 눌러줍니다.
| :bluecircle:`●` 중심점을 선택해주고,
| :yellowcircle:`●` 사각형 아래꼭지점을 선택해줍니다.
| :blackcircle:`●` 거리는 2.3mm 를 입력합니다.
|

| :subtitle:`Step.21`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_21.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 선 버튼을 눌러줍니다.
| :bluecircle:`●` 사각형 아래쪽 부분을 클릭해줍니다. 클릭하면 선이 그려지기 시작합니다.
| :yellowcircle:`●` 원을 접하게 지나가도록 선을 그려줍니다.
| :skybluecircle:`●` 원과 선이 접하는 표시가 나타날 때, 클릭을 합니다.
|

| :subtitle:`Step.22`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_22.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 그려진 선에 접함 기호가 있는지 확인해줍니다.
|

| :subtitle:`Step.23`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_23.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 방금 그린 직선을 클릭합니다.
| :bluecircle:`●` 중심에 있는 축(초록색)을 클릭합니다.
| :yellowcircle:`●` 이후 대칭 버튼을 클릭해주면, 초록색 축의 반대편에 대칭으로 직선이 그려집니다.
| 

| :subtitle:`Step.23`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_23.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 방금 그린 직선을 클릭합니다.
| :bluecircle:`●` 중심에 있는 축(초록색)을 클릭합니다.
| :yellowcircle:`●` 이후 대칭 버튼을 클릭해주면, 초록색 축의 반대편에 대칭으로 직선이 그려집니다.
| 

| :subtitle:`Step.24`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_24.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 대칭 버튼을 눌러줍니다.
| :bluecircle:`●` 중앙에 그린 원을 선택합니다.
| :yellowcircle:`●` 왼편에 그려진 선을 선택하면, 원과 선이 접하게 됩니다.
|

| :subtitle:`Step.25`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_25.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 점을 선에 일치 버튼을 눌러줍니다.
| :bluecircle:`●` 사각형 아래 선을 선택해줍니다.
| :yellowcircle:`●` 이어서 왼편 직선의 윗 점을 클릭해주면, 사각형 아래 선과 점이 만나게 됩니다.
| :blackcircle:`●` 곂쳐있지만 실제로 고정되어 있지 않을 수 있기 때문에 구속을 넣어주어야 합니다.
|

| :subtitle:`Step.26`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_26.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 수평 거리 설정 버튼을 눌러줍니다.
| :bluecircle:`●` 사각형과 직선이 만나는 왼편의 점을 선택하고
| :yellowcircle:`●` 오른편의 점을 선택합니다. 거리는 3.5mm 를 입력합니다.
|

| :subtitle:`Step.27`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_27.png
   :width: 800
   :align: center

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_27_2.jpg
   :width: 800
   :align: center

|
| :orangecircle:`●` 잘라내기 버튼을 눌러줍니다.
| :bluecircle:`●` 파란원으로 표시된 부분들을 클릭하여 제거합니다.
| :blackcircle:`●` 아래 사진 처럼 만들어 줍니다.
| :blackcircle:`●` 완료되면, 닫기 버튼을 눌러 스케치를 빠져나옵니다.
|

| :subtitle:`Step.28`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_28.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 돌출 컷 버튼을 눌러줍니다.
| :bluecircle:`●` 왼쪽 창에서 Length를 20mm로 입력해줍니다.
| :yellowcircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.29`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_29.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 이전에 만든 평면은 당분간 사용하지 않으니 잠시 숨겨둡니다.
| :orangecircle:`●` 평면을 선택해줍니다.
| :yellowcircle:`●` 보기- 표시 여부 - 선택영역 숨기기 로 숨겨줍니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_29_2.png
   :width: 600
   :align: center

|
| :blackcircle:`●` 다음 단계 부터 아랫 부분(A)을 그려보겠습니다.
| :blackcircle:`●` 이제부터는 자주 사용된 기능이나 간단한 과정들은 위치와 방법은 생략하도록 하겠습니다.
|

| :subtitle:`Step.30`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_30.png
   :width: 800
   :align: center

|
| :bluecircle:`●` 평면 생성 버튼을 눌러줍니다.
| :orangecircle:`●` 아랫면을 클릭해줍니다.
| :yellowcircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.31`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_31.png
   :width: 800
   :align: center
   
|
| :orangecircle:`●` 스케치 생성 버튼을 눌러줍니다.
| :yellowcircle:`●` 방금 만든 평면을 선택해줍니다.
|

| :subtitle:`Step.32`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_32.png
   :width: 800
   :align: center
   
|
| :orangecircle:`●` 외부 Geometry 버튼을 눌러줍니다.
| :yellowcircle:`●` 그림에서 나타나는 사각형의 상단부분을 클릭해줍니다.
| :blackcircle:`●` 외부 Geometry는 만들어진 모형에 나타나는 선을 스케치로 가져오는 기능입니다.
| :blackcircle:`●` 완료되면 상단부분에 선이 나타난 것을 확인할 수 있습니다.
| :blackcircle:`●` 이 선은 자동으로 보조선으로 적용됩니다.
|

| :subtitle:`Step.33`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_33.png
   :width: 800
   :align: center
   
|
| :orangecircle:`●` 원 버튼을 선택해줍니다.
| :bluecircle:`●` 사각형 가운데 쯤 원을 그려줍니다.
|

| :subtitle:`Step.34`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_34.png
   :width: 800
   :align: center
   
|
| :orangecircle:`●` 지름과 수직 거리 설정을 이용하여 위와 같이 설정해줍니다.
| :blackcircle:`●` 완료되면, 닫기 버튼으로 스케치를 빠져나옵니다.
|

| :subtitle:`Step.35`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_35.png
   :width: 800
   :align: center
   
|
| :orangecircle:`●` 돌출 컷 버튼을 눌러줍니다.
| :bluecircle:`●` Length 를 4mm 로 입력해줍니다.
| :yellowcircle:`●` 확인 버튼을 눌러줍니다.
|

| :subtitle:`Step.36`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_36.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 스케치 생성 버튼을 눌러줍니다.
| :bluecircle:`●` 방금 작업했던 평면과 동일한 평면을 선택해줍니다.
|

| :subtitle:`Step.37`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_37.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 외부 Geometry 버튼을 눌러줍니다.
| :yellowcircle:`●` 원 부분을 클릭해줍니다.
| :blackcircle:`●` 선택이 완료되면, 원 모양의 보조선이 생성됩니다.
|

| :subtitle:`Step.38`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_38.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 다각형 버튼을 눌러줍니다.
| :bluecircle:`●` 원의 중심을 클릭해줍니다.
| :yellowcircle:`●` 두번째 클릭은 아래로 살짝 이동 후 초록색 선에 클릭해줍니다.
| :blackcircle:`●` 완료되면 다각형이 그려집니다.
|

| :subtitle:`Step.39`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_39.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 수평 거리 설정 버튼을 눌러줍니다.
| :bluecircle:`●` 육각형 왼편 아래 부분의 꼭지점을 클릭해줍니다.
| :yellowcircle:`●` 육각형 오른편 아래 부분의 꼭지점을 클릭해줍니다.
| :blackcircle:`●` 치수는 5mm 를 입력해줍니다.
|

| :subtitle:`Step.40`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_40.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 선 버튼을 눌러줍니다.
| :bluecircle:`●` 육각형 왼편 윗 부분의 꼭지점을 클릭해줍니다.
| :yellowcircle:`●` 위로 올려 윗 공간에 클릭해줍니다.
| :skybluecircle:`●` 클릭전에 수직인 표시가 나타나는지 확인하고 클릭합니다.
| :blackcircle:`●` 반대편에도 직선을 그려줍니다.
|

| :subtitle:`Step.41`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_41.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 선 버튼을 눌러줍니다.
| :bluecircle:`●` 방금 그린 직선의 윗 부분 점을 클릭해줍니다.
| :yellowcircle:`●` 마우스를 옆으로 이동시켜, 반대편 직선 위에서 클릭해줍니다.
| :yellowcircle:`●` 클릭전에 수평, 점에 선을 일치 표시가 나타나는지 확인하고 클릭합니다.
|

| :subtitle:`Step.42`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_42.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 잘라내기 버튼을 눌러줍니다.
| :bluecircle:`●` 직선 위로 남는 부분을 제거해줍니다.
| :yellowcircle:`●` 육각형의 윗 부분 2개의 선도 제거해줍니다.
| :blackcircle:`●` 닫기 버튼을 눌러 스케치를 빠져나옵니다.
|

| :subtitle:`Step.43`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_43.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 돌출 컷 버튼을 눌러줍니다.
| :bluecircle:`●` Type 항목을 클릭하여, '2개의 치수 이용'으로 변경해줍니다.
|

| :subtitle:`Step.44`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_44.jpg
   :width: 500
   :align: center

|
| :blackcircle:`●` Length에는 4mm, 아래쪽에 2nd Length는 -1mm 를 입력하고 확인을 누릅니다.
|

| :subtitle:`Step.45`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_45.png
   :width: 800
   :align: center

|
| :blackcircle:`●` 이제 평면을 사용하지 않을 것이기 때문에 잠시 숨겨둡니다.
| :orangecircle:`●` 평면을 선택해줍니다.
| :yellowcircle:`●` 보기 - 표시 여부 - 선택영역 숨기기에서 숨겨줍니다.
|

|
| 이제 모델링을 거의 다 했습니다. 만든 모양이 실제 부품과 비슷해지지 않았나요?
| 좀 더 힘내서 마무리 작업들을 진행해봅니다.
| 

| :subtitle:`Step.46`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_46.png
   :width: 800
   :align: center

|
| :bluecircle:`●` 3개의 모서리를 모따기를 하기 위해 선택해줍니다. 여러개 선택시 Ctrl 키를 눌러주세요.
| :orangecircle:`●` 모따기 버튼을 눌러줍니다.
| :yellowcircle:`●` 버튼을 누르면 에러가 나타납니다. 이 에러는 길이가 적절하지 않다는 표시입니다.
| :yellowcircle:`●` 왼쪽 창에서 크기를 0.5mm로 입력합니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
| :blackcircle:`●` 아래 에러 창은 닫아줍니다.
|

| :subtitle:`Step.47`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_EX1_47.png
   :width: 800
   :align: center

|
| :bluecircle:`●` 화면을 이동시켜, 2개의 모서리를 모따기를 하기 위해 선택해줍니다.
| :orangecircle:`●` 모따기 버튼을 눌러줍니다.
| :yellowcircle:`●` 왼쪽 창에서 크기가 1mm 인것을 확인합니다.
| :skybluecircle:`●` 확인 버튼을 눌러줍니다.
|

|
| 여기까지 완료하셨으면, 3D 펜의 부품하나를 완성하신 것입니다.
| 생각보다 어려우셨을 수도 있고, 할만했을 수도 있습니다.
| 이번 예제에서는 모델링 과정을 최대한 상세하게 설명하였습니다. 
| 다음 단계에서는 이어서 다른 부품들을 만들어 보겠습니다.
|