PIO Programs
============

Developing programs for the PIOs is extremely challenging due to its
highly specialized instruction set with a lot of parallelism and (by
all means intended but complex) side effects.  Debugging PIO programs
directly on the RP2040 chip is, in practice, technically rather
impossible for multiple reasons, most notably because of lack of
access onto the PIOs' internal state from outside.  However, emulation
of the PIOs' core functionality can be perfectly tailored for support
in developing and debugging PIO programs.

.. figure:: images/monitor-trace-a2-pc.png
   :scale: 80%
   :alt: A tiny, but typical PIO program

   A tiny, but typical PIO program

   PIO programs are usually quite short, but their tight and therefore
   usually tricky functionality requires high expertise in developing
   and debugging.

Instruction Set
---------------

The set of instructions highly specialized

  * on bit manipulations rather than general-purpose computing and
  * on single-cycle precision of time.

Specifically, the instruction set

* does not support any arithmetic operations except register decrement
  on jump instructions,
* does not support any logic operations except a bitwise complement
  move instruction,
* features conditional jumps that only support test for zero status
  and register inequality and
* does not provide any instructions that support the concept of a
  program stack.

Also, overall shared instruction memory per PIO is limited to 32
instruction words for all of the 4 state machines.  On the other hand,
there are highly specialized machine operations

* for serializing streams of bits into words,
* shifting words into a FIFO,
* and reversely shifting words out of a FIFO and
* deserialization of words into streams of bits,
* and, as curiosity, direct execution of synthesized instruction
  op-codes with the MOV EXEC instruction.

Also, single instructions can be inserted for execution at any clock
cycle from external sources.  Moreover, each instruction has a few
bits reserved for *side-set* and / or instruction delay.  *Side-set*
allows for further direct bit manipulations on GPIO pins and is
executed in parallel and independently from the actual instruction.

Not surprisingly, there is, at least as of now, no high-level
programming language available that would automatically translate into
this very special machine language.  In other words, at the best, PIO
programs are coded with native assembler instructions that directly
translate into machine language op-codes.

.. table:: PIO Instruction Set

  +----------+-----------------------------------------------------------+
  | Mnemonic | Short Description                                         |
  +==========+===========================================================+
  | JMP      | Set program counter to specified address if specified     |
  |          | condition is true.  Otherwise, no operation.              |
  +----------+-----------------------------------------------------------+
  | WAIT     | Stall until some condition is met.                        |
  +----------+-----------------------------------------------------------+
  | IN       | Shift specified number of bits from specified source      |
  |          | into the Input Shift Register.                            |
  +----------+-----------------------------------------------------------+
  | OUT      | Shift specified amount of bits out of the Output Shift    |
  |          | Register and write those bits to specified destination.   |
  +----------+-----------------------------------------------------------+
  | PUSH     | Push the contents of the Input Shift Register into the    |
  |          | RX FIFO as a single 32-bit word.  Clear Input Shift       |
  |          | Register to all-zeroes.                                   |
  +----------+-----------------------------------------------------------+
  | PULL     | Load a 32-bit word from the TX FIFO into the Output Shift |
  |          | Register.                                                 |
  +----------+-----------------------------------------------------------+
  | MOV      | Copy data from the specified source to the specified      |
  |          | destination.                                              |
  +----------+-----------------------------------------------------------+
  | IRQ      | Set or clear the IRQ flag selected by the specified       |
  |          | index argument.                                           |
  +----------+-----------------------------------------------------------+
  | SET      | Write specified immediate value to specified destination. |
  +----------+-----------------------------------------------------------+

The PIOs' instruction set consists of just nine different
instructions that are highly specialized on bit manipulation.

Debugging
---------

Even worse, in the course of developing PIO programs, PIO code can
neither be debugged, nor traced or single-stepped, mainly for the
following reasons.

* PIO programs run on the RP2040 chip within one of the two PIO
  hardware blocks.  Unlike microprocessors of desktop computers,
  notebooks, mobile phones or similar hardware, the RP2040 is a
  microcontroller, and there is no multi-user / multi-process (time
  sharing) operating system running on the chip.  Instead, due to the
  lack of mult-process support, there is usually only a single thread
  of execution at all, or at best, one per processor core.  But,
  without further provision, there is no underlying operating system
  that would care for cooperation between the cores, such as
  distributing threads among the cores.  In theory, one *could*, for
  example, reserve one of the ARM CPU cores for the purpose of
  debugging / logging while the other cores run in parallel the actual
  software to be debugged.  However, keep in mind that there is
  nothing like task switching.  This means, that most likely, the
  software being debugged would have to be written in a specific way
  to actively cooperate with the debugger.  This means that it would
  not be easy or even impossible to run a debugger *out of the box*
  without adapting the program to be debugged.
* Also, on a microcontroller, resources are typically limited such
  that debugging can be done only to a very limited extent directly on
  the chip without negatively affecting functionality of the actual
  software to be debugged.
* While we may need to consider a debugger to include debugging the
  code running on the ARM cores (since this code may, for example,
  provide data for our PIO program), our main scope is not the code
  running on the ARM cores, but the *PIO program* itself.  This code
  runs on the state machines inside of a PIO block, and access to this
  block from outside (even from the ARM cores) is very limited.  For
  example, you can write op-codes into the PIO's instruction memory,
  but you can not read the current contents of that memory.  You can
  not even determine the current values of a state machine's current
  scratch registers X or Y, neither the contents of the shift
  registers ISR and OSR, the current ISR / OSR shift count or the
  number of an instruction's pending delays and other internal state
  variables.
* While the code running on the RP2040's ARM cores can basically start
  and stop state machines, there is no easy way to stop it at some
  specific instruction or after a number of specific cycles has been
  executed, since the state machines run at their own speed, depending
  on the state machines' individual clock configurations.  Stopping
  PIO programs in order to implement breakpoints is, in theory,
  possible with interrupts, but would stop the PIO program only after
  a few additional clock cycles.

In summary, with huge effort, in theory very limited support for
tracing and debugging may be possible to some extent, but in parctice
hardly feasible.

Emulation
---------

The only practical way to overcome all of these limitations is to
provide an emulator that assists in developing and debugging PIO
programs.  Specifically, an emulator has the potential to emerge into
an invaluably helpful tool when supporting the following features.

* Trace / single step PIO programs as aid for developing and
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

  In contrast, an emulator has access to the PIO's complete internal
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
to the developer of the emulator personally: Succeeding in
implementing a (more or less) correctly working emulation of the PIO
creates confidence in having a thorough understanding how the PIO
works and what capabilities it has when it comes to writing PIO
programs for it.
