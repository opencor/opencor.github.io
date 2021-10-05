.. _plugins_miscellaneous_core:

=============
 Core plugin
=============

The Core plugin is a non-selectable plugin that provides OpenCOR with file support, making it possible for OpenCOR to open, save, close, etc. files.
It also provides other plugins with handy methods and widgets.

.. _plugins_miscellaneous_core_uriScheme:

URI scheme
----------

The following commands are supported by the Core plugin:

- ``Core.selectMode``: select the mode in which a file should be viewed.

  - Example: |coreSelectMode|_.

.. |coreSelectMode| replace:: ``opencor://Core.selectMode/SimulationMode``
.. _coreSelectMode: opencor://Core.selectMode/SimulationMode

- ``Core.selectView``: select the view, within a given mode, in which a file should be viewed.

  - Example: |coreSelectView|_.

.. |coreSelectView| replace:: ``opencor://Core.selectView/RawTextView``
.. _coreSelectView: opencor://Core.selectView/RawTextView
