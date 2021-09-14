.. _uriScheme:

============
 URI scheme
============

OpenCOR has its own `URI scheme <https://en.wikipedia.org/wiki/Uniform_Resource_Identifier>`__, which gets registered the first time OpenCOR is run.
The scheme takes the form:

::

  opencor://[pluginName.]command[/argument1[|argument2|argument3|...|argumentN]]

It can be used in a Web browser, as well as in a Web document (e.g. the :ref:`plugins_index` page).
Both ``pluginName`` and ``command`` are case insensitive while it depends on the command when it comes to ``argument1``, ``argument2``, ``argument3``, ..., ``argumentN``.
For a command to be executable, no modal dialog must be active in OpenCOR.

The following commands are supported by OpenCOR itself:

- ``openPluginsDialog``: open the :ref:`Plugins dialog <plugins_index>`.

  - Example: |openPluginsDialog|_.

.. |openPluginsDialog| replace:: ``opencor://openPluginsDialog``
.. _openPluginsDialog: opencor://openPluginsDialog

- ``openPreferencesDialog``: open the :ref:`Preferences dialog <preferences>`.

  - Example: |openPreferencesDialog|_.

.. |openPreferencesDialog| replace:: ``opencor://openPreferencesDialog``
.. _openPreferencesDialog: opencor://openPreferencesDialog

- ``openAboutDialog``: open the About dialog.

  - Example: |openAboutDialog|_.

.. |openAboutDialog| replace:: ``opencor://openAboutDialog``
.. _openAboutDialog: opencor://openAboutDialog

- ``importFile``: import a file (or open it if it cannot be imported), which `path <https://en.wikipedia.org/wiki/Path_(computing)>`__/`URL <https://en.wikipedia.org/wiki/URL>`__ is given as an argument.

  - Example #1: |importFile01|_ to import ``/home/user/file``.
  - Example #2: |importFile02|_ to import ``https://my.domain.com/file``.

.. |importFile01| replace:: ``opencor://importFile//home/user/file``
.. _importFile01: opencor://importFile//home/user/file

.. |importFile02| replace:: ``opencor://importFile/https://my.domain.com/file``
.. _importFile02: opencor://importFile/https://my.domain.com/file

- ``importFiles``: import several files (or open one/several of them if it/they cannot be imported), which `path <https://en.wikipedia.org/wiki/Path_(computing)>`__/`URL <https://en.wikipedia.org/wiki/URL>`__ is given as arguments, separated by ``|``.

  - Example #1: |importFiles01|_ to import ``/home/user/file1`` and ``/home/user/file2``.
  - Example #2: |importFiles02|_ to import ``https://my.domain.com/file1`` and ``https://my.domain.com/file2``.

.. |importFiles01| replace:: ``opencor://importFiles//home/user/file1|/home/user/file2``
.. _importFiles01: opencor://importFiles//home/user/file1|/home/user/file2

.. |importFiles02| replace:: ``opencor://importFiles/https://my.domain.com/file1|https://my.domain.com/file2``
.. _importFiles02: opencor://importFiles/https://my.domain.com/file1|https://my.domain.com/file2

- ``openFile``: open a file, which `path <https://en.wikipedia.org/wiki/Path_(computing)>`__/`URL <https://en.wikipedia.org/wiki/URL>`__ is given as an argument.

  - Example #1: |openFile01|_ to open ``/home/user/file``.
  - Example #2: |openFile02|_ to open |sedmlFile|_.

.. |openFile01| replace:: ``opencor://openFile//home/user/file``
.. _openFile01: opencor://openFile//home/user/file

.. |openFile02| replace:: ``opencor://openFile/https://models.physiomeproject.org/.../cell-model.sedml``
.. _openFile02: opencor://openFile/https://models.physiomeproject.org/workspace/49e/rawfile/0a252e033bdf5e65d5a6490c9d3ade9035fef04e/experiments/cell-model.sedml

.. |sedmlFile| replace:: ``https://models.physiomeproject.org/.../cell-model.sedml``
.. _sedmlFile: https://models.physiomeproject.org/workspace/49e/rawfile/0a252e033bdf5e65d5a6490c9d3ade9035fef04e/experiments/cell-model.sedml

- ``openFiles``: open several files, which `path <https://en.wikipedia.org/wiki/Path_(computing)>`__/`URL <https://en.wikipedia.org/wiki/URL>`__ is given as arguments, separated by ``|``.

  - Example #1: |openFiles01|_ to open ``/home/user/file1`` and ``/home/user/file2``.
  - Example #2: |openFiles02|_ to open |cellmlFile|_ and |sedmlFile|_.

.. |openFiles01| replace:: ``opencor://openFiles//home/user/file1|/home/user/file2``
.. _openFiles01: opencor://openFiles//home/user/file1|/home/user/file2

.. |openFiles02| replace:: ``opencor://openFiles/https://models.physiomeproject.org/.../cell-model.xml|https://models.physiomeproject.org/.../cell-model.sedml``
.. _openFiles02: opencor://openFiles/https://models.physiomeproject.org/workspace/49e/rawfile/0a252e033bdf5e65d5a6490c9d3ade9035fef04e/experiments/cell-model.xml|https://models.physiomeproject.org/workspace/49e/rawfile/0a252e033bdf5e65d5a6490c9d3ade9035fef04e/experiments/cell-model.sedml

.. |cellmlFile| replace:: ``https://models.physiomeproject.org/.../cell-model.xml``
.. _cellmlFile: https://models.physiomeproject.org/workspace/49e/rawfile/0a252e033bdf5e65d5a6490c9d3ade9035fef04e/experiments/cell-model.xml

As hinted above, a command can be sent to a given plugin.
For example, we can ask the :ref:`Core <plugins_miscellaneous_core_uriScheme>` plugin to select a particular mode or view.

- Example #1: |coreSelectMode|_ to select the Simulation mode.
- Example #2: |coreSelectView|_ to select the :ref:`Raw Text view <plugins_editing_rawTextView>`.

.. |coreSelectMode| replace:: ``opencor://Core.selectMode/SimulationMode``
.. _coreSelectMode: opencor://Core.selectMode/SimulationMode

.. |coreSelectView| replace:: ``opencor://Core.selectView/RawTextView``
.. _coreSelectView: opencor://Core.selectView/RawTextView
