Step.3 예열하기
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

| Step2에 이어서 예열을 시작하고 온도가 60도가 되면 멈추는 블록을 만들어 보겠습니다.
|

| 열선을 가열을 하는 방법은 간단합니다. 열선은 디지털 9번 핀에 연결되어 있습니다. 이 디지털 9번 핀에 켜주기만 하면 됩니다.
|

.. image:: ../../images/Lv1/Chapter_6/Step3_1.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 하드웨어 블록을 클릭합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_2.png
   :width: 800
   :align: center

|
| :orangecircle:`●` :blackbold:`디지털 0번 핀 켜기` 블록을 :blackbold:`~ 아니면 ~` 부분으로 이동시켜 줍니다.
| :yellowcircle:`●` :blackbold:`디지털 0번 핀 켜기` 블록의 숫자를 9번으로 변경시켜 줍니다.
|
|

| 이제 블록 순서를 다시 살펴보면, 신호값이 978~984 사이(=온도값이 60이라면)가 아니라면, 디지털 9번 핀은 열선에 연결되어 있기 때문에 핀을 켜게 되면 가열이 시작됩니다. 뜨거워지겠죠. 그러면서 온도가 상승합니다.
| 상승하면서 온도가 60이 아닐 경우에는 계속해서 디지털핀을 켜게 됩니다.
| 여기서 오류가 하나 있습니다. 어떤 오류가 있을까요? 아마 발견하기 어려우실 수 있습니다.
| 온도를 상승시키는 그래프를 보면 힌트가 될 수 있습니다.
|

.. image:: ../../images/Lv1/Chapter_6/Step3_3.jpg
   :width: 600
   :align: center

|
| 대부분의 온도를 상승시키는 과정에서 설정 온도(60도)에 도달하자 마자 멈추는 과정은 드뭅니다. 그림처럼 설정온도를 넘어설 수 있습니다.(물론 정밀 조절을 하면 완화될 수 있습니다.) 이런 부분 때문에 생기는 문제 입니다.
| 우리가 신호 값 978~984 값에서 온도 값 60을 인식하고, 그외에 경우에는 계속 가열하게 하게끔 블록을 만들었습니다. 
| 하지만 984 값에 도달해서 멈추었음에도 그림 처럼 살짝 넘쳐서 978 보다 낮아진다면? (신호값이 낮아질수록 온도는 높음)
| 멈추지 않고 계속 가열하게 됩니다. 그럼 온도 60도를 유지하는 것이 아니라 계속해서 가열하게 됩니다.
|
| 그럼 신호값이 978 이하일 경우에는 가열을 멈춰야 합니다. 신호값 978 이하일 경우 디지털 9번 핀을 끄기 를 만들어 봅시다. 
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_4.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 흐름 블록으로 이동합니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_5.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`만일 참 (이)라면 ~ 아니면 ~` 블록을 이미 있던 :blackbold:`만일 참(이)라면 ~ 아니면 ~` 블록 아래쪽에 이동시켜 줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_6.png
   :width: 800
   :align: center

|
| :orangecircle:`●` 이동하고 난 뒤에는 그림처럼 :blackbold:`978 ≥ 아날로그 A0 번 센서갑` 블록에서 기호 쪽에 마우스 오른쪽 클릭합니다.
| :blackcircle:`●` 클릭을 하면 메뉴가 나오고, 여기에서 코드 복사 & 붙여넣기를 클릭합니다.
| :blackcircle:`●` 똑같은 블록이 하나 더 나오게 됩니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_7.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 복사된 블록을 아래쪽 :blackbold:`만일 참 (이)라면 ~ 아니면 ~` 블록에 이동시켜줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_8.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`만일 ~ (이)라면 ~ 아니면 ~` 블록의 아래에 있는 :blackbold:`디지털 9번 핀 켜기` 블록을 :blackbold:`만일 ~ (이) 라면` 의 아래쪽으로 이동시켜 줍니다. 
| :blackcircle:`●` 이 부분은 온도가 60도 이하일 경우(신호 값이 984 이상일 경우)에는 디지털 9번핀(가열부분)을 켜라는 명령을 줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_9.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`978 ≥ 아날로그 A0 번 센서갑` 블록의 ≥ 기호를 클릭합니다.
| :orangecircle:`●` ≤ 기호로 변경시켜 줍니다.
| :blackcircle:`●` 신호 값이 984보다 클 경우에는 온도가 60도 보다 낮기 때문에 디지털 핀을 켭니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_10.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`디지털 9번 핀 켜기` 블록을 마우스 오른쪽 클릭을 합니다.
| :orangecircle:`●` 코드 복사 & 붙여넣기 메뉴를 클릭합니다.
| :blackcircle:`●` 클릭을 하면 메뉴가 나오고, 여기에서 코드 복사 & 붙여넣기를 클릭합니다.
| :blackcircle:`●` 똑같은 블록이 하나 더 나오게 됩니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_11.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` 복사된 블록을 :blackbold:`~아니면~` 의 아래쪽에 이동시켜줍니다.
|
|

.. image:: ../../images/Lv1/Chapter_6/Step3_12.png
   :width: 800
   :align: center

|
| :yellowcircle:`●` :blackbold:`디지털 9번 핀 켜기` 블록의 켜기 부분을 클릭하여 끄기로 변경해줍니다.
|
|

|
| 블록을 완성하느라 수고하셨습니다. 블록을 다시 살펴보면, 신호 값(아날로그 A0 센서 값)이 978~984 사이에 있으면 온도 값을 60도로 저장합니다.
| 이후 신호 값이 984 이상이면(=온도가 60도 이하라면) 디지털 9번 핀을 켜서 온도를 올려주고, 아니라면 디지털 9번 핀을 끄게 하여 온도를 낮춰줍니다.
| 여기까지가 실제 온도측정하고 온도에 따라 다른 작동을 하도록 블록을 만들었습니다.
| 
| 시작하기 버튼을 누르면 실제로 온도가 올라가기 시작합니다. 고온으로 올라가면, 뜨겁기 때문에 주의하시기 바랍니다.

|
| 이제 모터 작동을 했던 것과, 온도를 올리는 것과 함께 사용해 볼 것입니다.
| 현재 작성된 코드를 지우지 않고, 다음 과정을 넘어갑니다.