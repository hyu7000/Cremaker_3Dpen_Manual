온도 측정하기
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

| 온도를 측정하는 방법은 온도 센서를 이용하는 것입니다.
| 3D 펜에 사용되는 온도 센서는 저항입니다. 정확히는 :blackbold:`온도가 변하면 저항값이 변하는 저항` 입니다.
| :blackbold:`센서의 변하는 저항값을 측정하고, 이를 통해 온도를 추측 되도록` 구현하는 것이 목표입니다.
|
| 아두이노는 아날로그 핀을 입력핀으로 설정하면, 현재 핀의 전압을 측정할 수 있습니다.
|

.. image:: ../../images/Lv3/Chapter_9/Step2_0.jpg
   :width: 600
   :align: center

|
| 구조가 상당히 복잡합니다. 노즐 온도센서는 노즐의 가운데 2개 핀입니다. 하나는 GND에 연결되어 있습니다. 다른 하나는 5V에 연결된 저항과 함께 A0에 연결되어 있습니다.
| 열선은 모스펫이라는 부품에 의해 연결되어 있습니다. 이 모스펫 부품의 역할이 있습니다. 트랜지스터와 비슷하지만 다른 부품이라 한번 살펴봅니다.
| 

.. image:: ../../images/Lv3/Chapter_9/Step2_1.jpg
   :width: 600
   :align: center

|
| 아두이노 디지털핀에는 기본적으로 출력할 수 있는 전압이 5V이며, 전류는 0.5A 입니다.
| 그리고 노즐 열선의 저항은 약 2.3 ~ 4.0 Ω 범위에 있고, 계산상 대략 3 Ω 이라고 가정합니다.
| 그렇다면, 노즐에 5V 전압이 연결될 때 필요한 전류를 계산할 수 있습니다.
|

.. math::

    I = V/R, 5/3 = 1.66A

|
| 단순 계산만으로도 노즐을 예열하려면, 1.66A가 필요합니다. 디지털 핀의 전류로는 부족합니다. 따라서 외부 전원을 빌려오게 됩니다. 이 외부전원은 디지털핀 처럼 껏다 켰다 신호를 주는 것처럼 작동하지 않기 때문에, 신호는 디지털 핀이 전달하고, 외부 전원으로 노즐에게 충분한 전류를 공급해주는 역할을 해주는 것이 모스펫입니다.
| 
| 이제 온도센서에 연결된 아날로그 A0 핀의 신호 값이 어느 정도인지 확인해보겠습니다. 
|

.. image:: ../../images/Lv2/Chapter_9/Step2_2.jpg
   :width: 600
   :align: center

|
| 현재 아날로그 핀의 전압 값을 읽어 올 수 있는 함수가 analogRead 입니다. 함수의 자료형이 int임으로 반환값이 정수입니다. 0V는 0을 반환하고, 5V는 1023을 반환합니다. 2.5V 라면 511을 반환합니다.
| ※함수의 자료형이 뭔지 기억이 안난다면, :ref:`여기 <targetL3C6S7_2_2 to paragraph>` 로 이동하세요.

|
| 온도센서가 A0에 연결되어 있음으로, 아날로그 A0 핀의 전압값을 읽어오고, 시리얼 모니터에 표시되도록 다음과 같은 코드를 작성할 수 있습니다.

.. code-block:: c++
    :emphasize-lines: 3, 8
    :linenos:

    void setup() {
        // put your setup code here, to run once:
        Serial.begin(9600);
    }

    void loop() {
        // put your main code here, to run repeatedly:
        Serial.println(analogRead(A0));
    }

|
| 작성된 코드를 업로드하고, 시리얼 모니터를 실행합니다.
|
| [시리얼 통신 사진]
|
| 보통 1023이나 1022가 많이 나타날 것입니다. 지금은 거의 5V 가까이 값을 나타내고 있습니다.
| 예열을 시작하면, 아날로그 신호 값은 아래의 온도표처럼 실제 온도에 따라 변경됩니다. (아직 예열 부분은 구현하지 않았습니다.)
|
| 먼저 온도표를 먼저 보도록 하겠습니다.

