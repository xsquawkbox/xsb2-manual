Getting Started
***************

Before you Begin
================

Before you download and install XSquawkBox 2, you should prepare your X-Plane
installation and ensure your system meets the requirements.

Also, if you haven't already done so, you should read through the VATSIM
terms & conditions, and register yourself an account.

System Requirements
-------------------

As of XSquawkBox 2.0beta3, XSquawkBox requires X-Plane 10.51+ or 11.36+ and one
of:

 - An X-Plane supported Mac running OS X 10.9 or newer
 
 - A PC running an X-Plane supported version of 64-bit Windows with suitable 
   graphics hardware

 - A PC running an X-Plane supported version of 64-bit Linux with suitable
   graphics hardware

If in doubt, about X-Plane support, please check the official 
`X-Plane 10 System Requirements`_ or `X-Plane 11 System Requirements`_ as
appropriate.

.. _X-Plane 10 System Requirements: http://www.x-plane.com/?article=x-plane-10-system-requirements
.. _X-Plane 11 System Requirements: http://www.x-plane.com/kb/x-plane-11-system-requirements/

If your X-Plane is a supported version, but not a supported release, please
follow the official instructions for `updating X-Plane 10`_ or 
`updating X-Plane 11`_ prior to installing XSquawkBox.

.. _updating X-Plane 10: https://www.x-plane.com/kb/updating-x-plane/
.. _updating X-Plane 11: https://www.x-plane.com/kb/updating-x-plane-11/

A note about macOS 10.15
^^^^^^^^^^^^^^^^^^^^^^^^

Due to changes in the GateKeeper proection system, macOS 10.15 (Catalina) will
not load the XSquawkBox plugin without you either:

* Explicitly authorising the plugin to load after it has failed once

* Disabling Gatekeeper completely

This is a limitation currently created by Apple's changes in macOS 10.15 and how
they affect existing software and consequentially, is outside of the ability of
the XSquawkBox developers to remedy.

Also note Laminar's position on macOS Catalina:

    "If your X-Plane 11 setup is heavily enhanced with add-ons, you may want
    to remain with Mojave."

    -- From the X-Plane Knowledge-base Article, `macOS Catalina & X-Plane`_ - 2019 Nov 18

.. _macOS Catalina & X-Plane: https://www.x-plane.com/kb/macos-catalina-x-plane/

As macOS 10.15 isn't compatible with 32-bit applcations, and X-Plane 10's 
support tools are 32-bit only, we cannot recommend you try to run XSquawkBox on
macOS 10.15 with X-Plane 10 either.

X-Plane Performance Requirements
--------------------------------
In addition to the basic requirements, you must configure your X-Plane to run in
real-time, that is, to have a framerate safely exceeding 20 frames per second in
all phases of operation.

.. admonition:: Further Information

   The 20 frames per second minimum `comes from X-Plane itself <https://www.x-plane.com/kb/the-simulators-measurement-of-time-is-slow/>`_
   and is a consequence of it's design.

Laminar Software maintains documentation on how to set the rendering options
correctly for 
`X-Plane 10 <https://www.x-plane.com/kb/setting-the-rendering-options-for-best-performance/>`_
and for
`X-Plane 11 <https://www.x-plane.com/manuals/desktop/#settingtherenderingoptionsforbestperformance>`_.

.. WARNING::

   If you do not configure X-Plane to achieve a minimum of 20 frames per second
   reliably in flight and on the ground, you may be disconnected automatically
   to prevent you from inconveniencing other pilots and controllers.

   That is, your frame rate should not regularly dip below 20fps for more than
   one or two frames, and should not sit, even marginally, below 20fps for
   any sustained period of time.

.. TIP::

   In the developer's experience, the phases of flight that cause the most 
   problems with frame-rates are those on the ground and on approach at low
   altitude, where the scenery rendering demands are at their highest.

   You should not optimise your simulator for framerate in the cruise at the
   expense of performance during those phases.

Plugin Compatibility
--------------------

As the underlying `libxplanemp <https://github.com/kuroneko/libxplanemp>`_
traffic rendering code was never intended to be loaded and operated concurrently
by multiple plugins at once,  XSquawkBox will conflict with any plugin that
uses it, or similar methods, to control traffic depiction inside the simulator.

The usual outcome of these conflicts is that one or more plugins will not be
able to inject TCAS information, or XSquawkBox will not be able to use its
ACF traffic rendering options.

If you wish to use these plugins, you should move XSquawkBox's folder out of 
your plugin folder when you're not using it, and similarly, you should move
conflicting plugins out of your plugin folder when you intend to use XSquawkBox.
If you do not do this, the developers cannot provide support for any issues
that may arise.

.. WARNING::

   It is NOT sufficient to use the X-Plane plugin manager to disable conflicting
   plugins as that happens well after simulator load.  They must not be
   installed together in order to prevent conflicts **during** simulator load.

Plugins that are known or assumed to cause related conflicts are:

* X-Ivap

* XSwiftBus (the Swift X-Plane interface)

* The PilotEdge client

* X-Pilot

* LiveTraffic

.. admonition:: Further Information

   XSquawkBox does not and will not support the concurrent injection of traffic
   from multiple sources.

   Such behaviour, if permitted, would create severe difficulties for
   controllers in sequencing and separating you as they would have to account
   for "phantom" aircraft they cannot see.
   
   Do not contact the developers about this.

Installing XSquawkBox
=====================

Installing the Plugin
---------------------

XSquawkBox is distributed as a Zip-file that contains the XSquawkBox plugin for
all three platforms (Windows, macOS and Linux), and a minimum set of resources
to use XSquawkBox.

To install the plugin:

1. Ensure that X-Plane is not running.

2. Locate your X-Plane installation folder, then open the subfolder "Resources",
   then "Plugins".

3. Open or unzip the distribution zipfile, and then move the "XSquawkBox" folder
   from the XSquawkBox distribution into the Plugins folder.

Once this has been done, when you start up X-Plane and start a flight, you 
should see a "XSquawkBox" menu item in the plugins menu.

If the menu item is missing, please see the section on
:ref:`troubleshooting plugin loading issues <troubleshooting-load>`

Configuring XSquawkBox
----------------------

.. TIP::

   XSquawkBox 2 is significantly different to previous versions in this regard.

   Even if you have previous experience with XSquawkBox, it is highly 
   recommended you work through this section to ensure your key and button
   bindings are all set appropriately.

