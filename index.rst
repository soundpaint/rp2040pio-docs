.. RP2040 PIO Emulator documentation master file, created by
   sphinx-quickstart on Sun Apr 11 04:45:41 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

RP2040 PIO Emulator
===================

In late January of 2021, the `Raspberry Pi Foundation
<https://www.raspberrypi.org/>`_ announced their new `Raspberry Pi
Pico <https://www.raspberrypi.org/products/raspberry-pi-pico/>`_
microcontroller board, based on the new `RP2040 chip
<https://datasheets.raspberrypi.org/rp2040/rp2040-datasheet.pdf>`_,
that the foundation designed by itself.

Besides two dual-core Arm Cortex-M0+ processor core, the RP2040 chip
also features two *programmable I/O blocks* (*PIO*) that are highly
interesting components, each including 4 so-called *state machines*
(*SM*).  These state machines are, effectively, extremely simple, but
fast microprocessors that run in parallel and are specialized for bit
processing for the microcontroller's GPIO pins.  The concept of
*side-sets* provides for even more parallelism of bit manipulations.
Typical applications of PIO programs are implementation of I/O
protocols such as, for example, I²C, SPI or WS2812.

In general, writing PIO programs is extremely hard due to its very
special set of bit-manipulation oriented instruction set and parallel
side-effects.  Even worse, there is no way to debug a PIO program on a
real RP2040 chip.  That is, the only way to debug a PIO program is to
emulate a state machine's behaviour and its interaction with the outer
parts of its world.  This is exactly, what the RP2040 PIO emulator
does: It tries to mimick the behaviour of all of the two PIO's state
machines as precise as necessary to reproduce its logical
functionality such that a PIO program can be debugged in the emulator,
thus making developing programs for the PIO much easier.

.. figure:: images/overview.png
   :scale: 60 %
   :alt: Server Console, Monitor Control Program, Timing Diagram and
         GPIO Observer

   Server Console, Monitor Control Program, Timing Diagram and GPIO
   Observer at a Glance

   A typical development / debugging session with server console
   running in a standard terminal, client-side monitor for control and
   inspection, timing diagram for watching signals and GPIO Observer
   for watching current status of GPIO pins.

.. toctree::
   :maxdepth: 2
   :caption: Getting Started

   motivation
   overview
   download-and-compile

.. toctree::
   :maxdepth: 2
   :caption: Basic Blocks

   architecture
   emulation-server
   monitor

.. toctree::
   :maxdepth: 2
   :caption: More Client Applications

   diagram
   gpio-observer
   limitations

.. toctree::
   :maxdepth: 2
   :caption: Epilogue

   future-work

.. toctree::
   :maxdepth: 2
   :caption: User Reference Documentation

   monitor-commands
   socket-api

.. toctree::
   :maxdepth: 1
   :caption: Register API Documentation

   pico-emu-registers
   pio-emu-registers
   pio-registers
   gpio-registers

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
