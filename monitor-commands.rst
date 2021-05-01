.. # WARNING: This sphinx documentation file was automatically
.. # created directly from documentation info in the source code.
.. # DO NOT CHANGE THIS FILE, since changes will be lost upon
.. # its next update.  Instead, change the info in the source code.
.. # This file was automatically created on:
.. # 2021-05-01T17:31:40.243736Z

Monitor & Control Program Commands Reference
============================================

The *Monitor & Control Program*, or in short,
just *monitor*, features a set of built-in
commands with integrated, self-documenting
help.  The following reference documentation
has been compiled from these sources.

.. _commands-overview:

Overview
--------

The monitor supports all of the commands
listed below.

.. csv-table::
   :header: Command, Short Description
   :widths: 20, 80

   ":ref:`breakpoints <breakpoints-command-label>`","change breakpoints"
   ":ref:`clear <clear-command-label>`","clear screen and optionally scrollback buffer"
   ":ref:`enable <enable-command-label>`","enable or disable state machine(s) or show if enabled"
   ":ref:`enter <enter-command-label>`","enter instruction opcodes; exit by entering an empty line"
   ":ref:`execute <execute-command-label>`","write instruction for immediate execution or display instruction currently executed"
   ":ref:`fifo <fifo-command-label>`","display or change internal state machine's FIFO status"
   ":ref:`gpio <gpio-command-label>`","display or change status of GPIO pins"
   ":ref:`help <help-command-label>`","list all available monitor commands"
   ":ref:`label <label-command-label>`","display a register's label"
   ":ref:`load <load-command-label>`","load program from file and mark affected PIO memory area as allocated"
   ":ref:`quit <quit-command-label>`","quit monitor"
   ":ref:`read <read-command-label>`","low-level read access to a register"
   ":ref:`registers <registers-command-label>`","display or change internal registers of a state machine"
   ":ref:`reset <reset-command-label>`","emulator full reset"
   ":ref:`save <save-command-label>`","save a selected range of a PIO's instruction memory to a file"
   ":ref:`script <script-command-label>`","load monitor script from file and execute it"
   ":ref:`sideset <sideset-command-label>`","display or control a state machine's side-set configuration"
   ":ref:`trace <trace-command-label>`","trace program by performing a number of clock cycles"
   ":ref:`unassemble <unassemble-command-label>`","unassemble program memory"
   ":ref:`unload <unload-command-label>`","zero PIO memory area for the specified program and unmark it as allocated"
   ":ref:`version <version-command-label>`","print emulator version"
   ":ref:`wait <wait-command-label>`","wait for a register's bits to match an expected value"
   ":ref:`wrap <wrap-command-label>`","display or control a state machine's wrap and wrap target configuration"
   ":ref:`write <write-command-label>`","low-level write access to a register"

.. _breakpoints-command-label:

breakpoints
-----------

**Usage**
^^^^^^^^^

breakpoints [OPTION]…

**Description**
^^^^^^^^^^^^^^^

change breakpoints

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -s, --sm=NUMBER (default: 0)
            SM number, one of 0, 1, 2 or 3
  -a, --add=ADDRESS (mandatory: no)
            add breakpoint at specified address (0x00…0x1f)
  -d, --delete=ADDRESS (mandatory: no)
            remove breakpoint from specified address (0x00…0x1f)
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

For displaying breakpoints, use the "unassemble" command.

:ref:`Back to Overview <commands-overview>`

.. _clear-command-label:

clear
-----

**Usage**
^^^^^^^^^

clear [OPTION]…

**Description**
^^^^^^^^^^^^^^^

clear screen and optionally scrollback buffer

**Options**
^^^^^^^^^^^

  -b, --buffer (default: off)
            also clear scrollback buffer
  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _enable-command-label:

enable
------

**Usage**
^^^^^^^^^

enable [OPTION]…

**Description**
^^^^^^^^^^^^^^^

enable or disable state machine(s) or show if enabled

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (mandatory: no)
            PIO number, either 0 or 1 or both, if undefined
  -s, --sm=NUMBER (mandatory: no)
            SM number, one of 0, 1, 2 or 3, or all, if undefined
  +e / -e, --enable (mandatory: no)
            enable or disable or show, if undefined
  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _enter-command-label:

enter
-----

**Usage**
^^^^^^^^^

enter [OPTION]…

**Description**
^^^^^^^^^^^^^^^

enter instruction opcodes; exit by entering an empty line

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -a, --address=ADDRESS (mandatory: no)
            start address (0x00…0x1f)
  -v, --value=NUMBER (mandatory: no)
            instruction op-code
  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _execute-command-label:

