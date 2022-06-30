스케치 구속 기능
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

|
| 스케치에는 만들어진 선들을 각 길이, 위치에 맞게 고정시키는 기능이 있습니다. 이를 모델링에서는 구속(Constraint)이라 합니다.
|
| 이 구속조건은 그려진 선들을 좀 더 정교하게 다듬어 줍니다.
| 예시들을 보면서 어떻게 사용되는지 알아봅니다.
|

| :subtitle:`점 일치`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_1.png
   :width: 800
   :align: center

| 
| 2개의 점을 일치시켜주는 기능입니다. 떨어져 있거나, 서로 붙어 있지 않은 점을 연결시켜줄 때 사용합니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_2.gif
   :width: 800
   :align: center

|
| 적용 순서로는 점 일치 버튼을 누르고, 점 2개를 순서대로 클릭해주면 됩니다. 합쳐지는 곳은 첫번째 점의 위치입니다.
|

| :subtitle:`점을 선에 일치`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_3.png
   :width: 800
   :align: center

|
| 1개의 점을 선에 일치시켜주는 기능입니다. 해당 선의 위가 아닌 곳에도 연결되기도 합니다.
| 

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_4.gif
   :width: 800
   :align: center

|
| 점과 선을 일치시키고, 점을 드래그하여 이동시키면, 그려진 선의 연장된 부분에도 이동됨을 알 수 있습니다.
| 

| :subtitle:`수직, 수평`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_5.png
   :width: 800
   :align: center

| 
| 기울어진 선을 수평, 수직으로 고정시켜주는 기능입니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_6.gif
   :width: 800
   :align: center

|
| 버튼 클릭 후 기울어진 선을 클릭하면, 수평과 수직을 만들어줍니다.
|

| :subtitle:`평행, 수직`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_7.png
   :width: 800
   :align: center

|
| 2개의 선을 평행하게 해주거나, 수직되게 해줍니다.
| 수직 기능을 사용할 때에는, 2개의 선이 항상 만나게 해주진 않습니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_8.gif
   :width: 800
   :align: center

|
| 평행(혹은 수직) 버튼을 클릭하고, 이어서 선 2개를 선택하면, 선의 위치가 변경됩니다.
| 

| :subtitle:`탄젠트(접함)`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_9.png
   :width: 800
   :align: center

|
| 버튼의 이름은 탄젠트라고 되어 있습니다. 원과 선의 접하게 해주는 기능인데, 번역이 완벽하지 않아 보입니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_10.gif
   :width: 800
   :align: center

|
| 탄젠트 버튼을 클릭하고, 원과 선을 선택해주면, 서로 접하게 됩니다.
| 

| :subtitle:`동일`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_11.png
   :width: 800
   :align: center

|
| 동일 기능은 2개의 직선, 원의 치수를 같게 해줍니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_12.gif
   :width: 800
   :align: center

|
| 동일 버튼을 누르고 선 2개를 선택하거나, 원 2개를 선택하면, 첫번째 선택한 객체의 치수로 같게 변경됩니다.
|

| :subtitle:`대칭`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_13.png
   :width: 800
   :align: center

|
| 대칭 기능은 특정 선을 기준으로 다른 점들을 대칭으로 구속해 주는 기능입니다.
| 

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_14.gif
   :width: 800
   :align: center

|
| 대칭 버튼을 누르고, 점 2개와 선 1개를 연속으로 클릭하면, 선을 기준으로 2개의 점이 대칭되게 됩니다.
|

| :subtitle:`Constrain block`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_15.png
   :width: 800
   :align: center

|
| constarin block은 해당 선, 도형을 움직이지 못하게 고정시켜 줍니다. 
| 번역이 덜된 부분으로 :blackbold:`위치 고정` 정도로 이해해주시면 됩니다.
| 

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_16.gif
   :width: 800
   :align: center

|
| constarin block을 적용하면, 선의 색상이 바뀐 것을 확인할 수 있습니다.
|

| :subtitle:`Constrain horizontal(vertical) distance`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_17.png
   :width: 800
   :align: center

|
| 이 부분도 마찬가지로 번역이 덜 되어 있습니다.
| 수평, 수직거리 설정으로 이해해주시면 됩니다.
| 수평, 수직 거리를 설정할 수 있는 기능으로 구속 기능 중 하나입니다.
| 

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_18.gif
   :width: 800
   :align: center

|
| 수직 수평 거리는 선과 점과 점 모두 가능합니다. 
| 선이나 점2개를 클릭하면, 길이 입력창이 나오며, 여기에 원하는 치수를 입력하면, 해당 크기만큼으로 변경됩니다.
|

| :subtitle:`Constrain arc or circle`

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_19.png
   :width: 800
   :align: center

|
| 이 기능의 번역은 호, 원의 지름으로 이해해주시면 됩니다.
| 호와 원의 지름을 설정해줄 수 있습니다.
|

.. image:: ../../images/Lv3/Chapter_Modeling/FreeCad_Constraint_20.gif
   :width: 800
   :align: center

|
| Constrain arc or circle 기능을 사용하여, 그려진 원의 지름을 설정해줍니다.
| 