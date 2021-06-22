Future Work
===========

Some features currently may not yet work as expected and may need to
be fixed, including the following issues:

* FIFO mapping: The *exact* layout of FIFO memory in the registers'
  facade is poorly documented and therefore possibly incorrectly
  implemented.  This issue needs further investigation.

* Instruction insertion: The exact order of delays, PC value update,
  interaction with stalls, etc. is quite tricky.  There may be or may
  be not still subtle bugs in the code especially for corner cases.
  This part of the code definitely needs closer testing and / or
  review.

There are still a lot of highly desirable features that have not yet
been implemented.  This list includes, but is not limited to the
following items:

* Check if the set of monitor commands needs more features.  It should
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

  Basically, this task can already be done by writing a monitor script
  that executes any data input / output, as outlined in
  Sect. :ref:`section-top_io`.  In practice, however, writing such a
  script is tedious work, and this task should really be automated by
  providing support for injecting proper monitor commands into a
  script.

* Generate a warning whenever a race condition is detected.  In
  particular, generate a warning when multiple state machines
  concurrently access the same resource, like writing simultaneously
  to the same GPIO pin.  Warnings can be reported in the monitor
  program while debugging a program, as well as marked on the timing
  diagram.

* Generate a warning upon FIFO overflow / underflow.

* Generate a warning when trying to enqueue data to / dequeue data
  from TX, while RX is joined, and vice versa.

* Generate a warning when reading from or writing to a GPIO pin that
  has pin direction that conflicts with the type of access.

* Generate a warning if the condition for an undefined “MOV” from the
  OSR occurs whilst autopull is enabled, as specified in
  Sect. 3.5.4.2. “Autopull Details”.

* Generate a warning when instruction “WAIT 1 IRQ x” is used with an
  IRQ flag presented to the interrupt controller (cp. warning in
  Sect. 3.4.3. “WAIT”).

* Generate a warning when a client application writes to a read-only
  register of the register facade, or when reading from a write-only
  register.

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

* C language binding / integration with ``pioasm``.  PIO programs may
  contain C code that can not be directly executed by the emulator.
  Instead, we follow the idea of Pico C SDK's ``host`` interface:
  Whenever there is a direct access to the RP2040 chip via the Pico C
  SDK, we replace that access with a call to the corresponding
  emulator's register via the TCP/IP socket connection to the register
  server.  This way, even C code created by the ``pioasm`` tool will
  be able to communicate with the emulator as expected (except for
  timing, since the emulation is running at its own speed; this aspect
  needs more provsions).  For the general outline of this approach,
  see the pico-host-sdl repository at
  https://github.com/raspberrypi/pico-host-sdl.

… and many more!
