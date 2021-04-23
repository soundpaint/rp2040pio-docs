The Emulation Server's Socket API
=================================

Knowledge about the emulation server's socket API is essential for
third-party developers who want to

* provide language bindings for writing clients in languages
  other than Java, or

* develop client applications that will have to communicate with the
  emulator, if the client is to be implemented in a language other
  than Java.

For client applications written in the C / C++ language, a language
binding will be provided presumably within the next two or three
months as of writing these lines.

Overview
--------

As outlined in Sect. :ref:`Architecture Section
<section-top_architecture>`, the emulator exposes access to all its
register facade via the *RegisterServer* as a TCP/IP socket service.
The API of this socket service is essential for third-party developers
writing client applications.  Java developers may directly build their
applications on top of the *RegisterClient* class that implements the
*Registers* interface, or even use the Java SDK which itself may be
run on top of the RegisterClient.  However, when developing client
applications for the emulator in other languages, the API of the
TCP/IP socket is the point of access to go for, since the socket API
can be used from any language that can talk with TCP/IP sockets.

.. warning::

  The emulation server's socket API is not yet considered stable and
  may change until release of the first stable version of the
  emulator.  In particular, support for grouping multiple operations
  as a critical section to be executed without other clients
  interfering, will be added by providing a yet to be implemented
  locking mechanism.  This change may or may not affect semantics of
  already existing functionality.

Example Session
---------------

Before diving into a formal specification of the socket API, we
demonstrate use of the emulator via a socket by manually communicating
via a socket.  Please keep in mind that the emulator's socket has not
designed with humans as end-users as target, but rather for use by
client software.  We manually talk to the emulator via the socket API
solely for demonstration purposes.

Assuming that an instance of the emulator has been started for port
address ``2040``, we open a terminal window and use the telnet client
application to connect to the server and establish a TCP/IP
session. ::

  $ telnet localhost 2040
  Trying 127.0.0.1...
  Connected to localhost.
  Escape character is '^]'.

Now, that we have established the TCP/IP connection, we may enter the
command ``h`` (*help*) to get a list of available command. ::

  h
  101 OK: available commands:
  h                    (help)
  v                    (version)
  q                    (quit)
  r <addr>             (read address)
  w <addr> <value>     (write address)
  i <addr> <value> [<mask> [<timeout cycles> [<timeout millis>]]]
                       (await value)
  l <addr>             (show address label)
  p <addr>             (check address validity)

The server responds with response status ``101 OK``, and, after the
``:`` delimiter, with a result (message body) of our request.  In this
case, we get a list of available commands, one by one on each line of
the message body.

Next, we check for the version of the server. ::

  v
  101 OK: RP2040 PIO Emulator Version 0.1 / Linux 4.15.0-139-generic

The emulator responds with version identifier ``RP2040 PIO Emulator
Version 0.1`` and, if available, after the ``/`` delimiter, some more
information about the client that it is running on, such as its
operating system, if that could be somehow relevant for the client.

Next, we try to read data from a register by passing an address
(remember, that the RP2040 uses memory-mapped I/O, such that register
is uniquely assigned to a specific address).  We deliberately choose
an address that is *not* one of the valid registers. ::

  r 0
  405 IO: read from unsupported address: 00000000
  Connection closed by foreign host.

The server detects the invalid request, observes that the client is
doing something completely wrong, and therefore decides to close the
connection (but nevertheless gives us a hint what was wrong with this
request).  So, let's connect to the server again with ``telnet
localhost 2040`` and this time try to read a valid address.  For a
retrospective view, first let us double-check that address 0 was
inavlid by querying it the emulator provides this address. ::

  p 0
  101 OK: false

