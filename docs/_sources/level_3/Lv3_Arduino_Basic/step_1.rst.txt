자료형
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

| 아두이노를 코딩할 때 여러가지 숫자, 문자들을 다루게 됩니다.
| 이런 데이터들의 형태를 :blackbold:`자료형` 이라고 합니다.
|
| :subtitle:`자료형`
| 자료형에는 여러가지 종류가 있습니다.

.. list-table:: 자료형 종류
    :widths: 25 25 50
    :header-rows: 1

    * - 자료형 이름
      - 형태
      - 범위
    * - boolean
      - 논리형
      - true, false
    * - char
      - 문자형
      - -128 ~ 127
    * - byte
      - 정수형
      - 0 ~255
    * - int
      - 정수형
      - -32,768 ~ 32,767
    * - unsigned int
      - 정수형
      - 0 ~ 65,535
    * - long
      - 정수형
      - -2,147,483,648 ~ 2,147,483,647
    * - unsigned long
      - 정수형
      - 0 ~ 4,294,967,295
    * - float
      - 실수형
      - 약 1.2x10^-38 ~ 3.4x10^38
    * - double
      - 실수형
      - 약 2.3x10^-308 ~ 1.7x10^308
    * - string
      - 문자열
      -

| 자주 사용되는 자료형들입니다. 물론 더 많은 자료형이 있지만 위의 5개 정도만 알아둡니다.

| :subtitlesmall:`boolean`
| boolean의 이름은 영국의 수학자 조지 불(George boole)이 창안해서 붙여진 이름으로 논리값을 나타냅니다. 논리값이라는 것은 :blackbold:`참, 거짓` 을 뜻합니다. 영어로는 true, false입니다.
| 아두이노에서는 boolean과 bool 을 함께 사용할 수 있습니다. :blackbold:`아두이노에서는 숫자로도 true와 false를 구별하기도 합니다.` 0 은 false이며, 다른 나머지 숫자들은 true로 인식합니다.
|
| :subtitlesmall:`char`
| char는 글자, 문자를 뜻하는 character에서 앞부분만 사용된 것으로, :blackbold:`문자를 저장` 합니다.
| 문자를 저장하는데 범위는 왜 숫자냐? 고 물으실 수 있습니다.
| 간단하게 설명드리면, 프로그래밍에서 문자를 ASCII 코드를 숫자로 표시 되곤합니다. ASCII 코드에는 'A'라는 글자가 65라는 값을 가지고 있습니다.
|
| :subtitlesmall:`byte`
| byte는 말 그대로 1바이트를 사용하는 정수 자료형이며 char와 다른 점은 - 값이 범위에 없다는 것입니다.
|
| :subtitlesmall:`int`
| int는 정수라는 뜻을 가진 integer라는 단어에서 만들어 졌습니다. 정수값을 저장하며 범위는 -32,768 ~ 32,767 입니다.
|
| :subtitlesmall:`unsigned int`
| unsigned int 는 int 와 마찬가지로 정수를 다루지만, 범위만 다릅니다 unsigned 의 뜻 그대로 음수를 포함하지 않는 범위를 가집니다. 범위는 0 ~ 65,535 입니다. unsigned int는 65,535에서 1을 더하는 계산을 하면 0 이됩니다.
|
| :subtitlesmall:`long`
| long은 int와 마찬가지로 정수값을 저장하지만, int보다 범위가 훨씬 큰 자료형입니다. :blackbold:`큰 수를 다루는 경우에 사용` 되며, 범위는 -2,147,483,648 ~ 2,147,483,647 입니다.
|
| :subtitlesmall:`unsigned long`
| unsigned long 는 long 와 마찬가지로 정수를 다루지만, 범위만 다릅니다 unsigned 의 뜻 그대로 음수를 포함하지 않는 범위를 가집니다. 범위는 0 ~ 4,294,967,295 입니다. unsigned long는 4,294,967,295에서 1을 더하는 계산을 하면 0 이됩니다.
| 
| :subtitlesmall:`float`
| float은 :blackbold:`소수점을 포함하는 실수` 를 다룹니다. 단어의 유래는 실수를 표현하는 방법이 여러가지가 있는데, 부동소수점(floating point) 방식을 사용한다고 하여 붙여졌습니다. ※부동소수점이 뭔지는 모르셔도 됩니다.
| 범위는 약 1.2x10^-38 ~ 3.4x10^38 입니다.
|
| :subtitlesmall:`double`
| double는 float과 같이 실수를 다루지만, 범위만 다릅니다. 범위는 약 2.3x10^-308 ~ 1.7x10^308 입니다.
|
| :subtitlesmall:`string`
| string은 문자열을 뜻합니다. char 자료형은 문자 하나만을 취급하는 반면, string은 여러개로 이어진 문자열을 취급합니다.