.. # WARNING: This sphinx documentation file was automatically
.. # created directly from documentation info in the source code.
.. # DO NOT CHANGE THIS FILE, since changes will be lost upon
.. # its next update.  Instead, change the info in the source code.
.. # This file was automatically created on:
.. # 2021-06-04T16:35:16.485739Z

.. _section-top_emulator_global_registers:

.. index::
   single: Emulator Global Registers
   single: registers set; Emulator Global Registers

Emulator Global Registers
=========================

List of Registers
-----------------

The PIO emulator provides global registers, hereafter
called *Emulator Global Registers*, that are used to inspect
and control the emulator as a whole (rather than just
referring to a specifc PIO) and that are accessible through
this registers facade and provided in addition to the
registers of the original RP2040 hardware.
Base address for the emulator global register set is
0x58000000.


.. csv-table::
   :header: Offset, Name, Info
   :widths: 8, 20, 40

   0x000, :ref:`PWR_UP <PWR_UP-details-label>`, "Writing the value 0xa55a5aa5 to this address will fully reset the emulator.  Writing any other value will have no effect."
   0x004, :ref:`MASTERCLK_FREQ <MASTERCLK_FREQ-details-label>`, "Unsigned integer value that represents the target frequency of the emulation in 1/8Hz. That is, a value of 1 represents a frequency of 0.125 Hz, and the maximum value of 2^32 - 1 = 4294967295 represents a frequency of 536.870911875MHz.  A value of 0 indicates that the emulation should execute as fast as possible.  Note that there is no guarantee at all to run at the specified frequency.  Instead, the value is just the frequency that the emulation tries to catch up with as close as possible.  The reset value corresponds to a target frequency of 125MHz."
   0x008, :ref:`MASTERCLK_MODE <MASTERCLK_MODE-details-label>`, "Selects the clock mode."
   0x00c, :ref:`MASTERCLK_TRIGGER_PHASE0 <MASTERCLK_TRIGGER_PHASE0-details-label>`, "When master clock is in single step mode, writing any value to this address will trigger the emulator to execute phase 0 of the next clock cycle.  In phase 0, the emulator fetches and decodes the next instruction.  When already in phase 0, writing once more to this address will have no effect.  When master clock is in target frequency mode, writing to this address will have no effect.  Upon reset, the system is in phase 1. Reading from this register will return value 0x1 if and only if the emulator is in phase 0 *and* phase 0 is settled (i.e. the emulator has completed all operations to be performed during this phase), and 0x0 otherwise."
   0x010, :ref:`MASTERCLK_TRIGGER_PHASE1 <MASTERCLK_TRIGGER_PHASE1-details-label>`, "When master clock is in single step mode, writing any value to this address will trigger the emulator to execute phase 1 of the current clock cycle.  In phase 1, the emulator will execute the instruction previously decoded in phase 0.  When already in phase 1, writing once more to this address will have no effect. When master clock is in target frequency mode, writing to this address will have no effect.  Upon reset, the system is in phase 1. Reading from this register will return value 0x1 if and only if the emulator is in phase 1 *and* phase 1 is settled (i.e. the emulator has completed all operations to be performed during this phase), and 0x0 otherwise."
   0x014, :ref:`WALLCLOCK_LSB <WALLCLOCK_LSB-details-label>`, "LSB value (lower 32 bits) of wall clock.  The wall clock is a 64 bit counter that is initialized to 0 and incremented whenever the master clock has completed a cycle."
   0x018, :ref:`WALLCLOCK_MSB <WALLCLOCK_MSB-details-label>`, "MSB value (upper 32 bits) of wall clock.  The wall clock is a 64 bit counter that is initialized to 0 and incremented whenever the master clock has completed a cycle."
   0x01c, :ref:`GPIO_PINS <GPIO_PINS-details-label>`, "Each bit of this value corresponds to each of the 32 GPIO pins' pad input state that is provided from some external source."

.. _PWR_UP-details-label:

.. index::
   single: register details; PWR_UP
   single: PWR_UP

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: PWR_UP Register
-----------------------------------------------------------------------------------------

**Offset:** 0x000

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Writing the value 0xa55a5aa5 to this address will fully reset the emulator.  Writing any other value will have no effect.", WF, 0

.. _MASTERCLK_FREQ-details-label:

.. index::
   single: register details; MASTERCLK_FREQ
   single: MASTERCLK_FREQ

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: MASTERCLK_FREQ Register
-------------------------------------------------------------------------------------------------

**Offset:** 0x004

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Unsigned integer value that represents the target frequency of the emulation in 1/8Hz. That is, a value of 1 represents a frequency of 0.125 Hz, and the maximum value of 2^32 - 1 = 4294967295 represents a frequency of 536.870911875MHz.  A value of 0 indicates that the emulation should execute as fast as possible.  Note that there is no guarantee at all to run at the specified frequency.  Instead, the value is just the frequency that the emulation tries to catch up with as close as possible.  The reset value corresponds to a target frequency of 125MHz.", RW, 1000000000

