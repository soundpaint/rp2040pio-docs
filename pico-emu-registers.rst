.. # WARNING: This sphinx documentation file was automatically
.. # created directly from documentation info in the source code.
.. # DO NOT CHANGE THIS FILE, since changes will be lost upon
.. # its next update.  Instead, change the info in the source code.
.. # This file was automatically created on:
.. # 2021-04-18T19:48:44.885250Z

.. _section-top_emulator_global_registers:

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
   0x00c, :ref:`MASTERCLK_TRIGGER_PHASE0 <MASTERCLK_TRIGGER_PHASE0-details-label>`, "When master clock is in single step mode, writing any value to this address will trigger the emulator to execute phase 0 of the next clock cycle.  In phase 0, the emulator fetches and decodes the next instruction.  When already in phase 0, writing once more to this address will have no effect.  When master clock is in target frequency mode, writing to this address will have no effect.  Upon reset, the system is in phase 1."
   0x010, :ref:`MASTERCLK_TRIGGER_PHASE1 <MASTERCLK_TRIGGER_PHASE1-details-label>`, "When master clock is in single step mode, writing any value to this address will trigger the emulator to execute phase 1 of the current clock cycle.  In phase 1, the emulator will execute the instruction previously decoded in phase 0.  When already in phase 1, writing once more to this address will have no effect. When master clock is in target frequency mode, writing to this address will have no effect.  Upon reset, the system is in phase 1."
   0x014, :ref:`WALLCLOCK_LSB <WALLCLOCK_LSB-details-label>`, "LSB value (lower 32 bits) of wall clock.  The wall clock is a 64 bit counter that is initialized to 0 and incremented whenever the master clock has completed a cycle."
   0x018, :ref:`WALLCLOCK_MSB <WALLCLOCK_MSB-details-label>`, "MSB value (upper 32 bits) of wall clock.  The wall clock is a 64 bit counter that is initialized to 0 and incremented whenever the master clock has completed a cycle."

.. _PWR_UP-details-label:

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: PWR_UP Register
-----------------------------------------------------------------------------------------

**Offset:** 0x000

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Writing the value 0xa55a5aa5 to this address will fully reset the emulator.  Writing any other value will have no effect.", WF, 0

.. _MASTERCLK_FREQ-details-label:

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: MASTERCLK_FREQ Register
-------------------------------------------------------------------------------------------------

**Offset:** 0x004

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "Unsigned integer value that represents the target frequency of the emulation in 1/8Hz. That is, a value of 1 represents a frequency of 0.125 Hz, and the maximum value of 2^32 - 1 = 4294967295 represents a frequency of 536.870911875MHz.  A value of 0 indicates that the emulation should execute as fast as possible.  Note that there is no guarantee at all to run at the specified frequency.  Instead, the value is just the frequency that the emulation tries to catch up with as close as possible.  The reset value corresponds to a target frequency of 125MHz.", RW, 1000000000

.. _MASTERCLK_MODE-details-label:

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

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: MASTERCLK_TRIGGER_PHASE0 Register
-----------------------------------------------------------------------------------------------------------

**Offset:** 0x00c

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "When master clock is in single step mode, writing any value to this address will trigger the emulator to execute phase 0 of the next clock cycle.  In phase 0, the emulator fetches and decodes the next instruction.  When already in phase 0, writing once more to this address will have no effect.  When master clock is in target frequency mode, writing to this address will have no effect.  Upon reset, the system is in phase 1.", WF, ―

.. _MASTERCLK_TRIGGER_PHASE1-details-label:

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: MASTERCLK_TRIGGER_PHASE1 Register
-----------------------------------------------------------------------------------------------------------

**Offset:** 0x010

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "When master clock is in single step mode, writing any value to this address will trigger the emulator to execute phase 1 of the current clock cycle.  In phase 1, the emulator will execute the instruction previously decoded in phase 0.  When already in phase 1, writing once more to this address will have no effect. When master clock is in target frequency mode, writing to this address will have no effect.  Upon reset, the system is in phase 1.", WF, ―

.. _WALLCLOCK_LSB-details-label:

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: WALLCLOCK_LSB Register
------------------------------------------------------------------------------------------------

**Offset:** 0x014

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "LSB value (lower 32 bits) of wall clock.  The wall clock is a 64 bit counter that is initialized to 0 and incremented whenever the master clock has completed a cycle.", RO, ―

.. _WALLCLOCK_MSB-details-label:

:ref:`Emulator Global Registers <section-top_emulator_global_registers>`: WALLCLOCK_MSB Register
------------------------------------------------------------------------------------------------

**Offset:** 0x018

.. csv-table::
   :header: Bits, Name, Description, Type, Reset
   :widths: 8, 20, 40, 8, 20

   31:0, ―, "MSB value (upper 32 bits) of wall clock.  The wall clock is a 64 bit counter that is initialized to 0 and incremented whenever the master clock has completed a cycle.", RO, ―