+-----------+--------------+
| 실제 온도 | 아날로그 값  |
+===========+==============+
| 10        | 1008         |
+-----------+--------------+
| 20        | 994          |
+-----------+--------------+
| 30        | 990          |
+-----------+--------------+
| 40        | 985          |
+-----------+--------------+
| 50        | 983          |
+-----------+--------------+
| 60        | 981          |
+-----------+--------------+
| 70        | 978          |
+-----------+--------------+
| 80        | 975          | 
+-----------+--------------+
| 90        | 965          |
+-----------+--------------+
| 100       | 959          |
+-----------+--------------+
| 110       | 952          |
+-----------+--------------+
| 120       | 948          |
+-----------+--------------+
| 130       | 941          |
+-----------+--------------+
| 140       | 932          |
+-----------+--------------+
| 150       | 920          |
+-----------+--------------+
| 160       | 908          |
+-----------+--------------+
| 170       | 890          |
+-----------+--------------+
| 180       | 875          |
+-----------+--------------+
| 190       | 845          |
+-----------+--------------+
| 200       | 820          |
+-----------+--------------+
| 210       | 790          |
+-----------+--------------+
| 220       | 765          |
+-----------+--------------+

| 위의 표처럼 아날로그 핀의 신호 값이 981 이라면 실제 온도는 60도에 가깝다고 판단할 수 있습니다. 온도가 높아 질수록 아날로그 신호 값은 계속해서 낮아집니다.
| ※ 이런 온도표의 작성은 보통 온도센서 제조사에서 하거나, 실제 측정을 하여 작성합니다.
| 
| 온도를 올려보면서 아날로그 값들을 확인해봅니다. 이전 그림에서 노즐의 열선은 디지털 9번핀에 연결되어 있음을 알 수 있습니다.
| 따라서 디지털 9번핀을 출력 설정을하고, 실제 HIGH 값을 출력하는 코드를 작성해봅니다.
|

.. code-block:: c++
    :emphasize-lines: 5, 10, 11
    :linenos:

    void setup() {
        // put your setup code here, to run once:
        Serial.begin(9600);

        pinMode(9,OUTPUT);
    }

    void loop() {
        // put your main code here, to run repeatedly:   
        digitalWrite(9, HIGH); // 예열 시작
        delay(5); // 약간의 대기시간 추가

        Serial.println(analogRead(A0));
    }

| 위의 코드처럼 작성되지만, 위의 코드는 문제가 있습니다. 온도가 계속 상승하는 것만 있기 때문에 적절한 온도일때, 예열을 중단해주어야 합니다. 
| 예열을 할때와 하지 않을 때의 아날로그 신호 값이 약간의 차이가 있습니다. 그래서 예열을 하지 않을 때 analogRead 로 신호 값을 조정합니다. 이 순서는 다음 코드 작성함에 있어서 중요합니다.
| 
| 예열 On 일때와 Off 일때의 차이는 전원의 저항 때문입니다. 먼저 디지털 9번핀(D9)가 LOW 상태인 경우를 살펴 보겠습니다.
|

 .. image:: ../../images/Lv3/Chapter_9/Step2_1_2.jpg
   :width: 700
   :align: center

|
| 위는 온도 센서와 노즐 열선을 개략도로 나타낸 것입니다. 위 온도 센서는 저항으로 온도에 따라 저항값이 바뀌기 때문에 모양이 살짝 다릅니다. 이 저항에 걸리는 전압이 아날로그 신호 값으로 인식됩니다.
| 아래쪽 D,S,G 라고 표시된 것은 모스펫 입니다. 디지털 9번핀(D9)에서 G로 신호를 주게 되면, D에서 S로 전기가 흐르게 됩니다.
| 
| 디지털 9번핀(D9)이 LOW이라면, 회로는 직렬연결이 되게 됩니다. 전원 저항, 100옴 저항, 온도센서 저항으로 총 3개의 저항이 직렬 연결되어 있습니다. 그리고 저항이 높다보니, 전류는 아주 약하게 흐릅니다.
| 전류가 약하기 때문에 전원의 저항에도 큰 전압이 걸리지 않습니다.
| 아래쪽 D9에서도 약간의 전류가 나옵니다. 이 전류는 모스펫의 G 로 가지 않도록 배치해둔 100k 저항쪽으로 흐릅니다.
|

 .. image:: ../../images/Lv3/Chapter_9/Step2_1_3.jpg
   :width: 700
   :align: center

