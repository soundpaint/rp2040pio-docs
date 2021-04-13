Overview
========

In a typical development / debugging session, one will begin with
starting a server instance.  Next, a monitor instance can be used to
load, modify, trace and save PIO programs and inspect the current
state of all state machines or any other parts of the emulator.  For
continuously observing the state of registers, entering register
queries over and over again on the monitor's command line is tedious
work.  Therefore, there are specialized client applications such as
for example the GPIO Observer, that continously visualizes the current
state of GPIO pins without further need for interaction.  These
additional visual tools are highly useful add-ons that can be run in
parallel with the monitor.
