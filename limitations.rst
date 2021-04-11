Limitations
===========

While the client-server architecture is powerful approach due to its
versatile application scenarios, it also reveals a major drawback:
Clients potentially compete for resources.  The probably most simple
approach conflicts is to use only one instance of a client for
modifying the emulator's state (i.e. a single Monitor instance), but
as many read-only clients as desired.

Example: Concurrent Instruction Memory Allocation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For example, no one prevents you from starting *two* instances of a
Monitor client, that both write program instructions into the same or
at least overlapping memory areas.  The Raspberry Pi foundation's Pico
C SDK provides special methods to *allocate* instruction memory, thus
preventing you from *accidentally* loading a program into a memory
area that is already in use.  Note that allocation is a feature of the
Pico C SDK, and not of the RP2040 itself.  This works well as long as
there is only a single instance of the Pico C SDK running, which
usually applies.

The RP2040 emulator provides its own Java SDK that provides methods
equivalent to the functions of the Pico C SDK (but limited to those
functions that are relevant for the emulation of the two PIOs).
Likewise, the Java SDK implements memory allocation also as a feature
that is bound to the Java SDK instance that is in use.  However, in a
multi-client environment, each client runs a Java SDK instance of its
own and within a JVM of its own.  That is, if you are running multiple
instances of the Monitor application, no monitor will know about the
allocation status of any other monitor.  Hence, protection against
accidental overwrite will work only within a single monitor instance,
but not across multiple monitors.

Similarly, if you are running a TimingDiagram and a Monitor in
parallel (which is basically ok), be aware that running a monitor
script from within the TimingDiagram will ignore any memory marked as
allocated in your Monitor instance (i.e. you may expect that the
TimingDiagram possibly overwrites your PIO program, even if it is
marked as allocated in the monitor).

Note that for the future, I may decide to implement PIO instruction
memory allocation as a feature of the emulator itself (rather than as
a feature of the SDK, as it is implemented at the moment).  In that
case, all monitor instances (and all other clients) would have access
to allocation information and thus could avoid accidental modification
of memory that is marked as allocated.  However, be aware, that memory
allocation is nevertheless designed as a safety feature rather than as
a security feature.  No one prevents a client from directly writing
instruction op-codes into memory area that is marked as allocated,
since the RP2040's register interface allows any client to overwrite
instruction op-codes at any time, regardless of any allocation marks.

Lost Updates
~~~~~~~~~~~~

Imagine one client modifies, say, the contents of one of the PIO's
FIFOs, and then does not further observe any modifications.  In the
meantime, another client may modifiy the same FIFO, without the first
client noticing the change (unless it actively checks for such
changes).  If the first client, assuming that the FIFO has not changed
in the meantime, applies further operations that depend on the FIFOs
contents, unexpected changes of the FIFOs may result in unexpected
behaviour of that client.

The emulator already provides a function waiting for a register's
value to change.  Using this function, a client may observe register
values that it depends on and thus properly react onto unexpected
changes.  However, the implementation of the wait function is
currently limited.  Registers are checked for modification only once
per clock cycle, but not for modifications that occur during a single
clock cycle.  Therefore, there is currently no reliable way of
observing registers if any changes must be granted to be recognized.
Currently, the best approach for a client is to regularly poll for
changes of register values that it relies on.

A future version of the register facade implementation may introduce a
feature for a client to retrieve and hold a lock on an arbitrary set
of registers and release the lock only after it has completed all
updates to these registers.  This way, modification of a set of
registers could be made an atomic operation from all client's point of
view.

Race Conditions
~~~~~~~~~~~~~~~

The implementation of the local register facade currently directly
accesses the PIOs' internal variables, rather than a copy made after
each clock cycles.  If a client happens to access a register while a
clock cycle is in progress, the client may see spurious data hazards.
For example, if multiple state machines are actively writing different
values to the same GPIO pin during the same clock cycle, finally one
state machine will eventually win, according to the ouput priority
rules as specified in the GPIO Mappings section of the RP2040
datasheet.  Currently the best approach to circumvent this flaw is to
follow the following rules:

* Ensure that only a single client triggers clock cycles.  In
  particular, do not run multiple instances of a monitor for
  simultaneously triggering clock cycles from different monitors.
* After triggering a clock cycle, the client should sleep for a short
  period (~1ms should be sufficient for a typical notebook or desktop
  environment, if the CPU is otherwise idle), thus giving the emulator
  enough time to fully execute the triggered instruction before the
  client inspects the results of the instruction that has been
  executed.
* Other clients should frequently poll for changes that they depend
  on, but should expect to see spurious hazards.

A future version of the emulator's implementation may work on a
duplicate set of internal registers, with one internal active set of
registers, and the other one exposed to the register interface, and
swapping between both register sets after each clock cycle.  This way,
no hazards resulting from internal operation will show up through the
register facade.

Summary
~~~~~~~

For safe operation of clients without unexpected behaviour, you are
advised to obey the following rules:

* Do not run multiple instances of the Monitor application at the same
  time against the same emulation server instance, unless you really
  know what you are doing.
* However, use as many read-only clients (*observers*) in parallel as
  you like, such as the GPIOObserver.  Though, in rare case and under
  special circumstances, they *might* show spurious value hazards.
* When concurrently running a Monitor and a TimingDiagram (which is
  basically fine), be aware that executing a monitor from within the
  TimingDiagram script will ignore your monitor's memory allocation
  marks and thus may unexpectedly overwrite your PIO instruction
  memory without any further warning.
* While the TimingDiagram executes a monitor script, do not
  concurrently perform any actions in a concurrently running Monitor.
