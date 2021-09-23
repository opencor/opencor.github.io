.. _knownLimitations:

===================
 Known limitations
===================

The following limitations have been noticed when using OpenCOR on our `supported platforms <https://opencor.ws/supportedPlatforms.html>`__.

Windows, Linux and macOS
------------------------

- By default, OpenCOR uses the system's language for menus, message boxes, etc., as long as it is either English or French (please `contact us <https://opencor.ws/contactUs.html>`__ if you would like OpenCOR to support other languages).
  If the system uses another language, OpenCOR will default to English.
  Otherwise, if you specify English or French, then please be aware that system messages, diaogs, etc. will still be displayed using the system's language (assuming it is not one of the languages supported by OpenCOR).
- OpenCOR uses the `CellML API <https://github.com/cellmlapi/cellml-api/>`__, which is known to have the following limitations:

  - It will crash OpenCOR if you try to export a `CellML <https://cellml.org/>`__ file to a user-defined format that is described in a file that contains valid, but unknown, `XML <https://w3.org/XML>`__.
  - It may incorrectly (in)validate certain `CellML <https://cellml.org/>`__ files.

- OpenCOR comes with :ref:`pythonSupport`, which requires OpenCOR to be installed in a directory that does not contain spaces.

Windows and Linux
-----------------

- A scaled display will, on `Linux <https://en.wikipedia.org/wiki/Linux>`__, result in some aspects of OpenCOR being rendered at the wrong size (e.g. icons will be smaller and scroll bars bigger).
  On `Windows <https://en.wikipedia.org/wiki/Windows>`__, OpenCOR should scale itself automatically, although it will look more or less blurry depending on your display scaling and screen resolution.
  In case OpenCOR does not scale itself, turn off *Fix scaling for apps*:

    .. image:: pics/windowsSettings01.png
       :align: center
       :scale: 25%

    .. image:: pics/windowsSettings02.png
       :align: center
       :scale: 25%

    .. image:: pics/windowsSettings03.png
       :align: center
       :scale: 25%

  or better, locate your copy of OpenCOR, right click on ``[OpenCOR]\bin\OpenCOR.exe``, click on the ``Properties`` menu item, and have the high DPI scaling performed by the system:

    .. image:: pics/opencorProperties01.png
       :align: center
       :scale: 25%

    .. image:: pics/opencorProperties02.png
       :align: center
       :scale: 25%

Windows
-------

- The :ref:`File Browser window <plugins_organisation_fileBrowserWindow>` plugin may, on some systems, result in OpenCOR being slow to respond at startup.
  This has nothing to do with OpenCOR, but most likely with a `Windows <https://en.wikipedia.org/wiki/Microsoft_Windows>`__ shell add-on.
  `This page <https://brighthub.com/computing/windows-platform/articles/86552.aspx>`__ may help address the issue, but if not then you might have to disable the :ref:`File Browser window <plugins_organisation_fileBrowserWindow>` plugin.
- If OpenCOR was installed in a system folder using the `ZIP <https://en.wikipedia.org/wiki/ZIP_(file_format)>`__ file then the first time OpenCOR is run it will have to be run as administrator.
  This is so that OpenCOR can update the `shebang <https://en.wikipedia.org/wiki/Shebang_(Unix)>`__ of its `Python <https://en.wikipedia.org/wiki/Python_(programming_language)>`__ scripts to point to its copy of Python.

macOS
-----

- Starting with `macOS Mojave <https://en.wikipedia.org/wiki/MacOS_Mojave>`__, macOS has a `Dark Mode <https://support.apple.com/HT208976>`__, which is not currently supported by OpenCOR.
