.. _section-top_gpio-observer:

GPIO Observer
=============

The *GPIO Observer*' displays the current status of all of the
emulator's 32 GPIO pins from either a PIO's or an external point of
perspective.

The application is available as Jar file and can be executed from the
command line via ::

  java -jar rp2040pio_gpioobserver.jar

with optional paramater ``-p`` to specify the server port to connect
to.  Again, like as for the server, the default port is ``2040``, if
not specified on the command line.

.. figure:: images/gpio-observer.png
   :scale: 80%
   :alt: GPIO Observer Application

   GPIO Observer Application

   The GPIO Observer visualizes the current state of all GPIO pins as
   seen either from a PIO's or from an external point of view.

PIO vs. GPIO View
-----------------

Since both PIOs share the same 32 GPIO pins, a PIO's view of its local
management of GPIO pins may differ from the state of GPIO pins as seen
from outside of the chip.  Therefore, the GPIO Observer offers two
different views:

* a selected PIO's view on the GPIO pins, and
* the actual GPIO's view as seen from outside.

For selection of the PIO, the former view features two radio buttons.

When debugging PIO programs running a single PIO, while the other PIO
does not make use of any GPIO pin, both views are typically identical.
However, if there _is_ some difference, it may indicate a setup
problem (such as forgetting to initally assign a GPIO pin to a
specific PIO).  Therefore, by default, both views are displayed, but
can be collapsed by clicking on the ``⊟`` symbol, if not needed.  When
in collapsed state, the view can be expanded again by clicking on the
``⊞`` symbol that will be appear instead.

Override
--------

The RP2040's GPIO section itself has a feature called _override_ that
supports further manipulation of each individual GPIO pin, such as
inverting its incoming or outgoing value or overriding the pin to
stick to a constant value.  Inverting is useful e.g. when a physical
low level of voltage is associated with logical high value and vice
versa.  Sticking to a constant value can be useful e.g. for
temporarily disabling a signal.  By default, override does nothing,
but just lets pass all signals unmodified.

The ``GPIO View of GPIO Pins`` panel provides radio buttons to choose
whether to display the pins' state _before_ or _after_ override.
Since, by default, the override feature will pass all signals
unmodified, both views usually look identical, unless override has
been explicitly configured to modify the signal of specific GPIO pins.

Pin View
--------

For each GPIO pin, the application displays the pin's current pad
value and pin direction with an LED-like symbol.  If a GPIO pin is
programmed as input, it will be displayed as a green LED.  If a GPIO
pin is programmed as output, it will be displayed as a red LED.  If
the bit value of the pin is logical 1, it will be displayed with light
color.  If it is logical 0, it will be displayed with dark color.

Refresh
-------

The display is regularly refreshed.  Currently, refresh is implemented
by active polling in regular time intervals with a default interval of
100ms.  The length of this interval can be overridden by passing the
``-r`` command-line option to the application: ::

  java -jar rp2040pio_gpioobserver.jar -r 1000

will, for example, set the refresh interval to 1000ms (that is, to a
second).

A future implementation may be based on a push model via client
notification for saving CPU resources, as compared to the current
polling.

The GPIO Observer is, as the name already suggests, implemented as a
read-only client.  That is, it uses the emulation server only for
read-access of RP2040 registers, but does not do any write access.  As
such, the this client does not compete with any other clients.  In
fact, other clients will not notice presence of this client; it
operation keeps transparent.
