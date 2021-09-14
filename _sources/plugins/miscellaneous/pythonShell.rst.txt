.. _plugins_miscellaneous_pythonShell:

====================
 PythonShell plugin
====================

The PythonShell plugin offers a :ref:`CLI <userInterfaces_commandLineInterface>` interface to a `Python <https://python.org/>`__ shell in OpenCOR's environment.

.. _plugins_miscellaneous_pythonShellHelp:

Help
----

::

  $ ./OpenCOR -c PythonShell::help
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

Interactive Python shell
------------------------

::

  $ ./OpenCOR -c PythonShell::python
  Python 3.7.5 (default, Dec  2 2019, 11:02:28)
  [Clang 11.0.0 (clang-1100.0.33.12)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  >>>

From the :ref:`help <plugins_miscellaneous_pythonShellHelp>` section above, we can see that the ``python`` command is actually optional, which means that an interactive `Python <https://python.org/>`__ shell can also be launched using:

::

  $ ./OpenCOR -c PythonShell
  Python 3.7.5 (default, Dec  2 2019, 11:02:28)
  [Clang 11.0.0 (clang-1100.0.33.12)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  >>>

OpenCOR comes with the ``pythonshell[.bat]`` :ref:`script <userInterfaces_commandLineInterfacePythonRelatedScriptsPythonshell>`, which is an alias to ``./OpenCOR -c PythonShell $*``.
So, a third way to launch an interactive `Python <https://python.org/>`__ shell is:

::

  $ ./pythonshell
  Python 3.7.5 (default, Dec  2 2019, 11:02:28)
  [Clang 11.0.0 (clang-1100.0.33.12)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  >>>

Run a Python script
-------------------

::

  $ ./OpenCOR -c PythonShell::python /path/to/my/python/script.py
  ...

::

  $ ./OpenCOR -c PythonShell /path/to/my/python/script.py
  ...

::

  $ ./pythonshell /path/to/my/python/script.py
  ...
