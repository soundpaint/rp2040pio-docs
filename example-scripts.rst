.. # WARNING: This sphinx documentation file was automatically
.. # created directly from documentation info in the source code.
.. # DO NOT CHANGE THIS FILE, since changes will be lost upon
.. # its next update.  Instead, change the info in the source code.
.. # This file was automatically created on:
.. # 2021-06-22T21:54:00.485167Z

.. index::
   single: scripts; examples
   single: example scripts
   single: reference; example scripts

.. _example-scripts-reference:

Example Scripts Reference
=========================

The RP2040 PIO Emulator and client
applications are bundled with a set of
built-in example scripts.  These scripts
loosely follow some of the PIO code examples
in the RP2040 datasheet, but are adapted to
run as Monitor scripts, using the Monitor
specific syntax of commands.

In the Monitor application, the set of thesebuilt-in example scripts can be listed with
the Monitor command ``script --list``.

.. index::
   single: script group; APA102
   single: APA102 script group

.. _APA102-example-script-group:

APA102
------

.. index::
   single: script; apa102-mini
   single: apa102-mini script

.. _apa102-mini-example-script:

APA102 Mini (``apa102-mini``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for APA102 Mini example.
To be executed on PIO 0, SM 0.
pin_din is mapped to GPIO0 in this example.
pin_clk is mapped to GPIO1 in this example.

.. index::
   single: script; apa102-rgb555
   single: apa102-rgb555 script

.. _apa102-rgb555-example-script:

APA102 RGB555 (``apa102-rgb555``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for AP102 RGB555 example.
To be executed on PIO 0, SM 0.
output pin is mapped to GPIO0.

.. index::
   single: script group; Autopush and Autopull
   single: Autopush and Autopull script group

.. _Autopush and Autopull-example-script-group:

Autopush and Autopull
---------------------

.. index::
   single: script; auto-push-pull
   single: auto-push-pull script

.. _auto-push-pull-example-script:

Auto-Push-Pull (``auto-push-pull``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for auto-push-pull example (see RP2040
datasheet, Sect. 3.5.4. "Autopush and Autopull").
To be executed on PIO 0, SM 0.

.. index::
   single: script; autopull
   single: autopull script

.. _autopull-example-script:

Autopull (``autopull``)
^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for auto pull example (see RP2040
datasheet, Sect. 3.5.4. "Autopush and Autopull").
To be executed on PIO 0, SM 0.
Clock (side-set) output is mapped to GPIO 0.
Data (OUT) ouput is mapped to GPIO 1.

.. index::
   single: script; manual-pull
   single: manual-pull script

.. _manual-pull-example-script:

Manual Pull (``manual-pull``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for manual pull example (see RP2040
datasheet, Sect. 3.5.4. "Autopush and Autopull").
To be executed on PIO 0, SM 0.
Clock (side-set) output is mapped to GPIO 0.
Data (OUT) ouput is mapped to GPIO 1.

.. index::
   single: script; pull-example1
   single: pull-example1 script

.. _pull-example1-example-script:

Pull Example 1 (``pull-example1``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for pull_example1 (see RP2040
datasheet, Sect. 3.2.3.1. "Output Shift
Register (OSR)").
To be executed on PIO 0, SM 0.

Each FIFO entries holds 4 bytes of output data.
Each 2nd cycle, the next byte is output on pins
GPIO0…GPIO7.

.. index::
   single: script; pull-example2
   single: pull-example2 script

.. _pull-example2-example-script:

Pull Example 2 (``pull-example2``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for pull_example2 (see RP2040
datasheet, Sect. 3.2.3.1. "Output Shift
Register (OSR)").
To be executed on PIO 0, SM 0.

Each FIFO entries holds 4 bytes of output data.
Each 2nd cycle, the next byte is output on pins
GPIO0…GPIO7.

.. index::
   single: script; pull-example3
   single: pull-example3 script

.. _pull-example3-example-script:

Pull Example 3 (``pull-example3``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for pull_example3 (see RP2040
datasheet, Sect. 3.2.3.1. "Output Shift
Register (OSR)").
To be executed on PIO 0, SM 0.

Each FIFO entries holds 4 bytes of output data.
Each 2nd cycle, the next byte is output on pins
GPIO0…GPIO7.

.. index::
   single: script; pull-example4
   single: pull-example4 script

.. _pull-example4-example-script:

Pull Example 4 (``pull-example4``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script like pull_example3 (see RP2040
datasheet, Sect. 3.2.3.1. "Output Shift
Register (OSR)"), but with an output of 1 byte
every system cycle.
To be executed on PIO 0, SM 0.

Each FIFO entries holds 4 bytes of output data.
Each 2nd cycle, the next byte is output on pins
GPIO0…GPIO7.

.. index::
   single: script; somewhat-manual-pull
   single: somewhat-manual-pull script

.. _somewhat-manual-pull-example-script:

Somewhat Manual Pull (``somewhat-manual-pull``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for partial auto pull example (see RP2040
datasheet, Sect. 3.5.4 "Autopush and Autopull").
To be executed on PIO 0, SM 0.
Clock (side-set) output is mapped to GPIO 0.
Data (OUT) ouput is mapped to GPIO 1.

.. index::
   single: script group; Differential Manchester (BMC) TX and RX
   single: Differential Manchester (BMC) TX and RX script group

.. _Differential Manchester (BMC) TX and RX-example-script-group:

Differential Manchester (BMC) TX and RX
---------------------------------------

.. index::
   single: script; bmc-rx
   single: bmc-rx script

.. _bmc-rx-example-script:

Differential Manchester RX (``bmc-rx``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for BMC RX example (see RP2040 datasheet,
Sect. 3.6.6. "Differential Manchester (BMC) TX and RX").  To be
executed on PIO 0, SM 0.

.. index::
   single: script; bmc-tx
   single: bmc-tx script

.. _bmc-tx-example-script:

Differential Manchester TX (``bmc-tx``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for BMC TX example (see RP2040 datasheet,
Sect. 3.6.6. "Differential Manchester (BMC) TX and RX").  To be
executed on PIO 0, SM 0.

.. index::
   single: script group; Manchester Serial TX and RX
   single: Manchester Serial TX and RX script group

.. _Manchester Serial TX and RX-example-script-group:

Manchester Serial TX and RX
---------------------------

.. index::
   single: script; manchester-rx
   single: manchester-rx script

.. _manchester-rx-example-script:

Manchester Serial RX (``manchester-rx``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for Manchester Serial RX example (see RP2040
datasheet, Sect. 3.6.5. "Manchester Serial TX and RX").  To be
executed on PIO 0, SM 0.

.. index::
   single: script; manchester-tx
   single: manchester-tx script

.. _manchester-tx-example-script:

Manchester Serial TX (``manchester-tx``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for Manchester Serial TX example (see RP2040
datasheet, Sect. 3.6.5. "Manchester Serial TX and RX").  To be
executed on PIO 0, SM 0.

.. index::
   single: script group; SPI
   single: SPI script group

.. _SPI-example-script-group:

SPI
---

.. index::
   single: script; spi-cpha0
   single: spi-cpha0 script

.. _spi-cpha0-example-script:

SPI CPHA0 (``spi-cpha0``)
^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for SPI CPHA0 example.
To be executed on PIO 0, SM 0.
SCK is side-set pin.
MOSI is OUT pin.
MISO is IN pin.
MOSI and MISO mapped to same pin, so we get loopback.
n_bits = 8 in this example.

.. index::
   single: script; spi-cpha0-cs
   single: spi-cpha0-cs script

.. _spi-cpha0-cs-example-script:

SPI CPHA0 with Chip Select (``spi-cpha0-cs``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for SPI CPHA0 with Chip Select example.
To be executed on PIO 0, SM 0.
SCK is side-set pin 0.
CSn is side-set pin 1 (n=1).
MOSI is OUT pin (host-to-device).
MISO is IN pin (device-to-host).
MOSI and MISO mapped to same pin, so we get loopback.
n_bits = 8 in this example.

.. index::
   single: script; spi-cpha1
   single: spi-cpha1 script

.. _spi-cpha1-example-script:

SPI CPHA1 (``spi-cpha1``)
^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for SPI CPHA1 example.
To be executed on PIO 0, SM 0.
SCK is side-set pin.
MOSI is OUT pin.
MISO is IN pin.
MOSI and MISO mapped to same pin, so we get loopback.
n_bits = 8 in this example.

.. index::
   single: script; spi-cpha1-cs
   single: spi-cpha1-cs script

.. _spi-cpha1-cs-example-script:

SPI CPHA1 with Chip Select (``spi-cpha1-cs``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for SPI CPHA1 with Chip Select example.
To be executed on PIO 0, SM 0.
SCK is side-set pin 0.
CSn is side-set pin 1 (n=1).
MOSI is OUT pin (host-to-device).
MISO is IN pin (device-to-host).
MOSI and MISO mapped to same pin, so we get loopback.
n_bits = 8 in this example.

.. index::
   single: script; spi-tx-fast
   single: spi-tx-fast script

.. _spi-tx-fast-example-script:

SPI TX Fast (``spi-tx-fast``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for SPI TX Fast example,
as described in RP2040 datasheet,
Sect. 3.5.1. "Side-set".

To be executed on PIO 0, SM 0.
Data output is fed to GPIO 0.
Clock output is fed to GPIO 1.

.. index::
   single: script group; Squarewave
   single: Squarewave script group

.. _Squarewave-example-script-group:

Squarewave
----------

.. index::
   single: script; ext-wave
   single: ext-wave script

.. _ext-wave-example-script:

External Wave (``ext-wave``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for providing an external square wave signal put
onto GPIO pad 23, that changes the pin's status each 3rd clock
cycle.
This script serves as an example how to automatically set GPIO
pads in sync with another script that is executed in parallel.
See chapter "Interfacing With External Data" in the RP2040 PIO
Emulator documentation for details.

.. index::
   single: script; squarewave
   single: squarewave script

.. _squarewave-example-script:

Squarewave (``squarewave``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for Squarewave example (base version).
To be executed on PIO 0, SM 0.

.. index::
   single: script; squarewave-fast
   single: squarewave-fast script

.. _squarewave-fast-example-script:

Squarewave Fast (``squarewave-fast``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for Squarewave example ("fast" version).
To be executed on PIO 0, SM 0.

.. index::
   single: script; squarewave-wrap
   single: squarewave-wrap script

.. _squarewave-wrap-example-script:

Squarewave Wrap (``squarewave-wrap``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for Squarewave example ("wrap" version).
To be executed on PIO 0, SM 0.

.. index::
   single: script group; UART
   single: UART script group

.. _UART-example-script-group:

UART
----

.. index::
   single: script; uart-rx
   single: uart-rx script

.. _uart-rx-example-script:

UART RX (``uart-rx``)
^^^^^^^^^^^^^^^^^^^^^

Monitor script for UART RX example (see RP2040 datasheet,
Sect. 3.6.4. "UART RX").  To be executed on PIO 0, SM 0.

.. index::
   single: script; uart-rx-mini
   single: uart-rx-mini script

.. _uart-rx-mini-example-script:

UART RX Mini (``uart-rx-mini``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for UART RX Mini example (see RP2040 datasheet,
Sect. 3.6.4. "UART RX").  To be executed on PIO 0, SM 0.

.. index::
   single: script; uart-tx
   single: uart-tx script

.. _uart-tx-example-script:

UART TX (``uart-tx``)
^^^^^^^^^^^^^^^^^^^^^

Monitor script for UART TX example.
To be executed on PIO 0, SM 0.
Output is fed to GPIO 0.

.. index::
   single: script group; WS2812
   single: WS2812 script group

.. _WS2812-example-script-group:

WS2812
------

.. index::
   single: script; ws2812
   single: ws2812 script

.. _ws2812-example-script:

WS2812 (``ws2812``)
^^^^^^^^^^^^^^^^^^^

Monitor script for ws2812 example.
To be executed on PIO 0, SM 0.
Output is fed to GPIO 0.

.. index::
   single: script; ws2812-led
   single: ws2812-led script

.. _ws2812-led-example-script:

WS2812 LED (``ws2812-led``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for ws2812_led example,
as described in RP2040 datasheet,
Sect. 3.2.3.4. "Scratch Registers".

To be executed on PIO 0, SM 0.
Output is fed to GPIO 0.

.. index::
   single: script; ws2812-parallel
   single: ws2812-parallel script

.. _ws2812-parallel-example-script:

WS2812 Parallel (``ws2812-parallel``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for ws2812_parallel example.
To be executed on PIO 0, SM 0.
Output is fed to GPIO 0.

.. index::
   single: script group; Other
   single: Other script group

.. _Other-example-script-group:

Other
-----

.. index::
   single: script; addition
   single: addition script

.. _addition-example-script:

Addition (``addition``)
^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for addition example (see RP2040
datasheet, Sect. 3.6.9. "Addition").
To be executed on PIO 0, SM 0.

.. index::
   single: script; blink
   single: blink script

.. _blink-example-script:

PIO Blink (``blink``)
^^^^^^^^^^^^^^^^^^^^^

Monitor script for PIO Blink example.
To be executed on PIO 0, SM 0.
For LED on OUT pin, mapped to GPIO0.

.. index::
   single: script; clocked-input
   single: clocked-input script

.. _clocked-input-example-script:

Clocked Input (``clocked-input``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for Clocked Input example.
To be executed on PIO 0, SM 0.
Data input pin is mapped to GPIO0.
Clock input pin is mapped to GPIO1.

.. index::
   single: script; exec-example
   single: exec-example script

.. _exec-example-example-script:

Exec Example (``exec-example``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for EXEC'd instructions
example.

To be executed on PIO 0, SM 0.

.. index::
   single: script; hello
   single: hello script

.. _hello-example-script:

Hello PIO (``hello``)
^^^^^^^^^^^^^^^^^^^^^

Monitor script for Hello PIO example.
To be executed on PIO 0, SM 0.
pin is mapped to GPIO0 in this example.

.. index::
   single: script; hub75
   single: hub75 script

.. _hub75-example-script:

HUB75 (``hub75``)
^^^^^^^^^^^^^^^^^

Monitor script for HUB75 example.
To be executed on PIO0, SM0 and SM1.

This example consists of *two* PIO programs
that are executed in parallel on two
different state machines.  The first PIO program
is to be executed on SM0 and cares for output pins
GPIO6…GPIO10, GPIO12 and GPIO13.  The second PIO
program is to be executed on SM1 and cares for
GPIO0…GPIO5 and GPIO11.  In particular:

* SM1 RGB (rrggbb) out data pins, mapped to GPIO0…GPIO5.
* SM0 Row Select out pins are A-E, mapped to GPIO6…GPIO10.
* SM1 side-set pin 0 is clock_pin, mapped to GPIO11.
* SM0 side-set pin 0 is Latch (aka Strobe), mapped to GPIO12.
* SM0 side-set pin 1 is OEn, mapped to GPIO13.

.. index::
   single: script; i2c
   single: i2c script

.. _i2c-example-script:

I²C (``i2c``)
^^^^^^^^^^^^^

Monitor script for I²C example.
To be executed on PIO 0, SM 0.
pin_sda is fed to GPIO 0.
pin_scl is fed to GPIO 1.

.. index::
   single: script; logic-analyser
   single: logic-analyser script

.. _logic-analyser-example-script:

Logic Analyser (``logic-analyser``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for Logic Analyser example.
To be executed on PIO 0, SM 0.

.. index::
   single: script; pwm
   single: pwm script

.. _pwm-example-script:

PWM (``pwm``)
^^^^^^^^^^^^^

Monitor script for PWM example (see RP2040 datasheet,
Sect. 3.6.8. "PWM").  To be executed on PIO 0, SM 0.

.. index::
   single: script; st7789-lcd
   single: st7789-lcd script

.. _st7789-lcd-example-script:

ST7789 LCD (``st7789-lcd``)
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Monitor script for ST7789 LCD example.
To be executed on PIO 0, SM 0.
Data on OUT pin, mapped to GPIO0.
Clock on side-set pin, mapped to GPIO1.