execute
-------

**Usage**
^^^^^^^^^

execute [OPTION]…

**Description**
^^^^^^^^^^^^^^^

write instruction for immediate execution or display instruction currently executed

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -s, --sm=NUMBER (default: 0)
            SM number, one of 0, 1, 2 or 3
  -i, --instruction=CODE (mandatory: no)
            opcode of instruction to be executed
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

Writes an instruction for immediate execution (including jumps)
and then resuming execution or displays the currently excuted
instruction.  Immediate execution means execution during the next
clock cycle.

Options -p and -s select the state machine that this command
applies to.  Default is PIO0 and SM0.

If option -i is not specified, the instruction currently being
executed by the selected state machine will be displayed.

If option -i is specified, the specified instruction is written
for immediate execution.

:ref:`Back to Overview <commands-overview>`

.. _fifo-command-label:

fifo
----

**Usage**
^^^^^^^^^

fifo [OPTION]…

**Description**
^^^^^^^^^^^^^^^

display or change internal state machine's FIFO status

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -s, --sm=NUMBER (default: 0)
            SM number, one of 0, 1, 2 or 3
  -a, --address=ADDRESS (mandatory: no)
            FIFO memory address (0x0…0x7) to write value into
  -v, --value=VALUE (mandatory: no)
            value to enqueue or directly write into FIFO memory
  -d, --dequeue (default: off)
            dequeue value from either RX or TX FIFO
  -e, --enqueue (default: off)
            enqueue value provided with option -v into either RX or TX FIFO
  -j, --join (default: off)
            let either RX or TX FIFO steal the other FIFO's storage
  -u, --unjoin (default: off)
            revoke join operation of either RX or TX FIFO
  -t, --tx (default: off)
            apply modification on TX FIFO
  -r, --rx (default: off)
            apply modification on RX FIFO
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

If none of the FIFO modification options is specified, the status
of the FIFO of the selected is displayed.
Option '-a' together with option '-v' can be used for directly
low-level write a value into one of the 8 FIFO's data registers.
Otherwise, for all specified modification options, the corresponding
modifications will be performed for the selected state machine and
the selected FIFO (either RX or TX).

:ref:`Back to Overview <commands-overview>`

.. _gpio-command-label:

gpio
----

**Usage**
^^^^^^^^^

gpio [OPTION]…

**Description**
^^^^^^^^^^^^^^^

display or change status of GPIO pins

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (mandatory: no)
            PIO number, either 0 or 1 or undefined
  -g, --gpio=NUMBER (mandatory: no)
            number of GPIO pin (0…31)
  -i, --init (default: off)
            initialize GPIO pin for use with the specified PIO
  -s, --set (default: off)
            set GPIO pin of the specified PIO
  -c, --clear (default: off)
            clear GPIO pin of the specified PIO
  -e, --enable (default: off)
            enable GPIO output of the specified PIO, setting direction to "out"
  -d, --disable (default: off)
            disable GPIO output of the specified PIO, setting direction to "in"
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

Each PIO has a set of local GPIO pins that, depending on the GPIO's
function selection settings, are propagated to the RP2040's GPIO
pins or not.  Use this command for displaying the RP2040's GPIO pins
after function selection, or as directly output by a specific PIO's
local GPIO pins.

Use one of options "-i", "-s", "-c", "-e", "-d", together
with option "-g", for either initializing a GPIO pin for a PIO, or
for clearing or setting its status or for specifying its pin
direction by enabling or disabling its output, respectively.
Use options "-p" and "-g" option to specify which PIO and GPIO
pin to apply the operation.

If none of options "-i", "-s", "-c", "-e", "-d" is
specified, the current status of all GPIO pins will be displayed,
depending on option "-p" for either of the PIOs or for the GPIO
after function selection.

:ref:`Back to Overview <commands-overview>`

.. _help-command-label:

help
----

**Usage**
^^^^^^^^^

help [OPTION]…

**Description**
^^^^^^^^^^^^^^^

list all available monitor commands

**Options**
^^^^^^^^^^^

  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _label-command-label:

label
-----

**Usage**
^^^^^^^^^

label [OPTION]…

**Description**
^^^^^^^^^^^^^^^

display a register's label

**Options**
^^^^^^^^^^^

  -a, --address=ADDRESS (mandatory: no)
            address (0x00000000…0xffffffff) of the register to display
  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _load-command-label:

load
----

**Usage**
^^^^^^^^^

load [OPTION]…

**Description**
^^^^^^^^^^^^^^^

