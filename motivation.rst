Motivation
==========

What is the purpose of an RP2040 emulator if you can easily use the
original?  There are a number of good reasons for doing so:

* To be able to trace / single step a PIO program as an invaluable aid
  for developing and debugging, which is hardly possible directly on
  the RP2040 hardware.

* To inspect all of the PIO's internal state while developing and
  debugging a PIO program.  This feature applies even to those parts
  of the PIO and state machines that are not accessible when running
  on real RP2040 hardware, such as:

  * the contents of PIO registers X, Y, ISR and OSR,

  * the current value of the ISR / OSR shift count or

  * the number of an instruction's pending delays.

  In contrast, the emulator has access to the PIO's complete internal
  logical state (otherwise, the emulation could not correctly work).

* To debug your PIO program in the context of your IDE: The emulator
  will typically run on your development host machine.  That is, there
  is no need to upload the PIO program to a real RPI2040 for each and
  every tiny change, thus saving time and stress in the course of
  small and frequent development cycles.

* To be able to automatically generate detailed timing diagrams
  straight from an emulated run of a PIO program.  Timing diagrams are
  highly useful for debugging as well as for documentation, as proof
  of concept or fact sheet.  The selection of signals shown on the
  diagram is freely configurable.

* To be able to debug a PIO program even if there is no RP2040
  hardware at hand.  (Fun fact: It is still challenging to get hands
  on a RP2040, since many distributors are sold out or have only a
  small amount of RP2040s in stock.  I still do not own an RP2040 of
  my own, but solely have to rely on the specs and other sources of
  documentation and use the example PIO programs in the RP2040
  datasheet for testing and verification.)

* A motivation that applies to me personally: If I succeed in
  implementing a (more or less) correctly working emulation of the
  PIO, than I am somewhat confident that I have basically understood
  how the PIO works and what capabilities it has when it comes to
  writing PIO programs for it.
