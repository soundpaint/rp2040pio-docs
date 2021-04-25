Client Applications
===================

Client applications connect to the Emulation Server for controlling
the emulation and observing the emulator's status.  Multiple clients
can concurrently interact with the server.  Consequently, a set of
parallel runnable tools sharing the same emulator can be combined to
an individually tailored devlopment and debugging environment.

Currently, the following tools are available.

+-----------+----------------------------+------------------------------------+--------------------------------------+
| Title     | Application Jar File       | Description                        | Screenshot                           |
+===========+============================+====================================+======================================+
| Monitor & | rp2040pio_monitor.jar      | Textual-based interpreter with a   | .. figure:: images/monitor-help.png  |
| Control   |                            | set of commands for command-line   |                                      |
| Program   |                            | interaction with the emulator.     |                                      |
+-----------+----------------------------+------------------------------------+--------------------------------------+
| Timing    | rp2040pio_diagram.jar      | Tool for creating timing diagrams  | .. figure:: images/diagram.png       |
| Diagram   |                            | of PIO internal state, displayed   |                                      |
|           |                            | as signals for debugging and       |                                      |
|           |                            | verification.                      |                                      |
+-----------+----------------------------+------------------------------------+--------------------------------------+
| GPIO      | rp2040pio_gpioobserver.jar | Realtime visualization of GPIO     | .. figure:: images/gpio-observer.png |
| Observer  |                            | pins status (level & direction).   |                                      |
|           |                            | of all of the 32 GPIO pads.        |                                      |
+-----------+----------------------------+------------------------------------+--------------------------------------+
| Code      | rp2040pio_codeobserver.jar | Realtime visualization of PIO      | .. figure:: images/code-observer.png |
| Observer  |                            | instruction memory as interpreted  |                                      |
|           |                            | by a specific state machine, also  |                                      |
|           |                            | considering side-set configuration |                                      |
|           |                            | of the particular state machine.   |                                      |
+-----------+----------------------------+------------------------------------+--------------------------------------+

More client applications like one for observing FIFO memory, are
planned for future implementation.
