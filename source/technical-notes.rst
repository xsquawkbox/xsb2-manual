Technical Notes
***************

Introduction
============

This section of the manual is dedicated to technical information about the
internals of XSquawkBox to aid debugging and integration.

Audio
=====

There are two independant audio implementations inside XSquawkBox.

One handles aural notifications - that's a simple wrapper onto OpenAL which
uses OpenAL-soft on Windows, and uses the X-Plane11 OpenAL on all other
platforms by inheriting the symbolspace from the X-Plane process.

The other implementation is the voice implementation that is part of AFV-Native.

AFV-Native itself is open source and more details about how the implementation
works under the hood can be glened by reading it's `source code <https://github.com/xsquawkbox/AFV-Native>`_.

AFV-Native itself runs in a dedicated thread which uses a combination of mutexes
& atomic variables to exchange the easily maintainable state between X-Plane and
AFV-Native.  A lock protected queue is used to pass major events (those normally
raised by the callback hook on AFV-Native's client class) from AFV-Native to 
X-Plane.  For This reason, most datarefs that are directly linked to AFV-Native
only update when the AFV-Native backend thread is running, and do so at a rate
independant to the framerate - roughly linked to AFV-Native's internal 20ms
tick.

Certain details from AFV-Native are exposed as datarefs to assist with capture
and real-time debugging of certain issues.  

+----------------------------------------+------------------------------------------------+
| Dataref Name                           | Purpose                                        |
+========================================+================================================+
| ``xsquawkbox/voice/input_overflows``   | Input Overflow counter.  Increments whenever   |
|                                        | input device has more data than AFV-Native     |
|                                        | is able to process in a timely manner.         |
+----------------------------------------+------------------------------------------------+
| ``xsquawkbox/voice/output_underflows`` | Output Underflow counter.  Increments when     |
|                                        | the output device requests more data than      |
|                                        | AFV-native has ready for playback              |
+----------------------------------------+------------------------------------------------+
| ``xsquawkbox/voice/active_channels``   | Number of independent voice streams currently  |
|                                        | being handled by AFV-Native.  This is          |
|                                        | distinctly different to the number of audiable |
+----------------------------------------+------------------------------------------------+
| ``xsquawkbox/voice/audiable_channels`` | Number of independent voice streams currently  |
|                                        | audiable - that is, they're tuned, have audio  |
|                                        | data available, and are on a radio that is     |
|                                        | capable of playback, and has non-zero gain.    |
+----------------------------------------+------------------------------------------------+
| ``xsquawkbox/voice/iterations``        | Iteration counter.  Increments whenever        |
|                                        | AFV-Native's main thread loop runs             |
+----------------------------------------+------------------------------------------------+
| ``xsquawkbox/voice/input_peak``        | Input Peak in dB.  Updates as long as audio is |
|                                        | active.                                        |
+----------------------------------------+------------------------------------------------+
| ``xsquawkbox/voice/input_vu``          | Input VU in dB.  Updates as long as audio is   |
|                                        | active.                                        |
+----------------------------------------+------------------------------------------------+
