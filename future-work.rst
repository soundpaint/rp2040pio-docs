Future Work
===========

Some essential features currently do not yet work correctly and need
to be fixed, including the following issues:

* GPIO mapping: Output priority is not yet implemented.  Currently, in
  the case of a conflicting write of multiple state machines onto the
  same GPIO pin, the state machines will just write to the PIO's GPIO
  pads, and by chance, one state machine will win without considering
  any priority.  This bug only applies if there are conflicts, but has
  no impact otherwise.

* FIFO mapping: The *exact* layout of FIFO memory in the registers'
  facade is poorly documented and therefore probably badly
  implemented.  This (presumed) bug will be fixed hopefully soon,
  together with implementing a small new FIFO Observer example client.

* Instruction insertion: The exact order of delays, PC value update,
  interaction with stalls, etc. is quite tricky.  There may be or may
  be not still subtle bugs in the code especially for corner cases.
  This part of the code definitely needs closer testing and / or
  review.

There are still a lot of highly desirable features that have not yet
been implemented.  This list includes, but is not limited to the
following items:

* The set of monitor commands needs still more features.  It should
  roughly support functionality comparable to the features of the Pico
  C SDK, such that PIO programs can properly configured and
  controlled.  Though, keep in mind, that these features are just
  convenience wrappers for direct register access.  In other words,
  for any missing feature, there should exist a sequence of native
  register read / write commands that will do the same job.

* Support specifying when and which logical values will be put onto
  the GPIO pins or when and which values will be shifted into the TX
  FIFO or shifted out from the RX FIFO via DMA access on the PIO
  (i.e. from outside of the PIO).

  For example, when developing a PIO program that is expected to
  receive an incoming stream of bits to process, this stream of bits
  somehow has to be fed into the state machine while the emulation
  runs, e.g. by modifying GPIO pins at the correct time, or by feeding
  data into the FIFOs in regular intervals.

  Actually, at least in theory, this task can already be done by
  writing a monitor script that traces through a PIO prigram cycle by
  cycle, an inserting instructions (by directly writing the PIO's
  SMx_INSTR register) for manipulating GPIO pins or FIFO contents.  In
  practice, however, writing such a script would be tedious work, and
  this task should really be automated by providing support for
  injecting proper monitor commands into a script.

* Generate a warning whenever a race condition is detected.  In
  particular, generate a warning when multiple state machines
  concurrently access the same resource, like writing simultaneously
  to the same GPIO pin.  Warnings can be reported in the monitor
  program while debugging a program, as well as marked on the timing
  diagram.

* Generate a warning upon FIFO overflow / underflow.

* Generate a warning when reading from or writing to a GPIO pin that
  has pin direction that conflicts with the type of access.

* Maybe add tooltips in timing diagrams with descriptive /
  explanatory text for all of those warnings.

* Address the lost update problem and potential race conditions
  between competing clients.  To address these issues, for example
  provide a lock mechanism for enabling a client to atomically perform
  a sequence of register accesses on the emulator.

* Make observer client applications, that use the register wait
  commmand for getting notified upon register modification, not only
  get notfied upon each clock cycle, but also when another client has
  changed the register value in question.

… and many more!