|
| 반면 디지털 9번핀(D9)가 HIGH 라면, 아래쪽에는 저항이 작기 때문에 큰 전류가 흐르게 됩니다. 자연스럽게, 전원의 저항에도 큰 전류가 흐르게 되고, 이로써 약간의 전압이 낮아지게 됩니다. 따라서 온도 센서에도 영향을 주게 됩니다.
| 따라서 아날로그 A0번핀을 측정할 경우에는 디지털 9번핀(D9)를 HIGH 한 상태에서 체크하도록 통일해야 정확도가 높아집니다.
| 
| 온도가 60도 이상올라갈 경우 예열을 중단하는 코드를 작성하면 다음과 같이 작성될 수 있습니다.

.. _targetL3C9S2_2_5:

.. code-block:: c++
    :linenos:

    int tempValueA0 = 0; // A0 신호 값 저장용
    bool isHeating = false; // 예열 상태를 확인하는 확인하는 bool 변수

    void setup() {
        // put your setup code here, to run once:
        Serial.begin(9600);

        pinMode(9,OUTPUT);
    }

    void loop() {
        // put your main code here, to run repeatedly: 
        digitalWrite(9, HIGH); // 예열 시작
        delay(1);
        tempValueA0 = analogRead(A0); // 아날로그 신호 값을 tempValueA0 저장
        if(!isHeating)
        {
            digitalWrite(9, LOW); // 예열 종료
        }

        Serial.println(tempValueA0);        

        if(tempValueA0 < 981)
        {
            digitalWrite(9, LOW); // 예열 종료
            delay(5); // 약간의 대기시간 추가

            isHeating = false;
        }
        else
        {
            digitalWrite(9, HIGH); // 예열 시작
            delay(5); // 약간의 대기시간 추가

            isHeating = true;
        }

    }

| 먼저 예열이 시작된 상태로 아날로그 신호 값을 읽습니다. (12줄)
| 예열되고 있지 않은 상태라면, 아날로그 신호 값을 조정합니다. 디지털 9번핀이 HIGH인 상태와 LOW 상태에 따라 아날로그 A0 의 신호값이 약간의 오차가 있기 때문에 이 오차를 보정하기 위해서 아날로그 A0 신호를 읽기전에 디지털 9번핀을 HIGH 로 출력해줍니다.
| 읽어온 아날로그 신호값이 981일때 온도가 60도 임으로 981값보다 아래면, 예열을 중단하고, 981값보다 크면 예열을 시작하는 코드를 추가하였습니다. 
| 
| 업로드를 하고, 신호 값을 확인 하기 위해, 시리얼 모니터를 켜줍니다.
|

 .. image:: ../../images/Lv2/Chapter_9/Step2_3.png
   :width: 500
   :align: center

| 
| 온도가 60도를 유지하는 코드를 작성하였습니다. 이제는 온도표를 보고 현재온도를 정확하게 측정하는 방법에 대해서 알아보려 합니다.
| 만일 아날로그 신호 값이 962 로 읽힌다면, 온도는 어떻게 표시해야 할까요?
|

 .. image:: ../../images/Lv3/Chapter_9/Step2_2.jpg
   :width: 500
   :align: center

|
| 위 그림과 같이 2개의 포인트를 직선을 그리고, 이 직선을 기준으로 962 신호값의 온도를 추측하는 것이 :blackbold:`선형보간법` 이라고 합니다. 가장 간단한 방법으로는 직선의 방정식을 찾고, 해당 방정식을 기준으로 값을 도출해 낼 수도 있습니다.
|

 .. image:: ../../images/Lv3/Chapter_9/Step2_3.jpg
   :width: 500
   :align: center

