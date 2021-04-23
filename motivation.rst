Motivation
==========

Developing programs for the PIOs is extremely challenging due to its
highly specialized instruction set with a lot of parallelism and
intended side effects.  Debugging of PIO programs on the RP2040 chip
is impossible.

Developing and Debugging PIO Pograms
------------------------------------

The set of instructions highly specialized

  * on bit manipulations rather than general-purpose computing and
  * on single-cycle precision of time.

Therefore, there is no high-level programming language available.
Instead, PIO programs must be coded with native assembler instructions
that directly translate into machine language op-codes.  Even worse,
PIO programs can not be debugged, since most of the PIO's internal
state is not accessible.

.. figure:: images/monitor-trace-a2-pc.png
   :scale: 50 %
   :alt: A tiny, but typical PIO program

   A tiny, but typical PIO program

   PIO programs are usually quite short, but their tight and therefore
   usually tricky functionality requires high expertise in developing
   and debugging.

The only practical way to overcome these challenges is to provide an
emulator that assists in developing and debugging PIO programs.  In
particular, an emulator is an invaluably helpful tool if it supports
the following features:

* Trace / single step a PIO program as aid for developing and
  debugging, which is not possible directly on the RP2040 hardware.

* Inspect all of the PIO's internal state while developing and
  debugging a PIO program.  This feature applies even to those parts
  of the PIO and state machines that are not accessible when running
  on real RP2040 hardware, such as:

  * the contents of PIO registers X, Y, ISR and OSR,

  * the current value of the ISR / OSR shift count,

  * the values currently stored in the PIO's FIFOs,

  * the number of an instruction's pending delays,

  * and many more.

  In contrast, the emulator has access to the PIO's complete internal
  logical state (otherwise, the emulation could not correctly work).

* Debug your PIO program in the context of your IDE: The emulator will
  typically run on your development host machine.  That is, there is
  no need to upload the PIO program to a real RPI2040 for each and
  every tiny change, thus saving time and stress in the course of
  small and frequent development cycles.

* Automatically generate detailed timing diagrams straight from an
  emulated run of a PIO program.  Timing diagrams are highly useful
  for debugging as well as for documentation, as proof of concept or
  fact sheet.  The selection of signals shown on the diagram is freely
  configurable.

* Debug a PIO program even if there is no RP2040 hardware at hand.
  (Fun fact: It is still challenging to get hands on a RP2040, since
  many distributors are sold out or have only a small amount of
  RP2040s in stock.  I still do not own an RP2040 of my own, but
  solely have to rely on the specs and other sources of documentation
  and use the example PIO programs in the RP2040 datasheet for testing
  and verification.)

Finally, there is motivation for developing an emulator that applies
mainly to me personally: If I succeed in implementing a (more or less)
correctly working emulation of the PIO, than I am somewhat confident
that I have basically understood how the PIO works and what
capabilities it has when it comes to writing PIO programs for it.

Technical Background
--------------------

For a more technical in-depth reasoning for those who are still not
convinced: Why *exactly* is it not possible to trace or debug PIO
programs, as I just claimed above?

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
