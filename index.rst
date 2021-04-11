.. RP2040 PIO Emulator documentation master file, created by
   sphinx-quickstart on Sun Apr 11 04:45:41 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to RP2040 PIO Emulator's documentation!
===============================================

The RP2040's two *programmable I/O blocks* (*PIO*) are highly
interesting components of the RP2040 chip, each including 4 *state
machines* (*SM*), that are effectively very simple, but fast
processors that run in parallel specialized for bit processing on the
GPIO pins.  The concept of *side-sets* provides for even more
parallelism of bit manipulations.

Writing programs for the PIOs is extremely challenging.  Due to the
set of instructions highly specialized on bit manipulations rather
than general-purpose computing as well as the goal of performing bit
manipulations with single-cycle precision of time, there is no
high-level programming language.  Instead, the PIOs must be coded with
native assembler instructions that directly translate into machine
language op-codes.  Even worse, PIO programs can not at all debugged
for the following reasons:

* PIO programs run on the RP2040 chip within one of the two PIO
  hardware blocks.  Unlike microprocessors of desktop computers,
  notebooks, mobile phones or similar hardware, the RP2040 is
  microcontroller, and there is no multi-user / multi-process (time
  sharing) operating system running on the chip.  Usually, due to the
  lack of mult-process support, there is only a single thread of
  execution per processor core that can not be preempted by another
  debugging process.  Also, on a microcontroller, resources are
  limited such that a debugging can be performed only to a very
  limited extent directly on the chip.
* More specifically, PIO programs run on the state machines inside of
  a PIO block, and access to this block from outside (even from the
  ARM cores) is very limited.  For example, you can write op-codes
  into the PIO's instruction memory, but you can not read the current
  contents of that memory.  You can not even determine the current
  values of a state machine's current scratch registers X or Y,
  neither the contents of the shift registers ISR and OSR, the current
  ISR / OSR shift count or the number of an instruction's pending
  delays and other internal state variables.
* While the code running on the RP2040's ARM cores can basically start
  and stop state machines, there is no way to stop it at some specific
  instruction or after a number of specific cycles has been executed,
  since the state machines run at their own speed, depending on the
  state machines' individual clock configurations.

The only way to debug a PIO program is to emulate a state machine's
behaviour and its interaction with the outer parts of its world.  This
is, what the RP2040 PIO emulator does: It tries to mimick the
behaviour of all of the two PIO's state machines as precise as
possible to reproduce its binary functionality such that a PIO program
can be debugged in the emulator.

.. toctree::
   :maxdepth: 2
   :caption: Getting Started:

   motivation
   download-and-compile
   emulation-server
   diagram
   gpio-observer
   limitations
   future-work

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
