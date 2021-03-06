Getting Started
***************

Before you Begin
================

Before you download and install XSquawkBox 2, you should prepare your X-Plane
installation and ensure your system meets the requirements.

Also, if you haven't already done so, you should read through the VATSIM
terms & conditions, and register yourself an account.

On System Support
-----------------

In this manual, we'll use two terms - "support" and "compatibility" - when
talking about requirements and interoperability.

Support reflects our ability to accomodate issues - if something is supported,
we will try to fix it once we have enough information on how to address the 
issue.  If it's not supported, we're not saying that it can't work - we're just
saying that if it doesn't work, we won't invest effort into making it work.

Compatibility reflects if the components can or can't work together.  If we
state something is compatible, we expect it to work.  If it's compatible and 
supported, we will actively endevour to correct any issues preventing it from 
working.  If we state that it is incompatible, then we expect that the 
components will not work together.

Please do not report issues that relate to things that are clearly noted
as being unsupported or incompatible.

System Requirements
-------------------

As of XSquawkBox 2.0, XSquawkBox requires X-Plane 10.51+ or 11.36+ and one
of:

 - An X-Plane supported Mac running macOS 10.12 or newer.
   (If you're using macOS 10.14 or 10.15, please see the compatibility note below).
 
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

Versions of X-Plane older than the versions stated above are incompatible.

XSquawkBox 2.0 is unsupported with the upcoming Vulkan renderer.  (A future
version of XSquawkBox will address this).

A note about macOS 10.14 and newer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Our ability to support macOS 10.14 is highly limited due to the introduction of
the Audio permissions system.  If the issue cannot be reproduced on 10.15, we
cannot support it at this time.

Further, As macOS 10.15 isn't compatible with 32-bit applcations, and 
X-Plane 10's support tools are 32-bit only, we cannot recommend you try to run
XSquawkBox on macOS 10.15 with X-Plane 10 either.

For this reason, XSquawkBox is unsupported with X-Plane 10 on macOS 10.14 or
10.15 - we have made no efforts to prevent it from working, but we will not act
on bug reports for X-Plane 10 related issues on these versions of macOS.

On macOS 10.15 (or newer), X-Plane 11.41 (or newer) is **required** for 
microphone support to work at all.  All versions of X-Plane 11 prior to 11.41
are incompatible when used on macOS 10.14 or 10.15.

.. WARNING::

   When using XSquawkBox on macOS 10.14 or newer, you should ensure that you 
   have your Security & Privacy settings set to enable apps from Identified
   Developers.

   The XSquawkBox team cannot provide support for problems created by having
   your application restrictions set too high.

On Releases and Updates
-----------------------

All XSquawkBox releases are only made through the `XSquawkBox website
<http://xsb.xsquawkbox.net/>`_.  There is no automatic updater so you should 
check the website regularly for news of known issues or upcoming updates.

.. TIP:: 

   XSquawkBox operates a twitter account (@xsquawkbox) which only contain tweets
   about new articles on the website (such as development news, known issue
   notices or release notifications).  This is a conveniant way to monitor for
   XSquawkBox news without having to visit the site regularly.

   We're open to using other methods we can integrate with our website as well!

We have two types of release:

 * Stable, which are versions we expect to continue to work for a prolonged
   period

 * Beta, which include new features which require testing before being declared
   stable.

Betas operate on a time limited basis and will automatically expire after a
certain date which will be indicated in the ``README`` file included with the 
release.

Sometimes we screw up with our release process and need to supply a new build
to address a compatibility issue - these are released as "hotfixes".

Hotfixes never include new features or changes to XSquawkBox itself - they're
always due to needing to change settings in our build system, either against
XSquawkBox or one of it's dependencies.  If you have an older version of a 
hotfixed release (e.g: You've got 2.0b4 and 2.0b4 hotfix 1 is out), and aren't
experiencing any problems with it, then there's usually no need to update to the
newer hotfix.

X-Plane Performance Requirements
--------------------------------
In addition to the basic requirements, you must configure your X-Plane
installation to run in real-time, that is, to have a framerate safely exceeding
20 frames per second in all phases of operation.  The 20 frames per second
minimum `comes from X-Plane itself <https://www.x-plane.com/kb/the-simulators-measurement-of-time-is-slow/>`_
and is a consequence of it's design.

Laminar Software maintains documentation on how to set the rendering options
correctly for 
`X-Plane 10 <https://www.x-plane.com/kb/setting-the-rendering-options-for-best-performance/>`_
and for
`X-Plane 11 <https://www.x-plane.com/manuals/desktop/#settingtherenderingoptionsforbestperformance>`_.

In multi-system X-Plane setups, this restriction only applies to the system 
running the flight model.

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

   The injection of traffic from multiple source is not supported by XSquawkBox
   and never will be.

   Such behaviour, if permitted, would create severe difficulties for
   controllers in sequencing and separating you as they would have to account
   for "phantom" aircraft they cannot see.

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

.. NOTE::

   Do not attempt to directly open the `.xpl` files - you only need to put these
   in the right location and X-Plane will load them automatically.

Once this has been done, when you start up X-Plane and start a flight, you 
should see a "XSquawkBox" menu item in the plugins menu.

If the menu item is missing, please see the section on
:ref:`troubleshooting plugin loading issues <troubleshooting-load>`

Configuring your Operating System
---------------------------------

To ensure that XSquawkBox can acquire your microphone at the correct sampling
rate, on Windows and macOS, it can be necessary to change the OS default
capture settings.  Please refer to the section in troubleshooting on 
:ref:`input visibility issues <troubleshooting-audio-devices>`.


Configuring XSquawkBox
======================

.. TIP::

   XSquawkBox 2 is significantly different to previous versions in this regard.

   Even if you have previous experience with XSquawkBox, it is highly 
   recommended you work through this section to ensure your key and button
   bindings are all set appropriately.

Configuring the keyboard commands
---------------------------------

Unlike previous releases of XSquawkBox, XSquawkBox 2.0 uses the X-Plane keyboard
and joystick binding system for its commands.

If you are not familiar with how to set up keyboard bindings in X-Plane, you can
refer to the manual for 
`X-Plane 10 <https://www.x-plane.com/manuals/desktop/10/index.html#configuringkeyboardshortcuts>`_ and
`X-Plane 11 <https://www.x-plane.com/manuals/desktop/index.html#configuringkeyboardshortcuts>`_ .

The commands available are detailed below:

+-------------------------------------------+------------------------------------+------------------------------------------------+
| Command Name                              | Display Name (X-Plane 11)          | Purpose                                        |
+===========================================+====================================+================================================+
| ``xsquawkbox/voice/ptt``                  | XSB: Radio Press-to-Talk           | Use to send on the selected radio              |
+-------------------------------------------+------------------------------------+------------------------------------------------+
| ``xsquawkbox/command/start_text_entry``   | XSB: Start Text Entry              | Use to activate the input prompt for text      |
|                                           |                                    | commands and text radio                        |
+-------------------------------------------+------------------------------------+------------------------------------------------+
| ``xsquawkbox/command/toggle_text_window`` | XSB: Toggle Text Window Visibility | Toggles visibility of the text radio/command   |
|                                           |                                    | window                                         |
+-------------------------------------------+------------------------------------+------------------------------------------------+
| ``xsquawkbox/text/prevpage``              | XSB: Text Window: Previous Page    | Scrolls the text window back one line          |
+-------------------------------------------+------------------------------------+------------------------------------------------+
| ``xsquawkbox/text/nextpage``              | XSB: Text Window: Next Page        | Scrolls the text window forward one line       |
+-------------------------------------------+------------------------------------+------------------------------------------------+
| ``xsquawkbox/text/start``                 | XSB: Text Window: Scroll to Start  | Scrolls the text window to the earliest line   |
+-------------------------------------------+------------------------------------+------------------------------------------------+
| ``xsquawkbox/text/end``                   | XSB: Text Window: Scroll to End    | Scrolls the text window to the latest line     |
+-------------------------------------------+------------------------------------+------------------------------------------------+
| ``xsquawkbox/command/reply_next``         | XSB: Reply to Last Sender          | Starts a reply to the person who last sent you |
|                                           |                                    | a ``.msg`` - subsequent presses cycle through  |
|                                           |                                    | recent senders                                 |
+-------------------------------------------+------------------------------------+------------------------------------------------+
| ``xsquawkbox/command/toggle_whos_online`` | XSB: Toggle Who's Online           | Toggles visibility of the Who's Online window  |
+-------------------------------------------+------------------------------------+------------------------------------------------+

.. NOTE::

   You must bind the Press to talk and Start Text Entry commands to use
   XSquawkBox - you will not be able to interact with the network properly
   without them

.. TIP:: 

   It is highly recommended you bind the `Toggle Text Visibility` and the text 
   window scroll commands.

Recommending Bindings for First-time Users
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Bind ``xsquawkbox/command/start_text_entry`` (“XSB: Start Text Entry” in X-Plane
  11) to Enter and/or Space.

* Bind ``xsquawkbox/voice/ptt`` (“XSB: Radio Press-to-Talk” in X-Plane 11) to a
  joystick/yoke button that is easily accessible - usually a trigger or thumb
  button if you want an authentic position.

* Bind ``xsquawkbox/command/toggle_text_window`` ("XSB: Toggle Text Window 
  Visibility" in X-Plane 11) to Keypad - (minus).

* Bind ``xsquawkbox/text/prevpage`` ("XSB: Text Window: Previous Page" in 
  X-Plane 11) to Page Up.

* Bind ``xsquawkbox/text/nextpage`` ("XSB: Text Window: Next Page" in 
  X-Plane 11) to Page Down.

* Bind ``xsquawkbox/text/start`` ("XSB: Text Window: Scroll to Start" in X-Plane
  11) to Home.

* Bind ``xsquawkbox/text/end`` ("XSB: Text Window: Scroll to End" in X-Plane 11)
  to End.

* Bind ``xsquawkbox/command/reply_next`` ("XSB: Reply to Last Sender" in X-Plane
  11) to Keypad *

* Bind ``xsquawkbox/command/toggle_whos_online`` ("XSB: Toggle Who's Online" in
  X-Plane 11) to Keypad /

Setting up your Audio Devices
-----------------------------