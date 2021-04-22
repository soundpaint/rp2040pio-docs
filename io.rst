I/O
===

Usually, PIO programs are not purely self-contained suppliers, but,
other than the previusly demonstrated squarewave example, in reality
depend on I/O.  For example, implementation of a UART TX or I²C ouput
will be fed by data words from the CPU cores that the PIO program will
serialize into a stream of bits to be ouput on a GPIO pin.  Or,
reversely, implementation of a UART RX or I²C input will be fed by
external data provided on the GPIO pins as input signal that the PIO
program will collect and forward to the CPU cores as data words.

In either case, for debugging a PIO program, beside the PIO program
itself, usually some source of external data (either from the CPU
cores or from outside of the RP2040 chip) needs to be supplied to be
fed into the PIOs.  Moreover, this process of providing a stream of
data must be synchronized with the PIO program.  For example, when
tracing a PIO program in single-step mode, the process of delivering
data to the PIO must delayed accordingly, at the same pace as the PIO
program is executed.

We basically already have all necessary tools to provide an external
data source that is kept in sync with the PIO program's progress: We
just write another monitor script that runs in parallel with the
monitor instance that we use for debugging our PIO program.

External Squarewave Generator
-----------------------------

To keep this example easy, we create an external squarewave signal
that is provided on a GPIO pin and keep it in sync with our squarewave
PIO program.  However, to make it more interesting, we choose the
external squarewave to run at a speed of exactly 2/3 of that of the
squarewave produced by our example PIO program.

**TODO.**

The complete external squarewave generator that we just have developed
is also available as built-in example monitor script with the name
``ext-wave``.  For viewing the complete script, in the monitor, enter
the command ``script --show=ext-wave``.

Running the External Signal Against the PIO Program
---------------------------------------------------

Now let us perform another example monitor session to see how to apply
our external signal while debugging a PIO program.

First, start a monitor session.  Execute the example squarewave PIO
pogram monitor script with the command ``script -d --example
squarewave`` (or, abbreviated, ``sc -d -e squarewave``).  The script
will start with resetting the emulator such that we are in a
well-defined state now, load the squarewave example PIO program into
PIO0, and set up SM0 of PIO0 for execution of the program.  The
initial ``reset`` in the script will also reset the clock cycle count
to start with value 0 upon execution of the next instruction.

.. figure:: images/io-monitor-load-mon.png
   :scale: 50 %
   :alt: Prepare Monitor for Debugging Session

   Prepare Monitor for Debugging Session

   Running the ``squarewave`` monitor script will initialize the
   emulator for debugging the squarewave example PIO program.

Next, enter ``trace`` to execute the first instruction of the program.
This step will setup pin directions, and check the result with the
command ``gpio -p 0`` to see the pins at PIO0.

.. figure:: images/io-monitor-setup-pindirs.png
   :scale: 50 %
   :alt: Setup GPIO Pin Directions

   Setup GPIO Pin Directions

   Setup GPIO pin directions for use with the PIO program.

In another terminal window, we open a second instance of a monitor and
execute our ``ext-wave`` monitor script with the monitor command
``script -d -e ext-wave``.  The script will provide the external
signal on GPIO 23.  After startup, the script stops at the first
``wait`` command in expectation for the PIO program to arrive at clock
cycle 3.

.. figure:: images/io-monitor-external.png
   :scale: 50 %
   :alt: Start Monitor Script for Supplying External Signal

   Start Monitor Script for Supplying External Signal

   Starting the ``ext-wave`` monitor script will start the process of
   supplying an external signal.

Now, in our first monitor instance, we enter the command ``trace -g -p
0 -w 1000 -c 30`` to let the emulator perform 30 clock cycles in order
to continue execution of our PIO program for a while.  Option ``-w
1000`` will insert a delay of 1 second between clock cycles, such we
can easier follow what happens.  Options ``-g`` and ``-p 0`` will show
us the GPIO pins for each cycle as seen by PIO0.

.. figure:: images/io-monitor-sync.gif
   :scale: 50 %
   :alt: PIO Program Run With Synchronized External Signal Input

   PIO Program Run With Synchronized External Signal Input

   Executing 30 cycles of our PIO program ``squarewave`` while our
   ``ext-wave`` script provides external signal input.  One can see
   the perfect 2/3 time proportion between the toggling bit of GPIO 0
   (first, red column) that toggles every 2nd cycle, and the toggling
   bit of GPIO 23 (last green column in of the third group of columns)
   that toggles every 3nd cycle.

As we can see, the ``squarewave`` PIO program toggles GPIO pin 0 every
2nd cycle, while the synchronized external monitor script ``ext-wave``
toggles GPIO pin 23 every 3rd cycle.  In this example, there is, for
simplicity, no interaction between the external signal and the PIO
program.  But in a real-world example, the PIO program could read in
the bit that is provided by the external signal.

Conclusion
----------

We have seen how to provide an external signal to the GPIO pins and
keep it in sync with a PIO program, even if the PIO program is
debugged in single-step mode, just by implementing a monitor script
that supplies the external data at the expected pace.

Similarly, we could write a monitor script that e.g. writes data into
the PIO's FIFOs, and sync this data supply monitor script with the PIO
program in the same way as we have done it for the external signal.
This way, we can simulate the processor cores to deliver data to the
PIO.

Yet, writing data supply monitor scripts can be tedious work.  Future
plans for the PIO emulator contain ideas for providing a client
application that assists in creating data supply monitor scripts,
e.g. by graphically editing an external signal and generating a proper
monitor script.

Alternatively, a yet-to-be-written emulator client application also
could directly interface the emulator via the socket API / register
facade for supplying external data to the PIO at the correct pace,
rather than generating and running monitor scripts.
