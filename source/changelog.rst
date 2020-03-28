XSquawkBox 2.0 Changelog
************************

For updates before 2.0, please refer to the README file included with the 
release

2.0 (stable) (2020-03-29)
=========================

 * Fixed a cosmetic bug where XSB OSBs would register themselves as servicing
   99.998MHz instead of VATSIM's standard 199.998MHz.

 * We now mangle the malformed .x20 and .x70 frequencies to their correct form
   when displayed, and normalise all frequency usage correctly for the
   respective service.  Hopefully this ends the confusion over what to tune, and
   radios not working as expected.

 * Make sure that command-entered frequencies (// and ///) are rounded to 5khz
   intervals.

 * Verbosely report when we're connecting and disconnecting from VATSIM AFV
   (Voice) as AFV service issues causing silent failures have been confusing
   endusers.

 * AFV-Native: Disable Nagle (where possible) on http connections per insistence
   of the AFV team.
 
2.0 beta 6 (2020-02-29)
=======================

 * Alas, another beta due to the two bugs (one major) dealt with in this
   release.

 * Fixed a bug in the HF frequency aliasing where we weren't correcting the
   frequency scale (KHz vs Hz) during the lookup.  Oceanic should now work with
   voice.

 * Treat Voice server timeouts the same as disconnects so they're automatically
   reconnected, rather than disabling the whole voice system until the next
   explicit reconnect.

 * Report Voice server errors as a System Message so they're more obvious.

 * Reenabled the use of ``xsquawkbox/input/string`` to pass input to other
   plugins for processing.

 * Update to AFV-Native 0.9.5:

   * Fixed a bug where the reported audiable channels count wasn't initialised
     inbetween creating the radio simulation state, and the first network
     update.  (Cosmetic only)

2.0 beta 5 hotfix 1 (2020-02-01)
================================

 * Reincorproate the fix from beta 4 hotfix 2 to not include AVX instructions
   in the non-AVX execution paths.

2.0 beta 5 (2020-02-01)
=======================

 * We do not perform time dilation detection for external flight model and
   OBS users anymore.  These restrictions were more from oversight than
   intent.

 * Time Dilation is now warned correctly after a soft reset of the time
   dilation pool.  (The actual behaviour was correct, we just weren't warning
   properly).

 * Don't produce a "your simulator is good" message unless we've produced a
   warning first.

 * Expose the time dilation detector pool remaining as a percentage and current
   detected fast/slow state via dataref.

 * Export some of our datarefs to DRE/DRT to make them easier to inspect, and
   to make that inspection reliable across all platforms.

 * Harden the ACCONFIG parser and tidy up our own output slightly to avoid
   potential undefined behaviours including random crashes when connected.

 * Fixes a bug where a run-time change of aircraft in AI slots could trip a
   disconnect without warning due to ignoring the plane identity slot of
   ``XPLM_MSG_PLANE_LOADED`` messages.

 * Fixes a bug where we reset the ACCONFIG internal model state every time we
   saw a ``XPLM_MSG_PLANE_LOADED`` message, irrespective if it was for our plane
   or for an AI slot.

 * Linux builds are now being performed on Ubuntu 18.04 (rather than 16.04).

 * Updated to AFV-Native 0.9.4 (build-chain and dependency version updates only)

2.0 beta 4 hotfix 2 (2020-01-01)
================================

 * Fix a build issue with libopus that was producing AVX instructions in the
   non-AVX execution paths on macOS and probably on Linux too.

2.0 beta 4 hotfix 1 (2019-12-30)
================================

 * Fix a build issue with portaudio that produced a hard dependency on macOS
   10.15
 
2.0 beta 4 (2019-12-29)
=======================

 * Made the volume controls work more naturally (volume reduction sounds more
   gradual making the volume control significantly more useful)

 * Fixed an oversight where the Radio effects enable/disable state wasn't
   being saved to preferences.

 * Update to AFV-Native 0.9.3:

   * Reverted to portaudio

   * Various small improvements.

   * Attempt to fix the behaviour around CryptoDTO session timeout/renewal.

   * Fixed race condition in audio processing when API session renewal occurred.

 * Expose voice stack debugging information via dataref so we can chart it
   and determine if certain things are behaving correctly.

2.0 beta 3 (2019-11-28)
=======================

 * Due to changes in AFV-Native, we no longer assume default devices are known.
   If you haven't selected an audio device, and audio is enabled, you'll get an
   error/warning on start-up and during connect and voice will be disabled until
   devices are set correctly.

 * Fixed Windows build to use the statically linked C++ runtime, removing the
   accidental dependency on the Visual C++ 2019 redistributable.

 * From AFV-Native: Fixed a bug where we'd under-fill the output buffer if
   we started an output stream, without a source attached (such as when XSB
   runs run the peak test).

 * From AFV-Native: changed the audio interface (again) from portaudio to
   libsoundio

 * Fixed the name libxplanemp presents as - log messages should correctly read
   "XSB" instead of "A PLUGIN" again. :)

 * Re-add a "disable_voice" config flag for use with multi-system rendering
   set-ups.

 * AFV-Native's logging now comes through XSB into the X-Plane logs - one less
   logfile.

2.0 beta 2 (2019-11-05)
=======================

 * Fixed a logic inversion that prevented the text-radio from working.

 * From AFV-Native: Reworked the audio device logic slightly so we should be
   able to find a working device even when the default doesn't work.

 * From libxplanemp: Re-enabled Async OBJ8 loading.

 * From AFV-Native: Fixed build issue that was causing speexdsp to use dynamic
   linking instead of static linking on MacOS and Linux

 * Attempted to fix the MacOS minimum required version and get it back down
   to 10.9, rather than 10.13.

2.0 beta 1 (2019-11-01)
=======================

 * Integrated AFV-Native to support the new VATSIM Audio Platform.  The
   AFV implementation (AFV-Native) and its integration represents 1-month of
   full-time professional development effort. AFV-Native will be open-sourced
   in short order.

 * We now support sending and receiving text radio messages on COM2.

 * The old keyboard/button-intercept code is gone - There's now a series of
   bindable commands in the ``xsquawkbox/`` namespace which replace them.
   You'll need to bind this by hand after upgrading!

 * Added ``.rx`` and ``.tx`` commands to provide access to the radio audio panel
   controls in models that do not have the right datarefs hooked up.

 * Switched to using the 8.33KHz spacing radio datarefs for future 8.33Khz
   frequency spacing support.

 * From libxplanemp:  Fixed a bug that was causing asynchronous OBJ7 loads to
   crash the simulator.

 * XSquawkBox is now a two man effort - please thank Jared Davison for adding
   his assistance to the client.

 * From libxplanemp:  Fix for the MSAA text size bug.

 * From libxplanemp:  Fix for the texture handle bug with specific versions of 
   the FF A320.

 * From libxplanemp:  Removed OpenGL state readbacks to avoid driver stalls.

 * From libxplanemp:  Fixed bug where libxplanemp tries to control AI aircraft
   when it didn't have exclusive control over the AI aircraft system.

 * From libxplanemp:  Obey simulator's anisotropic filtering setting when loading
   textures for legacy CSLs.

 * Observer Mode Support.

 * Aircraft Configuration State Visibility with Ground Level Correction.

 * Aural notifications on direct message and wallops.
 
 * Time Dilation safety check and enforcement.

 * Automatic Disconnect on slew and aircraft model change.

