Download & Compile
==================

The RP2040 Emulator is published as open source under GPL v2 and
available on Github under the following URL [Reuter21a]_:
https://github.com/soundpaint/rp2040pio

Since no stable version 1.0 has not yet been released, I do not yet
provide pre-compiled binaries.  That is, as of now, you have to
compile all Java files by yourself.  Also, the build process itself is
still under development.  As of writing these lines, you roughly have
to proceed as follows.

Prerequisites
-------------

List of required software:

* Java OpenJDK 11.x (other recent versions should also work, but have
  not been tested)
* GNU Make
* Git

The emulator itself as well as currently all client applications are
written in Java.  My developing environment is a Ubuntu Linux system,
using ``openjdk`` version 11.0.x as Java JDK.  The build process is
currently based on ``GNU Make``.  For enhanced interoperability, I may
at some point in the future switch to either ``Ant`` or ``Maven`` or
``cmake`` (the Pico C SDK uses ``cmake`` as well), but this has not
yet been decided.  You also need ``Git`` to download the repository.

To summarize, for compiling I currently recommend a Unix / Linux
operating system with ``GNU Make`` and ``Java JDK 11``, though the
steps may also work with other environments.

Download
--------

Download the source repository from Github with the following steps:

* Open a Unix/Linux terminal window (or, on Windows, a Git bash
  (untested)).
* Change to whatever directory you want to contain the project tree of
  source files of the emulator.
* Clone the rpi2040pio Git repository from Github: ::

    git clone git@github.com:soundpaint/rp2040pio.git

Compile
-------

* Go to the project root directory of the repository that you just
  have cloned: ::

    cd rp2040pio

* Run the build process: ::

    make all

* If all went well, there should now be a new directory ``jar``: ::

    cd jar

* Now you should be able e.g. to start the emulation server: ::

    java -jar rp2040pio_server.jar

If anything went wrong when compiling, you may run ``make clean`` to
clean the repository, try to fix any errors (e.g. by upgrading to a
different JDK version) and try again with ``make all``.