.. _MASTERCLK_MODE-details-label:

.. index::
   single: register details; MASTERCLK_MODE
   single: MASTERCLK_MODE

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: MASTERCLK_MODE Register
-------------------------------------------------------------------------------------------------

**Offset:** 0x008

**Description**

Selects the clock mode.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:1, Reserved., "―", ―, ―
   0, ―, "Bit 0 = 0: Target frequency mode. Bit 0 = 1: Single step mode.", RW, 0

.. _MASTERCLK_TRIGGER_PHASE0-details-label:

.. index::
   single: register details; MASTERCLK_TRIGGER_PHASE0
   single: MASTERCLK_TRIGGER_PHASE0

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: MASTERCLK_TRIGGER_PHASE0 Register
-----------------------------------------------------------------------------------------------------------

**Offset:** 0x00c

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "When master clock is in single step mode, writing any value to this address will trigger the emulator to execute phase 0 of the next clock cycle.  In phase 0, the emulator fetches and decodes the next instruction.  When already in phase 0, writing once more to this address will have no effect.  When master clock is in target frequency mode, writing to this address will have no effect.  Upon reset, the system is in phase 1. Reading from this register will return value 0x1 if and only if the emulator is in phase 0 *and* phase 0 is settled (i.e. the emulator has completed all operations to be performed during this phase), and 0x0 otherwise.", WF, ―

.. _MASTERCLK_TRIGGER_PHASE1-details-label:

.. index::
   single: register details; MASTERCLK_TRIGGER_PHASE1
   single: MASTERCLK_TRIGGER_PHASE1

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: MASTERCLK_TRIGGER_PHASE1 Register
-----------------------------------------------------------------------------------------------------------

**Offset:** 0x010

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "When master clock is in single step mode, writing any value to this address will trigger the emulator to execute phase 1 of the current clock cycle.  In phase 1, the emulator will execute the instruction previously decoded in phase 0.  When already in phase 1, writing once more to this address will have no effect. When master clock is in target frequency mode, writing to this address will have no effect.  Upon reset, the system is in phase 1. Reading from this register will return value 0x1 if and only if the emulator is in phase 1 *and* phase 1 is settled (i.e. the emulator has completed all operations to be performed during this phase), and 0x0 otherwise.", WF, ―

.. _WALLCLOCK_LSB-details-label:

.. index::
   single: register details; WALLCLOCK_LSB
   single: WALLCLOCK_LSB

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: WALLCLOCK_LSB Register
------------------------------------------------------------------------------------------------

**Offset:** 0x014

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "LSB value (lower 32 bits) of wall clock.  The wall clock is a 64 bit counter that is initialized to 0 and incremented whenever the master clock has completed a cycle.", RO, ―

.. _WALLCLOCK_MSB-details-label:

.. index::
   single: register details; WALLCLOCK_MSB
   single: WALLCLOCK_MSB

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: WALLCLOCK_MSB Register
------------------------------------------------------------------------------------------------

**Offset:** 0x018

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "MSB value (upper 32 bits) of wall clock.  The wall clock is a 64 bit counter that is initialized to 0 and incremented whenever the master clock has completed a cycle.", RO, ―

.. _GPIO_PINS-details-label:

.. index::
   single: register details; GPIO_PINS
   single: GPIO_PINS

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: GPIO_PINS Register
--------------------------------------------------------------------------------------------

**Offset:** 0x01c

**Description**

Each bit of this value corresponds to each of the
32 GPIO pins' pad input state that is provided from
some external source.

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31, INFROMPAD_GPIO31, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   30, INFROMPAD_GPIO30, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   29, INFROMPAD_GPIO29, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   28, INFROMPAD_GPIO28, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   27, INFROMPAD_GPIO27, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   26, INFROMPAD_GPIO26, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   25, INFROMPAD_GPIO25, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   24, INFROMPAD_GPIO24, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   23, INFROMPAD_GPIO23, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   22, INFROMPAD_GPIO22, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   21, INFROMPAD_GPIO21, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   20, INFROMPAD_GPIO20, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   19, INFROMPAD_GPIO19, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   18, INFROMPAD_GPIO18, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   17, INFROMPAD_GPIO17, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   16, INFROMPAD_GPIO16, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   15, INFROMPAD_GPIO15, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   14, INFROMPAD_GPIO14, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   13, INFROMPAD_GPIO13, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   12, INFROMPAD_GPIO12, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   11, INFROMPAD_GPIO11, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   10, INFROMPAD_GPIO10, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   9, INFROMPAD_GPIO9, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   8, INFROMPAD_GPIO8, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   7, INFROMPAD_GPIO7, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   6, INFROMPAD_GPIO6, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   5, INFROMPAD_GPIO5, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   4, INFROMPAD_GPIO4, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   3, INFROMPAD_GPIO3, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   2, INFROMPAD_GPIO2, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   1, INFROMPAD_GPIO1, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0
   0, INFROMPAD_GPIO0, "signal value 0x0 or 0x1, as provided by some external source.", RW, 0

