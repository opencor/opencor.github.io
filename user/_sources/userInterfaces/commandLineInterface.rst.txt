.. _userInterfaces_commandLineInterface:

==============================
 Command Line Interface (CLI)
==============================

OpenCOR can be used from the `CLI <https://en.wikipedia.org/wiki/Command-line_interface>`__ using the ``OpenCOR`` script, as illustrated below.
`Python <https://python.org/>`__-related :ref:`scripts <userInterfaces_commandLineInterfacePythonRelatedScripts>` are also provided.

Help
----

::

  $ ./OpenCOR -h
  Usage: OpenCOR [-a|--about] [-c|--command [<plugin>]::<command> [<argument> ...]] [-e|--exclude <plugins>] [-h|--help] [-i|--include <plugins>] [-p|--plugins] [-r|--reset] [-s|--status] [-v|--version] [<files>]
   -a, --about     Display some information about OpenCOR
   -c, --command   Send a command to one or all the CLI plugins
   -e, --exclude   Exclude the given plugin(s)
   -h, --help      Display this help information
   -i, --include   Include the given plugin(s)
   -p, --plugins   Display all the CLI plugins
   -r, --reset     Reset all your settings
   -s, --status    Display the status of all the plugins
   -v, --version   Display the version of OpenCOR

About
-----

::

  $ ./OpenCOR -a
  OpenCOR Version 0.7
  macOS 13.0
  Copyright 2011-2022

  OpenCOR is a cross-platform modelling environment, which can be used to organise, edit, simulate and analyse CellML files.

Command
-------

::

  $ ./OpenCOR -c ::help
  Commands supported by the CellMLTextView plugin:
   * Display the commands supported by the CellMLTextView plugin:
        help
   * Export a CellML Text <file> to CellML:
        export <file>
   * Import a CellML <file> to the CellML Text format:
        import <file>

  Commands supported by the CellMLTools plugin:
   * Display the commands supported by the CellMLTools plugin:
        help
   * Export <file> to a given <format> or a given <language>:
        export <file> <format>|<language>
     <format> can take one of the following values:
        cellml_1_0: to export a CellML 1.1 file to CellML 1.0
     <language> can take one of the following values:
        c: to export a CellML file to C
        fortran_77: to export a CellML file to FORTRAN 77
        matlab: to export a CellML file to MATLAB
        python: to export a CellML file to Python
   * Validate <file>:
        validate <file>

  Commands supported by the JupyterKernel plugin:
   * Display the commands supported by the JupyterKernel plugin:
        help
   * Start the OpenCOR Jupyter kernel:
        kernel <connectionFile>

  Commands supported by the PythonShell plugin:
   * Display the commands supported by the PythonShell plugin:
        help
   * Run an interactive Python shell in OpenCOR's environment:
        [python] [<option> ...] [-c <command> | -m <module> | <file> | -] [<argument> ...]
     where
        -c <command> executes a program passed in as a string
        -m <module> runs a library module as a script
        <file> runs a program read from a script file
        - runs a program read from the standard input

::

  $ ./OpenCOR -c CellMLTools::help
  Commands supported by the CellMLTools plugin:
   * Display the commands supported by the CellMLTools plugin:
        help
   * Export <file> to a given <format> or a given <language>:
        export <file> <format>|<language>
     <format> can take one of the following values:
        cellml_1_0: to export a CellML 1.1 file to CellML 1.0
     <language> can take one of the following values:
        c: to export a CellML file to C
        fortran_77: to export a CellML file to FORTRAN 77
        matlab: to export a CellML file to MATLAB
        python: to export a CellML file to Python
   * Validate <file>:
        validate <file>

Exclude
-------

::

  $ ./OpenCOR -e Core HelpWindow Unknown
   - Core: cannot be directly excluded.
   - HelpWindow: excluded from the GUI version of OpenCOR.
   - Unknown: unknown plugin.

Include
-------

::

  $ ./OpenCOR -i Core HelpWindow Unknown
   - Core: cannot be directly included.
   - HelpWindow: included to the GUI version of OpenCOR.
   - Unknown: unknown plugin.

Plugins
-------

::

  $ ./OpenCOR -p
  The following CLI plugins are available:
   - CellMLTextView: a plugin to edit CellML files using the CellML Text format.
   - CellMLTools: a plugin to access various CellML-related tools.
   - JupyterKernel: the Jupyter kernel plugin.
   - PythonShell: the Python shell plugin.

Reset
-----

::

  $ ./OpenCOR -r
  All your settings have been reset.

Status
------

::

  $ ./OpenCOR -s
  The following plugins are available:
   - CellMLAPI: the plugin is loaded and fully functional.
   - CellMLEditingView: the plugin is loaded and fully functional.
   - CellMLSupport: the plugin is loaded and fully functional.
   - CellMLTextView: the plugin is loaded and fully functional.
   - CellMLTools: the plugin is loaded and fully functional.
   - COMBINESupport: the plugin is loaded and fully functional.
   - Compiler: the plugin is loaded and fully functional.
   - Core: the plugin is loaded and fully functional.
   - CVODESolver: the plugin is loaded and fully functional.
   - DataStore: the plugin is loaded and fully functional.
   - EditingView: the plugin is loaded and fully functional.
   - EditorWidget: the plugin is loaded and fully functional.
   - ForwardEulerSolver: the plugin is loaded and fully functional.
   - FourthOrderRungeKuttaSolver: the plugin is loaded and fully functional.
   - HeunSolver: the plugin is loaded and fully functional.
   - JupyterKernel: the plugin is loaded and fully functional.
   - KINSOLSolver: the plugin is loaded and fully functional.
   - libNuML: the plugin is loaded and fully functional.
   - libSBML: the plugin is loaded and fully functional.
   - libSEDML: the plugin is loaded and fully functional.
   - LLVMClang: the plugin is loaded and fully functional.
   - MathMLViewerWidget: the plugin is loaded and fully functional.
   - Python: the plugin is loaded and fully functional.
   - PythonPackages: the plugin is loaded and fully functional.
   - PythonQt: the plugin is loaded and fully functional.
   - PythonQtSupport: the plugin is loaded and fully functional.
   - PythonShell: the plugin is loaded and fully functional.
   - PythonSupport: the plugin is loaded and fully functional.
   - QScintilla: the plugin is loaded and fully functional.
   - QScintillaWidget: the plugin is loaded and fully functional.
   - Qwt: the plugin is loaded and fully functional.
   - SecondOrderRungeKuttaSolver: the plugin is loaded and fully functional.
   - SEDMLSupport: the plugin is loaded and fully functional.
   - SimulationSupport: the plugin is loaded and fully functional.
   - StandardSupport: the plugin is loaded and fully functional.
   - SUNDIALS: the plugin is loaded and fully functional.
   - ZIPSupport: the plugin is loaded and fully functional.
   - zlib: the plugin is loaded and fully functional.

Version
-------

::

  $ ./OpenCOR -v
  OpenCOR Version 0.7
