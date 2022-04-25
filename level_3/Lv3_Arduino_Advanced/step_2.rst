인터럽트
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

| 코드 하나가 실행되고 있습니다. 동작하던 중 어느 지점에서 잠깐 멈추고 다른 작업을 하고 다시 돌아와 이어서 작업하는게 가능할까요?
| 그런 작업을 가능하게 하는 것이 인터럽트입니다. 인터럽트 뜻은 방해하다, 중단하다 입니다. 코드가 실행되는 도중 잠깐 멈추고 다른 작업을 하고 돌아옵니다.
|

.. image:: ../images/Lv3/Chapter_6/Step2_1.jpg
   :width: 600
   :align: center

|
| 인터럽트는 위와 같은 형태로 진행됩니다. 메인 코드(메인 프로그램)가 수행되고 있는 도중에 인터럽트가 발생되면, 인터럽트를 수행하고 돌아옵니다. 그렇다면 궁금한 것이 인터럽트는 언제 발생되는가? 입니다.
| 아두이노에는 인터럽트 핀으로 사용할 수 있는 핀이 정해져 있습니다. 이 핀이 HIGH인지, LOW인지 혹은 변화가 있는지에 따라 인터럽트를 실행하도록 설정할 수 있습니다. 또한 일정시간마다 인터럽트를 발생시킬 수도 있습니다.
| 
| 함수도 유사한 기능을 생각하실 수 있지만, 함수는 호출을 해야 해당 지점에서 함수를 수행하고 돌아오는 것과 달리, 인터럽트는 인터럽트 핀, 시간에 따라 즉각적으로 인터럽트 코드를 수행하고 돌아옵니다.
|
| 3D 펜에서는 시간과 관련된 인터럽트를 사용합니다.