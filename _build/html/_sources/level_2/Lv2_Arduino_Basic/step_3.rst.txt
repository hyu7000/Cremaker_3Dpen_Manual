연산자
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

| 두개 이상의 값들을 어떤 연산을 처리해주는 것이 연산자입니다.
| 연산자의 종류는 여러분들이 잘알고 있는  +, - , x, / 와 같은 것들이 있습니다.
|
| 레벨2에서는 모든 연산자를 살펴보기보다, 필요한 연산자들만 먼저 알아보겠습니다.

.. list-table:: :subtitlesmall:`연산자 종류`
    :widths: 5 5 5 5
    :header-rows: 1

    * - 기호
      - 의미
      - 사용 예
      - a에 저장되는 값
    * - =
      - 오른쪽 값을 왼쪽으로 저장
      - a = 10;
      - 10
    * - `+`
      - 왼쪽과 오른쪽 값을 더함
      - a = 10 + 10;
      - 20
    * - `-`
      - 왼쪽 값에서 오른쪽 값을 뺌
      - a = 10 - 5;
      - 5
    * - `*`
      - 왼쪽과 오른쪽 값을 곱함
      - a = 10 * 2;
      - 20
    * - /
      - 왼쪽 값을 오른쪽 값으로 나눈 값
      - a = 9 / 3;
      - 3
    * - %
      - 왼쪽 값을 오른쪽 값으로 나눈 나머지
      - a = 10 / 3;
      - 1
    * - >
      - 왼쪽 값이 오른쪽 값보다 큰지 확인
      - a = 10 > 5;
      - true
    * - >=
      - 왼쪽 값이 오른쪽 값 이상인지 확인
      - a = 10 >= 20;
      - false
    * - <
      - 왼쪽 값이 오른쪽 값보다 작은지 확인
      - a= 10 < 5;
      - false
    * - <=
      - 왼쪽 값이 오른쪽 값 이하인지 확인
      - a = 10 <= 20;
      - true
    * - ==
      - 왼쪽 값과 오른쪽 값이 같은지 확인
      - a = 10 == 10;
      - true
    * - !=
      - 왼쪽 값과 오른쪽 값이 다른지 확인
      - a = 10 != 10;
      - false
    * - &&
      - 양쪽 모두 참(true)이여야, 참
      - a = (10==10) && (20==20);
      - true
    * - ||
      - 양쪽 중 하나만 참(true)이면, 참
      - a = (10==10) && (20==30);
      - true
    * - !
      - true면 false로, false면 true로 연산
      - b = true; a = !b;
      - false

|
| 여러 연산자들이 있지만 주로 사용하는 것들 위주로 표를 작성했습니다.
| 사칙연산이나 기존 수학기호를 그대로 사용하는 것이 많기 때문에 익숙하실 겁니다.
| 또한 위 연산자는 숫자에만 적용되는 것이 아니라 변수에도 적용이 됩니다.
| 
| 그렇다면, 아래의 연산에서는 a 변수에 어떤 값들이 저장될지 생각해보세요.
|
| :blackbold:`Q1` 
| int a = 1;
| a = a + 1;
| :blackbold:`Q2`
| int a = 2;
| a = 2 + a * a;
| :blackbold:`Q2`
| int b = 10;
| float a = b / 3;
| :blackbold:`Q4`
| bool a = true;
| a = a && !a;

| 정답

.. toggle::

    | A1 : a는 2 입니다.
    | A2 : a는 6 입니다.
    | A3 : a는 3.0 입니다.
    | A4 : a는 false 입니다.

| 
| 생각한것과 다른 값이 나온것이 있나요? 아마 두 개 다른 값이 나왔을것이라 예상해봅니다.
| 보통 Q2는 연산자의 연산순서에 의한 실수가 있었을 것이라 생각합니다.
| 사칙연산도 덧셈, 뺄셈보다 곱셈, 나눗셈을 먼저해야 하는 것과 마찬가지입니다.

.. list-table:: :subtitlesmall:`연산자 우선순위`
    :widths: 5 5 5
    :header-rows: 1

    * - 우선순위
      - 연산자
      - 방향
    * - 1
      - () [] -> . ++ --
      - ->
    * - 2
      - sizeof ++ -- & ~ ! * + -
      - <-
    * - 3
      - `* / %`
      - ->
    * - 4
      - `+ -`
      - ->
    * - 5
      - >> <<
      - ->
    * - 6
      - > >= < <=
      - ->
    * - 7
      - == !=
      - ->
    * - 8
      - &
      - ->
    * - 9
      - ^
      - ->
    * - 10
      - `|`
      - ->
    * - 11
      - &&
      - ->
    * - 12
      - ||
      - ->
    * - 13
      - ?
      - <-
    * - 14
      - `= += *= /= %= &= |= <<= >>=`
      - <-
    * - 15
      - ,
      - ->

| 위 표가 연산자 우선순위입니다. 모든 연산자들은 위와 같은 순서로 연산됩니다.
| 우선순위가 많더라도 겁먹지 마시고 굳이 기억하거나 외울 필요는 없습니다.
| 필요할 때 찾아보시면 되고, 연산이 헷갈려서, 값이 다르게 나올 것 같으면 괄호를 이용해서 순위를 먼저 지정해줍니다.
| 이런 순서로 되어 있구나 라고 슬쩍 보시고 넘어가시면 됩니다. 
|
| 생각한 것과 다르게 나온 것이 Q3 일 겁니다.
| Q3는 실수 자료형에 float 자료형에 b/3 계산 값을 초기화(처음 값 저장)하는데 당연히 3.33333... 이 아닌가? 라고 생각하셨을 수 있습니다.
| 하지만 :blackbold:`'b/3' 연산이 먼저 진행` 됩니다. 여기 분자 b는 실수가 아니라 정수임으로 b/3 은 정수로 결과값이 나옵니다. (분자가 실수면, 분모가 정수라도 실수 값이 계산됨)
| a에 3.3333.. 값이 될려면 아래와 같이 작성되어야 합니다.
|

.. code-block:: c++
        :linenos:

        int b = 10;
        float a = b;
        a = a/3;