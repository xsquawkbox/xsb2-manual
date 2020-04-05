Aircraft Compatibiilty
**********************

As XSquawkBox 2.x implements a significantly more extensive radio model, we've
discovered there are some compatibility issues with some aircraft.

Where it's indicated that the Tx Select control is inoperative or not rigged,
you can use the ``.tx`` command to manually set the selected radio for
Transmission.

Where it's indicated that the Rx Enable controls are inoperative or not rigged,
you can use the ``.rx`` command to manually enable or disable radios for 
listening.

More specific notes will be left where there is aberant or complex unexpected
behaviour.

.. NOTE:

   The information here is not exhaustive - but serves as a guide to issues
   we're aware of with specific aircraft.  Where possible, we've noted which
   versions we tested against.

   The XSquawkBox team can not provide support for issues with a specific
   aircraft model - only for XSquawkBox itself.

X-Plane Stock Aircraft
======================

Stock, as in, came with X-Plane.

X-Plane 10
----------

In general, X-Plane 10 stock aircraft have fairly poor radio rigging.

You will need to make use of the ``.tx`` and ``.rx`` commands to operate their
radios comfortably.

X-Plane 11
----------

This information was correct for X-Plane 11.41

This information only covers issues with Tx/Rx selection controls as we weren't
assessing any other issues at the time.

+----------------------------------------+---------------------------------------------------+
| Aircraft                               | Compatibility Notes                               |
+========================================+===================================================+
| Baron B58                              | No Tx Select Control.  No other problems found.   |
+----------------------------------------+---------------------------------------------------+
| Boeing 737-800                         | Tx Select Knob present, but not routed correctly. |
+----------------------------------------+---------------------------------------------------+
| Boeing 747-400                         | No problems found.                                |
+----------------------------------------+---------------------------------------------------+
| Cessna 172 (without G1000)             | No problems found.                                |
+----------------------------------------+---------------------------------------------------+
| Cirrus Vision (SF-50)                  | No problems found.                                |
+----------------------------------------+---------------------------------------------------+
| Kingair C90                            | No problems found.                                |
+----------------------------------------+---------------------------------------------------+
| MD-80                                  | No problems found.                                |
+----------------------------------------+---------------------------------------------------+
| Sikorsky S-76	                         | No Tx Select Control.  No other problems found.   |
+----------------------------------------+---------------------------------------------------+
| Stinson L5                             | One radio only.  No problems found.               |
+----------------------------------------+---------------------------------------------------+

Aerobask
========

Diamond DA-62 (v11.1.04)
------------------------
* No radio volume controls.

Airfoil Labs
============

Cessna 172SP (v1.7) - XP11
--------------------------
 * Missing volume controls from 3d panel.
 * COM1 volume available on GNS430 pop-out panel.

King Air 350 (v1.3) - XP11
--------------------------
 * Tx Select control will change Rx enabled states whenever changed.

Flight-factor / VMAX
====================

Airbus A320 Ultimate (v1.0.1) - XP11
------------------------------------
* Does not work properly with the ``//`` command.  Tuning via the 3D panel works
  fine.



Airbus A350 (v1.5.2) - XP11
---------------------------
* No progressive COM1/COM2 volume control.  (On/Off Only).


Boeing 757 (v1.21) - XP10
-------------------------
* Rx Enable is linked to Tx Select.
* Volume controls not rigged to datarefs.

FlyJSim
=======

727 Series V2 - XP10
--------------------
* No radio volume controls.


727 Series V3 (3.1908.1135) - XP11
----------------------------------
* Analogue radio volume not yet supported by XSB.

732 TwinJet V3 (3.1908.1135) - XP11
-----------------------------------
* Analogue radio volume not yet supported by XSB.

Hot Start
=========

TBM900 (v1.1.12) - XP11
-----------------------
* No problems found.

IXEG
====

737 Classic (v1.1) - XP10
-------------------------
* Independent COM volumes not rigged.

737 Classic (v1.21) - XP11
--------------------------
* Independent COM volumes not rigged.

Leading Edge Simulations
========================

Saab 340A (v1.5.1) - XP11
-------------------------
* No progressive COM volume. (volume sliders rigged as RX Enable).
* No visual indication to see currently selected Tx radio.

Rotate
======

MD-80 (v1.42r4) - XP11
----------------------
* Tx select not correctly rigged.                   |

X-Scenery
=========

Mitsubishi MU-2 Marquise (v1.9) - XP11
--------------------------------------
* Audio Panel auto-comm switch in-op.
* No COM1 volume control on 3D panel - popout GNS volume works.
* No COM2 volume control.