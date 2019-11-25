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

