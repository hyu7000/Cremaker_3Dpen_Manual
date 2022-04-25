모터 작동시키기
+++++++++++++++++++

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

| 3D 펜에서 재료를 밀어내는 역할을 하는 모터를 작동시켜 보려합니다.
| 이전에 배운 버튼을 이용해서, :blackbold:`각 버튼이 눌렸을 때, 모터가 회전되도록` 구현하는 것이 목표입니다.
|

| [실제 사진 추가]
| 

|
| 모터가 돌아가는 것은 아래쪽에서 확인할 수 있습니다.
| 이 모터는 DC 모터로 드라이버에 의해 제어됩니다.
|

.. image:: ../images/Lv2/Chapter_8/Step1_1.jpg
   :width: 600
   :align: center

|
| 그림이 약간 복잡합니다. L293D는 모터의 속도와 방향을 제어하게 해주는 모터 드라이버입니다. 이 부품이 어떤 부품인지 이해하기에는 난이도가 있으니 필요한 부분만 살펴보도록 하겠습니다.
| 모터 활성화, 모터 방향, 모터 속도에 관한 부분만 확인하면 됩니다.
| 그림에도 표시되어 있듯이 각각 디지털 핀 5,6,10 입니다.
|

.. image:: ../images/Lv2/Chapter_8/Step1_2.jpg
   :width: 600
   :align: center

| 
| 모터를 L293D로 작동시키려면, 먼저 모터 활성화가 되어야 하고, 방향을 정하고, 모터의 속도를 정해주어야 합니다.
| 모터 활성화가 되어 있지 않고, 되어 있더라도 모터의 속도가 0이면, 모터는 움직이지 않습니다.
| 모터를 작동시키려면 먼저 3개의 핀을 모두 OUTPUT(출력)으로 설정해주어야 합니다.
| 
| 이전 단계에 작성한 코드를 그대로 사용해서, 추가로 코드를 작성해봅니다.


.. code-block:: c++
    :emphasize-lines: 6,7,8,12

    void setup() {
        // put your setup code here, to run once:
        pinMode(8,INPUT_PULLUP);
        pinMode(7,INPUT_PULLUP);

        pinMode(5,OUTPUT);
        pinMode(6,OUTPUT);
        pinMode(10,OUTPUT);

        pinMode(13,OUTPUT);

        digitalWrite(5, HIGH);
    }

    void loop() {
        // put your main code here, to run repeatedly:
        if(digitalRead(8)==LOW)
        {
            digitalWrite(13,HIGH); //LED ON
        }
        else if(digitalRead(7)==LOW)
        {
            digitalWrite(13,LOW); //LED OFF
        }
    }

| pinMode는 처음 한번만 호출되면 됨으로 setup에 작성합니다. 5,6,10 모두 OUTPUT으로 설정합니다.
| setup의 digitalWrite(5,HIGH)는 모터 활성화 핀의 출력을 HIGH로 설정합니다. 
| 전원이 on 되면 모터는 항상 활성화가 되어 있게 됩니다. (모터 활성화 핀을 ROW로 하는 코드가 없기 때문)
|
| 이어서 모터의 방향보다 모터의 속도 먼저 설정해보도록 코드를 작성해봅니다.

.. code-block:: c++
    :emphasize-lines: 20, 25

    void setup() {
        // put your setup code here, to run once:
        pinMode(8,INPUT_PULLUP);
        pinMode(7,INPUT_PULLUP);

        pinMode(5,OUTPUT);
        pinMode(6,OUTPUT);
        pinMode(10,OUTPUT);

        pinMode(13,OUTPUT);

        digitalWrite(5, HIGH);
    }

    void loop() {
        // put your main code here, to run repeatedly:
        if(digitalRead(8)==LOW)
        {
            digitalWrite(13,HIGH); //LED ON
            analogWrite(10,100);            
        }
        else if(digitalRead(7)==LOW)
        {
            digitalWrite(13,LOW); //LED OFF
            analogWrite(10,0);
        }
    }

| analogWrite 라는 함수가 처음 등장했습니다. 분명 디지털 10핀인데 아날로그 관련된 함수를 사용합니다.
| 이해가 안가는 부분이 생겼습니다. 여기에서 analogWrite 함수는 디지털 핀중에 PWM이라는 핀이 있습니다.
| 우리가 사용하는 아두이노 나노 보드에는 3, 5, 6, 9, 10, 11의 디지털핀이 해당됩니다.
|

.. image:: ../images/Lv2/Chapter_8/Step1_3.jpg
   :width: 600
   :align: center

|
| 일반 디지털 핀의 제어는 위와 같이 :blackbold:`5V를 쭉 출력하여 모터속도가 최대로 유지`되는 반면, PWM은 짧은 시간에 5v로 이동했다가 0v로 이동을 반복함으로써 전류를 적게 보내주고, :blackbold:`모터속도가 줄어들면서 제어` 할 수있습니다.
|
| 즉, 일반 디지털 핀은 모터를 최대속도이거나 정지된 상태만 제어할 수 있다면, PWM 제어는 모터를 중간속도로도 설정할 할 수 있습니다.
| 그 PWM로 제어하게 하는 함수가 analogWrite 입니다.

.. image:: ../images/Lv2/Chapter_8/Step1_4.jpg
   :width: 600
   :align: center

|
| analogWrite 에는 PWM 이 지원되는 디지털핀만 사용이 가능합니다. PWM 값은 보통 0은 최소로 0V, LOW와 같고, 255는 최대로 5V, HIGH와 같습니다.

|
| 업로드를 진행하고, 동작이 되는지 확인합니다.
| ※ 업로드 버튼을 찾지 못하였다면 :ref:`여기 <targetL2C7S1_4>` 로 이동합니다.
|
| 정상적으로 작동된다면, 모터 방향도 한번 설정해보겠습니다.
| 모터 방향은 digitalWrite를 이용하여, 모터 방향핀을 HIGH, LOW 로 바꿔줄 때마다 방향이 바뀌게 됩니다.
|
| 1. A버튼을 눌렀을 경우 시계방향 회전
| 2. B버튼을 눌렀을 경우 반시계방향 회전
| 3. A,B 버튼 을 누르지 않았을 경우에는 모터 정지
| ※ 정지를 하려면 디지털 6번핀은 LOW가 되어야 하고, 10번핀에는 PWM 값이 0이 입력되야 합니다.
|
| 위 기능이 되도록 아래 코드를 보지 않고서 코드를 작성해봅니다.
|
| 작성을 다하고, 아래 코드랑 비교해봅니다.

.. toggle::

    .. code-block:: c++
        :emphasize-lines: 20, 26

        void setup() {
            // put your setup code here, to run once:
            pinMode(8,INPUT_PULLUP);
            pinMode(7,INPUT_PULLUP);

            pinMode(5,OUTPUT);
            pinMode(6,OUTPUT);
            pinMode(10,OUTPUT);

            pinMode(13,OUTPUT);

            digitalWrite(5, HIGH);
        }

        void loop() {
            // put your main code here, to run repeatedly:
            if(digitalRead(8)==LOW)
            {
                digitalWrite(13,HIGH); //LED ON
                digitalWrite(6,HIGH);
                analogWrite(10,100);            
            }
            else if(digitalRead(7)==LOW)
            {
                digitalWrite(13,LOW); //LED OFF
                digitalWrite(6,LOW);
                analogWrite(10,100);
            }
            else
            {
                digitalWrite(6,LOW);
                analogWrite(10,0);
            }            
        }
    
|