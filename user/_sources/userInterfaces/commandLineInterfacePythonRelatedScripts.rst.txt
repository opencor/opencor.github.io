.. _userInterfaces_commandLineInterfacePythonRelatedScripts:

========================
 Python-related scripts
========================

The following `Python <https://python.org/>`__-related scripts can be used to start:

- ``ipython[.bat]``: an `IPython <https://ipython.org/>`__ session;
- ``jupyter[.bat]``: a `Jupyter <https://jupyter.org/>`__ session;
- ``jupyterconsole[.bat]``: a `Jupyter <https://jupyter.org/>`__ console, i.e. a terminal frontend for `Jupyter <https://jupyter.org/>`__ kernels;
- ``jupyterlab[.bat|.vbs]``: a `JupyterLab <https://jupyterlab.readthedocs.io/en/latest/>`__, i.e. a Web-based interactive development environment for `Jupyter Notebooks <https://jupyter-notebook.readthedocs.io/en/latest/>`__, code and data;
- ``jupyternotebook[.bat|.vbs]``: a `Jupyter Notebook <https://jupyter-notebook.readthedocs.io/en/latest/>`__, i.e. a Web application to create and share documents that contain live code, equations, visualizations and narrative text; and
- ``pythonshell[.bat]``: a `Python <https://python.org/>`__ shell.

This, in OpenCOR's environment.

``ipython[.bat]``
-----------------

::

  $ ./ipython
  Python 3.7.5 (default, May 27 2022, 16:06:22)
  Type 'copyright', 'credits' or 'license' for more information
  IPython 7.8.0 -- An enhanced Interactive Python. Type '?' for help.

  In [1]:

``jupyter[.bat]``
-----------------

::

  $ ./jupyter
  usage: jupyter [-h] [--version] [--config-dir] [--data-dir] [--runtime-dir]
                 [--paths] [--json] [--debug]
                 [subcommand]
  jupyter: error: one of the arguments --version subcommand --config-dir --data-dir --runtime-dir --paths is required

.. _userInterfaces_commandLineInterfacePythonRelatedScriptsJupyterconsole:

``jupyterconsole[.bat]``
------------------------

::

  $ ./jupyterconsole
  Jupyter console 6.0.0

  Jupyter kernel for OpenCOR


  In [1]:

``jupyterlab[.bat]``
--------------------

::

  $ ./jupyterlab

.. image:: pics/commandLineInterfacePythonRelatedScripts01.png
   :align: center
   :scale: 25%

``jupyternotebook[.bat|.vbs]``
------------------------------

::

  $ ./jupyternotebook

.. image:: pics/commandLineInterfacePythonRelatedScripts02.png
   :align: center
   :scale: 25%

.. _userInterfaces_commandLineInterfacePythonRelatedScriptsPythonshell:

``pythonshell[.bat]``
---------------------

This script is a shortcut to using the :ref:`Python shell <plugins_miscellaneous_pythonShell>` plugin.
Thus,

::

  $ ./pythonshell


is an alias for:

::

  $ ./OpenCOR -c PythonShell "$@"
