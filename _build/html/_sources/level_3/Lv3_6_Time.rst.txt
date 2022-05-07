delay와 시간
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

| 기본 예제로써 아두이노를 한번 쯤 해보셨다면, Blink 예제가 있습니다.
| 여기에는 delay 함수가 있습니다.

.. code-block:: c++

   void loop() {
      digitalWrite(LED_BUILTIN, HIGH);   
      delay(1000);                       
      digitalWrite(LED_BUILTIN, LOW);    
      delay(1000);                       
   }

| 이 delay 함수는 코드가 복잡해질 수록 잘 사용하지 않습니다. 혹시 이유를 추측해보실까요?
| delay 함수의 기능이 매개변수로 입력된 시간만큼 기다리는 것인데, 문제는 :blackbold:`기다린다` 에 있습니다.
|
| 문제가 되는 예시를 알아보기 위해서, LED 가 2개 연결된 아두이노가 있다고 가정합니다.
| 첫 번째 LED는 3초마다 꺼지고, 켜지고를 반복하고, 두 번째 LED는 2초 마다 꺼지고, 켜지고를 반복하게 하려면, 어떻게 해야할까요?
|

.. image:: ../images/Lv3/Chapter_6/Step1_1.jpg
   :width: 600
   :align: center

| 
| 묘책이 떠오르셨나요? 아마 변수를 사용하서 어찌 저찌 할 수는 있습니다.
| 그렇다면, LED를 10개로 늘리고, 각기 다른 시간마다 On,Off가 반복 되게 하는 것은 좀 어렵겠죠?
| 이렇듯 delay를 사용해서 제어하는 것보다 좋은 방법이 있습니다.
|
| :subtitlesmall:`millis()`
| millis 함수를 이용하는 것입니다. 이 함수는 아두이노가 켜진 뒤부터 얼마나 시간이 지났는지 밀리 초(ms) 단위로 알 수 있습니다.

.. code-block:: c++
   :linenos:
   
   long time;

   void setup()
   {
      Serial.begin(9600); // 시리얼 통신 시작
   }

   void loop()
   {
      time = millis(); // millis 함수의 반환 값을 time에 저장

      time = time/1000; // 밀리초(ms) 단위를 초 단위로 변경

      Serial.println(time); // 시리얼 모니터에 time 값 출력
   }

|
| 켜지고 나서 시간이 계속해서 지나감을 알 수 있습니다.
| 이 함수를 사용하면, 좀 더 효율적으로 여러 작업을 진행할 수 있습니다.
|

| millis 함수를 이용해서
| 2개의 LED가 2초, 3초마다 반복해서 On, Off 되는 코드를 작성해봅니다.
| ※ LED는 디지털 12번핀, 13번핀에 연결되어 있다고 가정합니다.
|
| 작성하고 업로드 후, 동작을 확인합니다. 그리고 아래 코드랑 비교해봅니다.

.. toggle::

   .. code-block:: c++
      :linenos:   

      long timeLED1, timeLED2;
      bool isOnLED1, isOnLED2;

      void setup()
      {
         // 핀 모드 설정
         pinMode(12, OUTPUT);
         pinMode(13, OUTPUT);

         // 기준 시간 설정
         timeLED1 = millis();
         timeLED2 = millis(); 

         // LED 상태를 bool 변수에 저장
         isOnLED1 = isOnLED2 = false;
      }

      void loop()
      {
         // 기준 시간과 현재시간의 차이가 2초 이상인지 확인
         if(millis()-timeLED1 > 2000)
         {
            // LED 상태에 따라 On Off 실행
            if(isOnLED1)
            {
               digitalWrite(12,LOW);
               isOnLED1 = false
            }
            else
            {
               digitalWrite(12,HIGH);
               isOnLED1 = true;
            }

            // 기준시간에 현재시간을 저장
            timeLED1 = millis();
         }

         // 기준 시간과 현재시간의 차이가 3초 이상인지 확인
         if(millis()-timeLED2 > 3000)
         {
            // LED 상태에 따라 On Off 실행
            if(isOnLED2)
            {
               digitalWrite(13,LOW);
               isOnLED2 = false;
            }
            else
            {
               digitalWrite(13,HIGH);
               isOnLED2 = true;
            }

            // 기준시간에 현재시간을 저장
            timeLED2 = millis();
         }
      }

|
| millis()는 전원이 켜진 뒤 부터 계속해서 값이 증가합니다. 그러므로 long 변수를 만들고, 조건이 될 때마다 현재 시간을 저장해줘야 합니다.
| 이와 같은 코드로 LED가 많아질 수록 복잡하지 않게 코드를 작성할 수 있습니다.
| 

| 이런 형태로 아두이노는 2가지 이상의 작업을 수행하는 것처럼 보이게 할 수 있습니다.
| 실제 아두이노는 계산, 연산하는 두뇌에 해당되는 부품(프로세스, CPU에 해당)이 1개 밖에 없기 때문에 한번에 한가지 작업만 실행할 수 있습니다.
| 따라서 한번에 여러가지 작업을 하는 것처럼 보일려면, 이런 시간관련 함수를 사용해야 합니다.
|

.. | 만들어볼 3D 펜도 해야할 작업이 있습니다.
.. |
.. | 1. 버튼이 눌러져 있는지
.. | 2. 온도는 얼마인지
.. | 3. 예열On, Off
.. | 4. 모터 작동
.. |
.. | 이와 같은 것들을 동시에 처리하는 것 처럼 되기 위해서 다음 과정을 알아봅니다.