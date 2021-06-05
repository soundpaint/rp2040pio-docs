.. _section-top_emulation-server:

Emulation Server
================

While some of the emulation client applications can be run isolated
with a local emulation server of their own, the client / server
architecture develops its full usefulness only when all clients share
the same emulation server.

Starting the Server
-------------------

To start the server, envoke the ``java`` runtime (JDK or JRE) with
option ``-jar`` and followed by the file path of the
``rp2040pio_server.jar`` emulation server Jar file.  Depending on your
operating system and version, you may have a file explorer that
directly lets you either double-click on the Jar file or right-click
on it to start it with a Java runtime.  This approach may work, but
possibly, you will not see any warnings or confirmation messages that
the server emits to its standard output device.  Therefore, it is
highly recommended to start the server through a terminal:

* Open a terminal window.
* Ensure your ``PATH`` variables are properly set such that you can
  envoke the ``Java`` runtime or development kit.
* Use the command ``cd`` to go to the directory that contains the file
  ``rp2040pio_server.jar``.
* Enter the following command to start an instance of the emulation
  server:

::

  java -jar rp2040pio_server.jar

You should now see a short confirmation message, including the port
number that the server opens for communication with the emulator
instance that it just has been created.

::

   $ java -jar jar/rp2040pio_server.jar
   Emulation Server Daemon
   RP2040 PIO Emulator Version 0.1 / jvm 11.0.11 / 55.0
   Copyright © 2021 by Jürgen Reuter, Karlsruhe, Germany.

   This software comes with ABSOLUTELY NO WARRANTY;
   for details please look at the license file that you
   should have received together with this software.
   This is free software, and you are welcome to
   redistribute it under certain conditions;
   for details please look at the license file that you
   should have received together with this software.

   started emulation server at port 2040

If you try to start another instance of the emulation server in
another terminal window, you will get the following message: ::

  failed starting emulation server: Address already in use (Bind
  failed)

You will get this message, because the same port can not be shared
among different servers.  By default, the emulation server uses port
``2040`` as default, but you are free to use any other port number in
the range from ``1`` to ``65535``.  If on your system, port 2040 is
for some reason already in use or, for whatever reason else, you want
to use a different port, just envoke the server with the ``-p`` option
to specify an alternative port: ::

   java -jar rp2040pio_server.jar -p 2041

.. note::

  On most operating systems, for using port numbers in the range ``1``
  to ``1023``, you will need ``root`` or ``administrator`` access
  rights.  If you try anyway, you may get the following message: ::

    failed starting emulation server:
    Permission denied (Bind failed)

  In this case, just choose a different port number above ``1023``.

Leave the terminal window open while using the emulator (you can
minimize the window, but you should not close it).  The window may
show help warning or confirmation messages.  Depending on your
operating system, closing the terminal window may also kill the server
process, such that the emulation will be shut down.

Shutting Down
-------------

When finished with your emulator session, you may safely kill the
server process in order to shut down the emulation server.  For doing
so, on most operating system, just press ``CTRL-C`` in the terminal
window to stop the server process.  After that, you can safely close
the terminal window.