Ok, we are told that 0 is not among the addresses that the emulator
provides.  A look into the `RP2040 datasheet
<https://datasheets.raspberrypi.org/rp2040/rp2040-datasheet.pdf>`_,
Sect. 2.2.2 (*Detail* of \[*Address Map*] provides us with address
``0x50200000`` as the base address of ``PIO0`` (*PIO0_BASE*).
Sect. 3.7 lists all registers of the PIO, with addresses given
relative to the PIO's base address.  Let's choose register
``SM0_CLKDIV`` at the relative address ``0x0c8``, thus resulting in
the absolute address ``0x502000c8``.  First, let us double-check if we
caught the correct address by checking for the label for this address.
By the way, note that integer values are by default decimal, but a
leading ``0x`` indicates hexadecimal value. ::

  l 0x502000c8
  101 OK: SM0_CLKDIV

Ok, the server responds with the label that we expected.  So, now let
us read the current value of this register. ::

  r 0x502000c8
  101 OK: 65536

Since we just have started the emulator, this value is, as you can
double-check against the RP2040, actually this register's reset value.
Now let us update this register by writing th value 769. ::

  w 0x502000c8 769
  101 OK

And check, if the value was indeed stored. ::

  r 0x502000c8
  101 OK: 768

Why do we get ``768`` instead of ``769``?  If you carefully look into
the RP2040 datasheet, you will see, that the lower 8 bits of this
register are marked as ``reserved``.  In fact, the PIO emulator just
ignores the lower eight bits.  Specifically, written as binary value,
``769`` equals ``0b1100000001``.  Ignoring the lowermost 8 bits means
that the emulator will recognize the value as ``0b1100000000``, which
equals ``768``.

The socket API also provides the command ``i`` for *waiting* for a
specific register to change, though this feature is currently still
experimental, and precise semantics are subject to change.

We finally close the connection to the server with the command
``q``. ::

  q
  Connection closed by foreign host.

Request Syntax
--------------

The syntax of a request to a socket is specified with the following
grammar.

.. productionlist::
  request          : help-request | version-request |
                   : quit-request | read-request |
                   : write-request | await-request |
                   : label-request | provides-request .
  help-request     : 'h' .
  version-request  : 'v' .
  quit-request     : 'q' .
  read-request     : 'r' address .
  write-request    : 'w' address reg-value .
  await-request    : 'i' address reg-value [ mask [
                   :   timeout-cycles [ timeout-millis ]
                   : ] ] .
  label-request    : 'l' address .
  provides-request : 'p' address .
  address          : <int32> .
  reg-value        : <int32> .
  mask             : <int32> .
  timeout-cycles   : <int32> .
  timeout-millis   : <int32> .

``<int32>`` denotes a 32 bit integer value, denoted either as decimal
value, or as hexadecimal value, when preceded with ``0x``, and
interpreted as unsigned 32 bit value (i.e. decimal value -1 is
interpreted as 2^{32}-1 or ``0xffffffff``).

Response Syntax
---------------

The syntax of a response from the socket is specified with the
following grammar.

.. productionlist::
  response            : response-status [ ':' response-body ] .
  response-status     : status-code status-display-name .
  status-code         : <int32> .
  status-display-name : <simple-string> .
  response-body       : <string> .

A ``<simple-string>`` is a string with limited character set.
Specifically, it may not contain the character ``:``, since that
character is used as delimiter between the response status and the
response body.

Security Considerations
-----------------------

By default, sockets made available by a server are accessible for any
process owned by any user on the local host and even from a remote
host.  Typically, standard configuration of a host's firewall will
limit access to processes running on the local host.  The emulator is
expected to run in a trusted environment.  The emulator itself
interacts only with emulator client applications and may log
extraordinary events to its console.  That is, in the worst case, a
malicious emulator client application may compromise the emulator's
behavior as seen from other emulator client applications and may cause
increased amount of logging activity.  In general, client applications
always should expect other clients to affect the emulators behavior in
an unexpected way.  Client applications should not assume to have
exclusive access rights to the emulation server.

A future implementation of the RegisterServer may decide to introduce
some authorization scheme and use secure socket layer (SSL) as
underlying transport layer protocol.
