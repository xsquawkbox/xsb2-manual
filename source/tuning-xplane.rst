Tuning X-Plane for VATSIM
*************************

Due to some key behaviours in X-Plane that differ to its competitors, it is
necessary to ensure X-Plane is correctly adjusted to maintain a stable framerate
above 20fps.  XSquawkBox recommends that you target 30-35fps to ensure that
you do not experience significant slowdowns that result in the simulator's "time
dilation" effect from being applied.  "Time dilation" causes significant issues
for traffic separation and sequencing and is not permitted on the network.

Laminar Software maintains documentation on how to set the rendering options
correctly for 
`X-Plane 10 <https://www.x-plane.com/kb/setting-the-rendering-options-for-best-performance/>`_
and for
`X-Plane 11 <https://www.x-plane.com/manuals/desktop/#settingtherenderingoptionsforbestperformance>`_.

In addition to Laminar's notes, we offer the following guidance:

* Read Laminar's guides and follow the steps, looking at frame times and 
  adjusting settings as your first port of call before resorting to a graphics
  detail autoadjusting tool - getting the settings right first will generally 
  help immensely, and let the detail autoadjusting tool deal with the 
  unexpected.

* X-Plane 11 was released in 2016 and targetted hardware contemporary for the
  time.  If you only have an older system, do consider using X-Plane 10 instead.
  
  - In the XSB team's experience, older (DDR3 memory equipped) systems have
    significant difficulties running X-Plane 11 with higher CPU-dependent
    settings - even an i7-4770, once a top of the line i7 CPU, struggles in 
    X-Plane 11 with the world object setting set to medium, but can handle
    X-Plane 10 easily.

* X-Plane 11 can produce highly variant frame-rates based on the scene contents 
  - a properly tuned top-end system can produce 35-40fps on approach, and over
  90fps in flight.    This variance can be easily demonstrated by 
  switching to an external camera, moving the camera clear of the aircraft, and 
  then pitching the view up and down through 180 degrees, watching the framerate
  as you do it.  Tuning must be performed in areas with high complexity scenery
  areas, with the camera pointed at the terrain for best results.

* Scenery, Plugins and Add-on Aircraft can all dramatically change the minimum
  system requirements.

  - In particular, whilst alpilotx's HD and UHD terrain meshes look great,
    they seriously increase the CPU burden for the same rendering settings due
    to their autogen density.

  - XSB, and any other plugins that use xplanemp, require additional texture
    memory on top of what the simualtor uses by default to load aircraft
    textures on the fly - high traffic situations may result in significant
    increases in required texture memory.  Being conservative with the texture
    memory slider if you know you're going to enter a high traffic event is 
    well advised.  If your settings result in X-Plane needing more texture 
    memory than your system has available, it will result in a severe
    degradation of your frame-rate.

* Do not set texture quality to the Uncompressed option (the very highest 
  setting) - there's absolutely no cause for it.  If you're finding an add-on's
  textures look poor with compressed textures enabled, you should report the
  issue to the add-on developer - such issues only tend to occur with assets 
  that do not ship with precompressed textures as the real-time compressor
  is not as good as the offline tools.  The same applies to CSLs that look poor
  with compressed textures enabled - report such issues to the CSL author.
