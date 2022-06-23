온도 설정하기
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

| 온도를 측정하고 유지하는 것까지 알았습니다. 이제는 온도를 직접 설정하는 방법에 대해서 알아보겠습니다.
| 원하는 온도를 세세하게 설정하기엔 복잡함이 있음으로, :blackbold:`미리 재료에 적절한 온도 값을 저장하고, 그 값을 불러내어 목표온도로 설정하는 방식을 구현` 해보는 것이 목표입니다.
|

| 재료에 맞는 온도 값을 미리 배열로 저장하고 불러오기 위해, 변수와 배열을 :hoverxref:`선언 <hoverxref:declaration>` 합니다.

.. code-block:: c++
    :linenos:

    int curTemp        = 0; // 계산된 온도
    int targetTemp     = 0; // 설정 온도
    int presetIndex    = 0; // 저장된 설정 온도의 현재 순번

                      // 기본, PCL, PLA
    int presetTemp[3] = { 0,  60,  200 };

|
| 배열과 함께 변수가 2개 추가되었습니다. 먼저 현재온도가 아닌 목표온도(설정온도)가 무슨 값을 가지고 있는지 저장하고, 알기 위해 targetTemp 변수를 만들었습니다. 이어서 배열은 길이가 3개 입니다. 각각 0도 60도 200도를 설정할 수 있도록 3개의 항목이 배열에 저장되어 있습니다.
| 이 배열 현재의 위치를 가르키고 있는 숫자를 인덱스(index)라고 합니다. 인덱스의 뜻은 지표, 색인, 지수등을 뜻합니다. 프로그래밍에서는 배열[인덱스]와 같은 형태로 사용됩니다. 인덱스 변수와 배열은 코드로는 다음과 같습니다.

.. code-block:: c++
    :linenos:

    targetTemp = presetTemp[presetIndex];

|
| presetTemp의 배열의 presetIndex 의 위치의 값을 설정온도(targetTemp)로 저장하겠다는 표시입니다.
| 여기에서 버튼을 누를 때마다 presetIndex가 1씩 증가(혹은 감소)하면, targetTemp 의 값도 계속해서 변경되어질 것입니다.
| 
| 버튼을 누를 때마다 설정온도가 변경되도록 전체 코드를 작성해봅니다. 그리고 아래 코드와 비교해 봅니다.

.. toggle::

    .. code-block:: c++
        :linenos:

        int curTemp = 0;
        int targetTemp = 0;
        int presetIndex = 0;

                         // 기본, PCL, PLA
        int presetTemp[3] = { 0,  60,  200 };

        int temptable[23][2] = 
        {
            {1023,0},
            {1022,10},
            {1020,20},
            {1016,30},
            {1011,40},
            {1009,50},
            {1006,60},
            {1004,70},
            {1000,80},
            {990,90},
            {983,100},
            {976,110},
            {972,120},
            {964,130},
            {955,140},
            {942,150},
            {929,160},
            {910,170},
            {895,180},
            {864,190},
            {839,200},
            {800,210},
            {744,220}
        }; // 온도테이블

        void setup() {
            // put your setup code here, to run once:
            Serial.begin(9600);

            pinMode(11,INPUT_PULLUP);
            pinMode(12,INPUT_PULLUP);

            pinMode(9,OUTPUT);
        }

        // 신호 값을 보정하여 온도 값을 추측해내는 계산 함수
        int tempCali(int valueA0)
        {
            float ratioTemp;

            for(int i = 0; i<23; i++)
            {
                if(temptable[i][0] <= valueA0) 
                {
                    ratioTemp = ((float)valueA0 - temptable[i][0])/(temptable[i-1][0] - temptable[i][0]);

                    return temptable[i][1] - ratioTemp*(temptable[i][1] - temptable[i-1][1]);
                }

            }
        }

        void loop() {
            // put your main code here, to run repeatedly: 

            curTemp = tempCali(analogRead(A0)); // 온도 보상 함수 호출
  
            Serial.print(", 현재 온도 값 : ");
            Serial.print(curTemp);   
            Serial.print(", 설정 온도 값 : ");
            Serial.println(targetTemp);

            if(curTemp > targetTemp)
            {
                digitalWrite(9, LOW); // 예열 종료
                delay(5); // 약간의 대기시간 추가
            }
            else
            {
                digitalWrite(9, HIGH); // 예열 시작
                delay(5); // 약간의 대기시간 추가
            }

            if(digitalRead(11)==LOW)
            {
                presetIndex++;
                targetTemp = presetTemp[presetIndex];

                if(presetIndex>2)
                {
                  presetIndex = 0;
                }
                delay(100);
            }
            else if(digitalRead(12)==LOW)
            {
                presetIndex--;
                targetTemp = presetTemp[presetIndex];

                if(presetIndex<0)
                {
                  presetIndex = 2;
                }
                delay(100);
            }

        }

        | 업로드 후 시리얼 모니터로 값을 확인해보세요.
        | ?줄의 (float)valueA0는 int 정수형 변수인 valueA0를 float 실수형 값으로 읽겠다는 뜻입니다. 이 부분이 없으면, 실수 값으로 계산되지 않습니다.