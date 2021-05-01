Client Applications
===================

Client applications connect to the Emulation Server for controlling
the emulation and observing the emulator's status.  Multiple clients
can concurrently interact with the server.  Consequently, a set of
parallel runnable tools sharing the same emulator can be combined to
an individually tailored devlopment and debugging environment.

Currently, the following tools are available.

.. table:: Currently Available Client Applications
    :widths: 10 10 20 60

    +----------------------------------+--------------+------------------------------------+--------------------------------------+
    | Title                            | Jar File     | Description                        | Screenshot                           |
    +==================================+==============+====================================+======================================+
    | :ref:`section-top_monitor`       | rp2040pio\_  | Textual-based interpreter with a   | .. figure:: images/monitor-help.png  |
    |                                  | monitor.jar  | set of commands for command-line   |    :scale: 40%                       |
    |                                  |              | interaction with the emulator.     |                                      |
    +----------------------------------+--------------+------------------------------------+--------------------------------------+
    | :ref:`section-top_gpio-observer` | rp2040pio\_  | Realtime visualization of GPIO     | .. figure:: images/gpio-observer.png |
    |                                  | gpioobserver | pins status (level & direction).   |    :scale: 40%                       |
    |                                  | .jar         | of all of the 32 GPIO pads.        |                                      |
    +----------------------------------+--------------+------------------------------------+--------------------------------------+
    | :ref:`section-top_code-observer` | rp2040pio\_  | Realtime visualization of PIO      | .. figure:: images/code-observer.png |
    |                                  | codeobserver | instruction memory as interpreted  |    :scale: 40%                       |
    |                                  | .jar         | by a specific state machine, also  |                                      |
    |                                  |              | considering side-set configuration |                                      |
    |                                  |              | of the particular state machine.   |                                      |
    +----------------------------------+--------------+------------------------------------+--------------------------------------+
    | :ref:`section-top_fifo-observer` | rp2040pio\_  | Realtime visualization of a state  | .. figure:: images/fifo-observer.png |
    |                                  | fifoobserver | machine's contents of FIFO memory  |    :scale: 40%                       |
    |                                  | .jar         | and status.                        |                                      |
    +----------------------------------+--------------+------------------------------------+--------------------------------------+
    | :ref:`section-top_diagram`       | rp2040pio\_  | Tool for creating timing diagrams  | .. figure:: images/diagram.png       |
    |                                  | diagram.jar  | of PIO internal state, displayed   |    :scale: 40%                       |
    |                                  |              | as signals for debugging and       |                                      |
    |                                  |              | verification.                      |                                      |
    +----------------------------------+--------------+------------------------------------+--------------------------------------+

More client applications are planned for future implementation.