load program from file and mark affected PIO memory area as allocated

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -l, --list (default: off)
            list names of available example hex dumps
  -s, --show=NAME (mandatory: no)
            name of built-in example hex dump to show
  -e, --example=NAME (mandatory: no)
            name of built-in example hex dump to load
  -f, --file=PATH (mandatory: no)
            path of hex dump file to load
  -a, --address=ADDRESS (mandatory: no)
            preferred program start address (0x00…0x1f)
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

The "load" command reads in the specified hex dump and stores it
as a PIO program in one of the two PIOs' instruction memory.
By convention, hex dump files have ".hex" file name suffix.

Built-in example hex dumps are available that can be listed with
the "-l" option.  To select any of the example hex dumps, use the
"-e" option and pass to this option the hex dump's name as shown
in the list of available built-in hex dumps.  To view a built-in hex
dump prior to loading it, use the "-s" option.
For user-provided hex dumps, use the "-f" option to specify the
file path of the hex dump, including the ".hex" file name suffix.
Note that tracking memory allocation is not a feature of the
RP2040, but local to this monitor instance, just to avoid
accidentally overwriting your own PIO programs.  Other applications
that concurrently access the RP2040 will therefore ignore
this instance's allocation tracking and may arbitrarily
overwrite allocated PIO memory, using their own allocation scheme.

Expected file format:
The program file to be loaded must be a regular text file with
either "\n" or "\r\n" line endings and UTF-8 encoding.
Other encodings may also work for the core instruction opcodes, but
may give unexpected results if meta information is relevant.
Empty lines are ignored.  Each non-empty line of the text file
must contain either meta information or an opcode.  A meta
information line starts with a leading '#' character and may
contain either a special directive, or,  if the '#' is followed by
a ';' character, an arbitrary user comment.  Each non-empty line that
is not a meta information line must contain a single opcode.  Each
opcode is a 32 bits integer and represented as a plain four-digit
hexadecimal value without leading "0x".  The maximum allowed number
of opcodes is 32.

:ref:`Back to Overview <commands-overview>`

.. _quit-command-label:

quit
----

**Usage**
^^^^^^^^^

quit [OPTION]…

**Description**
^^^^^^^^^^^^^^^

quit monitor

**Options**
^^^^^^^^^^^

  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _read-command-label:

read
----

**Usage**
^^^^^^^^^

read [OPTION]…

**Description**
^^^^^^^^^^^^^^^

low-level read access to a register

**Options**
^^^^^^^^^^^

  -a, --address=ADDRESS (mandatory: no)
            address (0x00000000…0xffffffff) of the register to access
  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _registers-command-label:

registers
---------

**Usage**
^^^^^^^^^

registers [OPTION]…

**Description**
^^^^^^^^^^^^^^^

display or change internal registers of a state machine

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -s, --sm=NUMBER (default: 0)
            SM number, one of 0, 1, 2 or 3
  -x, --x=VALUE (mandatory: no)
            set value of register X
  -y, --y=VALUE (mandatory: no)
            set value of register Y
  -i, --isr=VALUE (mandatory: no)
            set value of ISR register
  -k, --isrshiftcount=VALUE (mandatory: no)
            set value of ISR shift count register
  -o, --osr=VALUE (mandatory: no)
            set value of OSR register
  -q, --osrshiftcount=VALUE (mandatory: no)
            set value of OSR shift count register
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

If none of the register options is specified, the status of
all those registers is displayed.
Otherwise, for all specified register options, the corresponding
register is set to the specified value.

:ref:`Back to Overview <commands-overview>`

.. _reset-command-label:

reset
-----

**Usage**
^^^^^^^^^

reset [OPTION]…

**Description**
^^^^^^^^^^^^^^^

emulator full reset

**Options**
^^^^^^^^^^^

  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _save-command-label:

save
----

**Usage**
^^^^^^^^^

save [OPTION]…

**Description**
^^^^^^^^^^^^^^^

save a selected range of a PIO's instruction memory to a file

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -a, --start=ADDRESS (mandatory: no)
            first address (0x00…0x1f) of the program
  -s, --stop=ADDRESS (mandatory: no)
            last address (0x00…0x1f, inclusive) of the program
  -f, --file=PATH (mandatory: no)
            path of file to write
  -n, --name=NAME (mandatory: no)
            program name to be added as ".program"directive
  +o / -o, --overwrite (default: false)
            overwrite if file already exists
  +r / -r, --relocatable (default: true)
            true, if the PIO program may be loaded anywhere into instruction memory
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

The file is written as a text file, with each instruction
added as a line consisting of its operation code represented
as hexadecimal 32 bit integer value (without "0x" prefix).