|
| 간단하게 그림으로 설명드리면, 왼쪽의 값은 965, 962, 959로 모두 나와 있고, 각각의 값들의 차이는 3이며, 비율은 1:1이 됩니다. 이 비율을 적용하여, 값에도 90도와 100도를 1:1 비율로 나누는 지점은 어디일까요? 95도가 됩니다.
| 3D 펜이나 다른 온도가 관련된 제품들도 대부분 선형 보간법을 많이 사용합니다. 다만 10도 단위가 아니라 5도 단위일 수 도 있으며, 제품에 따라 차이가 있습니다.
|

 .. image:: ../../images/Lv3/Chapter_9/Step2_4.jpg
   :width: 500
   :align: center

|
| 코드로 사용하기 위해서, 수식으로 한번 나타내 보았습니다. 비율이 같다는 조건으로 계산을 하게되고, 이로 y값을 계산할 수 있습니다.
| 이제 온도는 60도를 유지하되, 선형보간법 방식을 이용하여 온도 값을 계산하는 코드를 작성해보겠습니다.
| 또한 :ref:`이전 코드 <targetL3C9S2_2_5>` 에서 온도를 체크하는 부분을 함수로 분리하겠습니다.

.. code-block:: c++
    :linenos:

    int tempValueA0 = 0; // A0 신호 값 저장용
    int curTemp = 0; // 온도 값
    bool isHeating = false; // 예열 상태를 확인하는 확인하는 bool 변수

    int temptable[23][2] = 
    {
        {1023,0},
        {1008,10},
        {994,20},
        {990,30},
        {985,40},
        {983,50},
        {981,60},
        {978,70},
        {975,80},
        {965,90},
        {959,100},
        {952,110},
        {948,120},
        {941,130},
        {932,140},
        {920,150},
        {908,160},
        {890,170},
        {875,180},
        {845,190},
        {820,200},
        {790,210},
        {765,220}
    }; // 온도테이블

    void setup() {
        // put your setup code here, to run once:
        Serial.begin(9600);

        pinMode(9,OUTPUT);
    }

    // 신호 값을 보정하여 온도 값을 추측해내는 계산 함수
    int tempCali(int valueA0)
    {
        float ratioTemp;

        for(int i = 0; i<23; i++)
        {
            if(temptable[i][0] < valueA0) 
            {
                ratioTemp = (valueA0 - temptable[i][0])/(temptable[i-1][0] - temptable[i][0]);
            }

            return temptable[i][1] - ratioTemp*(temptable[i][1] - temptable[i-1][1]);
        }
    }

    // 아날로그 A0 핀의 신호 값을 디지털 9번핀(열선)이 HIGH인 상태에서 체크하도록 하는 함수
    void checkA0()
    {
        digitalWrite(9, HIGH); // 예열 시작
        delay(1);
        tempValueA0 = analogRead(A0); // 아날로그 신호 값을 tempValueA0 저장
        if(!isHeating)
        {
            digitalWrite(9, LOW); // 예열 종료
        }
    }

    void loop() {
        // put your main code here, to run repeatedly: 
        checkA0() // 아날로그 A0의 신호 값을 가져오는 함수

        curTemp = tempCali(tempValueA0); // 온도 보상 함수 호출

        Serial.println(curTemp);        

        if(curTemp > 60)
        {
            digitalWrite(9, LOW); // 예열 종료
            delay(5); // 약간의 대기시간 추가

            isHeating = false;
        }
        else
        {
            digitalWrite(9, HIGH); // 예열 시작
            delay(5); // 약간의 대기시간 추가

            isHeating = true;
        }

    }

|
| tempCali 함수는 조정된 아날로그 신호 값을 받고, 이를 좀 더 정확한 온도를 표시하게 합니다.
| 이후 시리얼 모니터를 열고, 출력되는 값을 확인하면, 좀 더 정확한 온드를 볼 수 있습니다.
| 