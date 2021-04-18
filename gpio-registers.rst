RP2040 GPIO Registers
=====================

The PIO emulator's interface provides access to a subset of the
registers described in the Raspberry Pi Foundation's *RP2040
datasheet*, Sect. 2.19.6 *List of Registers* of Sect. 2.19 *GPIO*
(i.e. it provides meta information such as register labels).  This
subset has been carefully chosen, having in mind a subset for making
the PIO work.

Specifically, the following registers are provided via the register
facade.

IO -- User Bank
---------------

The PIO emulator's interface provides access to all of these registers
described in the Raspberry Pi Foundation's *RP2040 datasheet*,
Sect. 2.19.6.1 *IO -- User Bank* of Sect. 2.19 *GPIO* (i.e. it
provides meta information such as register labels).

All of registers ``GPIOx_STATUS`` and ``GPIOx_CTRL`` (for ``x`` in the
range 0…31) are fully supported with a working backend implementation.

All other registers in this bank are provided via the register facade
(i.e. they provide meta information such as register labels), but they
are not backed by any working implementation.

See *RP2040 datasheet*, Sect. 2.19.6.1 *IO -- User Bank* for an
overview of and details about these registers.

Pad Control -- User Bank
------------------------

The PIO emulator's interface provides access to all of these registers
described in the Raspberry Pi Foundation's *RP2040 datasheet*,
Sect. 2.19.6.3 *Pad Control -- User Bank* of Sect. 2.19 *GPIO*
(i.e. it provides meta information such as register labels), but
currently, none of these registers is backed by any functional
implementation.  However, support is planned for the future to be able
to check correct setup of the GPIO pins.

See *RP2040 datasheet*, Sect. 2.19.6.3 *Pad Control -- User Bank* for
an overview of and details about these registers.

References
----------

[1] `RP2040 datasheet
<https://datasheets.raspberrypi.org/rp2040/rp2040-datasheet.pdf>`_.