If the specified stop address is lower than start address, then
the program is assumed to wrap from the highest memory address to
the first memory address.  Any configuration of a SM specific wrap
or wrap target is ignored.

If the file is specified to be not relocatable, a proper
".origin" directive will be added as a comment line.

If a program name is provided, it will be added as a
".program" directive in a separate comment line.

Comment lines start with the hash symbol "#".

:ref:`Back to Overview <commands-overview>`

.. _script-command-label:

script
------

**Usage**
^^^^^^^^^

script [OPTION]…

**Description**
^^^^^^^^^^^^^^^

load monitor script from file and execute it

**Options**
^^^^^^^^^^^

  -l, --list (default: off)
            list names of available example scripts
  -s, --show=NAME (mandatory: no)
            name of built-in example script to show
  -e, --example=NAME (mandatory: no)
            name of built-in example script to execute
  -f, --file=PATH (mandatory: no)
            path of monitor script file to execute
  +d / -d, --dry-run (default: true)
            dry-run the script commands rather than actually executing them
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

By convention, monitor scripts files have ".mon" file name suffix.
They contain commands to be executed verbatim as if they were
manually entered in exactly the same way.
For safety reasons as well as for providing for future extensions,
an additional flag "+d" is by default set to dry-run the script.
To actually run the script, you need to explicitly spcify "-d" to
override dry-run mode.

Some built-in example scripts are available that can be listed with
the "-l" option.  To execute a built-in script, use the "-e"
option and pass to this option the script's name as shown in the
list of available built-in scripts.
For user-provided script files, use the "-f" option to specify the
file path of the script, including the ".mon" file name suffix.

:ref:`Back to Overview <commands-overview>`

.. _sideset-command-label:

sideset
-------

**Usage**
^^^^^^^^^

sideset [OPTION]…

**Description**
^^^^^^^^^^^^^^^

display or control a state machine's side-set configuration

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -s, --sm=NUMBER (default: 0)
            SM number, one of 0, 1, 2 or 3
  -c, --count=COUNT (mandatory: no)
            number of side-set bits to be used (0…5)
  -b, --base=NUMBER (mandatory: no)
            base GPIO pin (0…31) number of side-set
  +o / -o, --opt (mandatory: no)
            make side <value> optional for instructions
  +d / -d, --pindirs (mandatory: no)
            apply side set values to the PINDIRs and not the PINs
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

Options -p and -s select the state machine that this command
applies to.  Default is PIO0 and SM0.

If none of the options -c, -b, ±o, ±d is specified, the currently
configured side-set of the selected state machine will be
displayed.  If at least one of the options -c, -b, ±o, ±d is
specified, the corresponding settings will be adjusted, while for
those not specified the corresponding settings will keep unmodified.

:ref:`Back to Overview <commands-overview>`

.. _trace-command-label:

trace
-----

**Usage**
^^^^^^^^^

trace [OPTION]…

**Description**
^^^^^^^^^^^^^^^

