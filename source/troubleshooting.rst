Troubleshooting XSquawkBox Issues
*********************************

General
=======

Be sure to check the `XSquawkBox Website <http://xsb.xsquawkbox.net>`_ to see
if your issue has been addressed on the Known Issues page, or in a recent
post from the developer.

.. WARNING::

   If submitting a bug report to the developers, You must not omit, edit or
   shorten the content from ``Log.txt`` as the full content can be critical in
   determining the cause of issues.

   If it is clear you have omitted, edited or shortened the log, the developers
   will ignore your bug report.
   
.. _troubleshooting-load:

Issues with Plugin Loading
==========================

Issues with the plugin not loading are usually caused by not following the
installation instructions correctly.

When X-Plane runs, it creates a file named ``Log.txt`` Inside your X-Plane
installation folder which contains errors and information from X-Plane's last
run.  If XSquawkBox has issues loading, the cause or related information is
usually recorded in this file.

.. admonition:: Linux

   On Linux, the usual cause for this is a missing shared library.  The 
   ``Log.txt`` file will indicate which shared library it failed to load.  You
   should then locate and install the version of that library as shipped by your
   distribution.  You can verify if all the necessary shared libraries are
   installed by using the ``ldd`` tool against the ``linux.xpl`` file inside the
   plugin's directory.

If your system meets the system requirements, and you have followed the 
installation instructions as written, and you cannot find any information 
suggesting a known cause, submit a bug report on the XSquawkBox website, 
including the contents of ``Log.txt`` in full.

.. _troubleshooting-audio-devices:

Can't see your desired input/output device
==========================================

AFV-Native can only handle a specific subset of audio devices:

All devices must support a 48Khz sampling rate, or have OS-provided resampling.
This accounts for the majority of USB headsets and most integrated audio 
devices.

In addition, input devices must be monaural or able to operate in a pure
monaural mode.  Similarly, output devices must be monaural or stereo or able to 
operate in a pure monaural or stereo mode.

In addition, bluetooth connected headsets are not supported - they might work if
they support the necessary sampling rate and capture modes, but the developers
cannot invest significant effort into trying to fix issues with them.

.. NOTE::

   The limitation is largely borne from AFV-Native audio interface code, and if
   you're a programmer, you can attempt to remedy the limitations there and 
   submit a patch to the author/maintainer.
   
   Unfortunately, there's just too many possibilities, and the requirements 
   from the AFV system itself are fairly specific - the author cannot support
   every possibility on his own and has focused on the most common cases.

Some OS Specific notes on this are below:

macOS
^^^^^

macOS only supports one audio API - CoreAudio.

Run the "Audio MIDI Setup" utility (usually in ``/Applications/Utilities``) and
make sure the sampling rate for the device you want to use is set to 48KHz.
Devices set to 44.1KHz (and presumably lower) will not be recognised as 
compatible.

Windows
^^^^^^^

Windows supports multiple audio APIs.  In terms of prefernce, it is recommended
to use WASAPI first if possible, with the next preference being DirectSound, and
the least preferred being WinMME.

5.1 Surround speaker sets that connect directly to your PC via 3 x 3.5mm jacks
have been known to not work with some integrated motherboard audio.  If you
really want to output the radio to the speakers, change your speaker layout to
stereo.  This configuration is not recommended however - dedicated headsets work
best for VATSIM radio communications.

To force the default sampling rate for a device:

 1. Open Control Panel (not settings)

 2. Open the "Sound" control panel

 3. Click on recording tab

 4. For each device you want to be able to use as a microphone:

    a. Locate the input on the device list and right click on it and select "Properties".

    b. Click on the "Advanced Tab"

    c. Make sure the "Default Format" is set to "48000Hz (DVD Quality)"

    d. Click "OK" to close the device settings.

 5. Click "OK" to close the Sound control panel.

Linux
^^^^^

Linux presently only supports the ALSA audio API.  

Whilst it is possible to connect ALSA to Pulse, or to connect audio processing 
that'll generally overcome any mismatch problems, no support can be offered for 
the Linux distribution provided audio components by the XSquawkBox team.

I'm Not Hearing Any Voice
=========================

The voice support has been fairly heavily tested - there have been a lot of
problems reported that were traced through to incorrect operation or 
compatibility issues.

.. NOTE::

   VATSIM has been suspending ATIS operation during periods of high activity.

   A failure to receive voice ATIS is not an indication of problems with the
   client unless you can confirm that other users are receiving voice ATIS.

First, make sure you didn't get a warning message from XSB when you connected 
that your audio devices weren't set up correctly.  If you did, you need to 
disconnect and access the Audio Setup option and select your input and output
devices.

Next, check the aircraft compatibility information to see if there's a known 
issue with the model you're using - you may need to vary how you're trying to
use XSB or the aircraft if there's an identified issue.

Once you've checked for known issues and compensated for any stated,
ensure you have set the right frequency on the radio, using the panel controls
only.  (If already correctly set, set the radio away from the desired frequency,
then back again).

If that doesn't resolve the issue, next ensure you have set the radio to be
enabled for receive on the audio panel.  Use the ``.rx`` command to force enable
it and see if that makes any difference.

Next, Adjust the radio's independant volume control and make sure it's turned
up.

Finally, if you've exhausted all of those options, and it's still not working,
disconnect and access audio setup - and make sure the audio device selected
is the one you are actually using.  Check that the peak meter moves when you
speak into your microphone.

I hear myself when I transmit voice
===================================

This is almost always caused by having both radios tuned to the same frequency,
and both set with Rx Enabled.

Disable the non-transmitting radio for receive, or change it's frequency.