trace program by performing a number of clock cycles

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (mandatory: no)
            limit options -l and -i to PIO number, either 0 or 1 or both, if undefined
  -s, --sm=NUMBER (mandatory: no)
            limit option -i to SM number, one of 0, 1, 2 or 3, or all, if undefined
  -c, --cycles=COUNT (default: 1)
            number of cycles to apply
  -i, --show-instr (default: off)
            show address of instruction pointer (aka PC reg) for selected SMs of selected PIOs
  -l, --show-local-gpio (default: off)
            show status of (local PIO's) GPIO pins
  -g, --show-gpio (default: off)
            show status of (global) GPIO pins
  -w, --wait=NUMBER (default: 0)
            before each cycle, sleep for the specified time [ms] or until interrupted
  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _unassemble-command-label:

unassemble
----------

**Usage**
^^^^^^^^^

unassemble [OPTION]…

**Description**
^^^^^^^^^^^^^^^

unassemble program memory

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -s, --sm=NUMBER (default: 0)
            SM number, one of 0, 1, 2 or 3
  -a, --address=ADDRESS (default: 0)
            start address (0x00…0x1f)
  -c, --count=COUNT (default: 32)
            number of instructions to unassemble
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

Memory locations marked as allocated are prefixed with leading 'X'.

Note that tracking memory allocation is not a feature of the
RP2040, but local to this monitor instance, just to avoid
accidentally overwriting your own PIO programs.  Other applications
that concurrently access the RP2040 will therefore ignore
this instance's allocation tracking and may arbitrarily
overwrite allocated PIO memory, using their own allocation scheme.

Note that the same PIO program may unassemble to differently
displayed instructions for different state machines, since
some settings specific to a particular state machine, such as
side-set count, will affect interpretation of op-codes.
Therefore, the unassemble command supports the "sm" argument
for displaying the instructions as interpreted by the selected
state machine, according to its current settings.

:ref:`Back to Overview <commands-overview>`

.. _unload-command-label:

unload
------

**Usage**
^^^^^^^^^

unload [OPTION]…

**Description**
^^^^^^^^^^^^^^^

zero PIO memory area for the specified program and unmark it as allocated

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -l, --list (default: off)
            list names of available example hex dumps
  -s, --show=NAME (mandatory: no)
            name of example hex dump to show
  -e, --example=NAME (mandatory: no)
            name of example hex dump to unload
  -f, --file=STRING (mandatory: no)
            path of hex dump file to unload
  -a, --address=ADDRESS (mandatory: no)
            start address (0x00…0x1f) of the area to free
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

The "unload" command first reads in the specified hex dump in order
to determine the program length of the corresponding PIO program.
Then, the identified instruction memory area that is associated with
the PIO program in the specified PIO will be zeroed, and any memory
allocation marks found in this memory area will be removed.

Built-in example hex dumps are available that can be listed with
the "-l" option.  To select any of the example hex dumps, use the
"-e" option and pass to this option the hex dump's name as shown
in the list of available built-in hex dumps.  To view a built-in hex
dump prior to unloading it, use the "-s" option.
For user-provided hex dumps, use the "-f" option to specify the
file path of the hex dump, including the ".hex" file name suffix.
Note that tracking memory allocation is not a feature of the
RP2040, but local to this monitor instance, just to avoid
accidentally overwriting your own PIO programs.  Other applications
that concurrently access the RP2040 will therefore ignore
this instance's allocation tracking and may arbitrarily
overwrite allocated PIO memory, using their own allocation scheme.

For information about the expected file format, enter the command
"load -h" to view the help information of the "load" command.

:ref:`Back to Overview <commands-overview>`

.. _version-command-label:

version
-------

**Usage**
^^^^^^^^^

version [OPTION]…

**Description**
^^^^^^^^^^^^^^^

print emulator version

**Options**
^^^^^^^^^^^

  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _wait-command-label:

wait
----

**Usage**
^^^^^^^^^

wait [OPTION]…

**Description**
^^^^^^^^^^^^^^^

wait for a register's bits to match an expected value

**Options**
^^^^^^^^^^^

  -a, --address=ADDRESS (mandatory: no)
            address (0x00000000…0xffffffff) of the register to observe
  -v, --value=VALUE (mandatory: no)
            expected value to match
  -m, --mask=MASK (default: -1)
            bit mask to select bits to match
  -c, --cycles=COUNT (default: 0)
            timeout after <COUNT> cycles or no timeout, if 0
  -t, --time=COUNT (default: 100000)
            timeout after <COUNT> millis or no timeout, if 0
  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

.. _wrap-command-label:

wrap
----

**Usage**
^^^^^^^^^

wrap [OPTION]…

**Description**
^^^^^^^^^^^^^^^

display or control a state machine's wrap and wrap target configuration

**Options**
^^^^^^^^^^^

  -p, --pio=NUMBER (default: 0)
            PIO number, either 0 or 1
  -s, --sm=NUMBER (default: 0)
            SM number, one of 0, 1, 2 or 3
  -w, --wrap=ADDRESS (mandatory: no)
            wrap (WRAP_TOP) address (0x00…0x1f)
  -t, --target=ADDRESS (mandatory: no)
            wrap target (WRAP_BOTTOM) address (0x00…0x1f)
  -h, --help (default: off)
            display this help text and exit

**Notes**
^^^^^^^^^

Options -p and -s select the state machine that this command
applies to.  Default is PIO0 and SM0.

If none of the options -w, -t is specified, the currently
configured wrap and wrap target of the selected state machine will be
displayed.  If at least one of the options -w, -t is
specified, the corresponding settings will be adjusted, while for
those not specified the corresponding settings will keep unmodified.

:ref:`Back to Overview <commands-overview>`

.. _write-command-label:

write
-----

**Usage**
^^^^^^^^^

write [OPTION]…

**Description**
^^^^^^^^^^^^^^^

low-level write access to a register

**Options**
^^^^^^^^^^^

  -a, --address=ADDRESS (mandatory: no)
            address (0x00000000…0xffffffff) of the register to access
  -v, --value=VALUE (mandatory: no)
            value to write
  -h, --help (default: off)
            display this help text and exit

:ref:`Back to Overview <commands-overview>`

