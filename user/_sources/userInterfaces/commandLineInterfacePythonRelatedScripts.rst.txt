.. _userInterfaces_commandLineInterfacePythonRelatedScripts:

========================
 Python-related scripts
========================

The following `Python <https://python.org/>`__-related scripts can be used to:

- ``ipython[.bat]``: start an `IPython <https://ipython.org/>`__ session;
- ``jupyter[.bat]``: start a `Jupyter <https://jupyter.org/>`__ session;
- ``jupyterconsole[.bat]``: start a `Jupyter <https://jupyter.org/>`__ console, i.e. a terminal frontend for `Jupyter <https://jupyter.org/>`__ kernels;
- ``jupyterlab[.bat|.vbs]``: start a `JupyterLab <https://jupyterlab.readthedocs.io/en/latest/>`__, i.e. a Web-based interactive development environment for `Jupyter Notebooks <https://jupyter-notebook.readthedocs.io/en/latest/>`__, code and data;
- ``jupyternotebook[.bat|.vbs]``: start a `Jupyter Notebook <https://jupyter-notebook.readthedocs.io/en/latest/>`__, i.e. a Web application to create and share documents that contain live code, equations, visualizations and narrative text;
- ``pip[.bat]``: run the `pip <https://pip.pypa.io/en/stable/cli/>`__ command;
- ``python[.bat]``: start a `Python <https://python.org/>`__ session; and
- ``pythonshell[.bat]``: start a `Python <https://python.org/>`__ shell.

This, in OpenCOR's environment.

``ipython[.bat]``
-----------------

::

  $ ./ipython
  Python 3.12.2 (main, Apr  4 2024, 21:14:06) [Clang 15.0.0 (clang-1500.3.9.4)]
  Type 'copyright', 'credits' or 'license' for more information
  IPython 8.21.0 -- An enhanced Interactive Python. Type '?' for help.

  In [1]:

``jupyter[.bat]``
-----------------

::

  $ ./jupyter
  usage: jupyter [-h] [--version] [--config-dir] [--data-dir] [--runtime-dir] [--paths] [--json] [--debug] [subcommand]

  Jupyter: Interactive Computing

  positional arguments:
    subcommand     the subcommand to launch

  options:
    -h, --help     show this help message and exit
    --version      show the versions of core jupyter packages and exit
    --config-dir   show Jupyter config dir
    --data-dir     show Jupyter data dir
    --runtime-dir  show Jupyter runtime dir
    --paths        show all Jupyter paths. Add --json for machine-readable format.
    --json         output paths as machine-readable json
    --debug        output debug information about paths

  Available subcommands: console dejavu events execute kernel kernelspec lab labextension labhub migrate nbconvert
  notebook qtconsole run server troubleshoot trust

  Please specify a subcommand or one of the optional arguments.

.. _userInterfaces_commandLineInterfacePythonRelatedScriptsJupyterconsole:

``jupyterconsole[.bat]``
------------------------

::

  $ ./jupyterconsole
  Jupyter console 6.6.3

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

``pip[.bat]``
---------------------

::

  $ ./pip
  Usage:
    [OpenCOR]/Python/bin/python -m pip <command> [options]

  Commands:
    install                     Install packages.
    download                    Download packages.
    uninstall                   Uninstall packages.
    freeze                      Output installed packages in requirements format.
    inspect                     Inspect the python environment.
    list                        List installed packages.
    show                        Show information about installed packages.
    check                       Verify installed packages have compatible dependencies.
    config                      Manage local and global configuration.
    search                      Search PyPI for packages.
    cache                       Inspect and manage pip's wheel cache.
    index                       Inspect information available from package indexes.
    wheel                       Build wheels from your requirements.
    hash                        Compute hashes of package archives.
    completion                  A helper command used for command completion.
    debug                       Show information useful for debugging.
    help                        Show help for commands.

  General Options:
    -h, --help                  Show help.
    --debug                     Let unhandled exceptions propagate outside the main subroutine, instead of logging them
                                to stderr.
    --isolated                  Run pip in an isolated mode, ignoring environment variables and user configuration.
    --require-virtualenv        Allow pip to only run in a virtual environment; exit with an error otherwise.
    --python <python>           Run pip with the specified Python interpreter.
    -v, --verbose               Give more output. Option is additive, and can be used up to 3 times.
    -V, --version               Show version and exit.
    -q, --quiet                 Give less output. Option is additive, and can be used up to 3 times (corresponding to
                                WARNING, ERROR, and CRITICAL logging levels).
    --log <path>                Path to a verbose appending log.
    --no-input                  Disable prompting for input.
    --keyring-provider <keyring_provider>
                                Enable the credential lookup via the keyring library if user input is allowed. Specify
                                which mechanism to use [disabled, import, subprocess]. (default: disabled)
    --proxy <proxy>             Specify a proxy in the form scheme://[user:passwd@]proxy.server:port.
    --retries <retries>         Maximum number of retries each connection should attempt (default 5 times).
    --timeout <sec>             Set the socket timeout (default 15 seconds).
    --exists-action <action>    Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup,
                                (a)bort.
    --trusted-host <hostname>   Mark this host or host:port pair as trusted, even though it does not have valid or any
                                HTTPS.
    --cert <path>               Path to PEM-encoded CA certificate bundle. If provided, overrides the default. See 'SSL
                                Certificate Verification' in pip documentation for more information.
    --client-cert <path>        Path to SSL client certificate, a single file containing the private key and the
                                certificate in PEM format.
    --cache-dir <dir>           Store the cache data in <dir>.
    --no-cache-dir              Disable the cache.
    --disable-pip-version-check
                                Don't periodically check PyPI to determine whether a new version of pip is available for
                                download. Implied with --no-index.
    --no-color                  Suppress colored output.
    --no-python-version-warning
                                Silence deprecation warnings for upcoming unsupported Pythons.
    --use-feature <feature>     Enable new functionality, that may be backward incompatible.
    --use-deprecated <feature>  Enable deprecated functionality, that will be removed in the future.

``python[.bat]``
---------------------

::

  $ ./python
  Python 3.12.2 (main, Apr  4 2024, 21:14:06) [Clang 15.0.0 (clang-1500.3.9.4)] on darwin
  Type "help", "copyright", "credits" or "license" for more information.
  >>>

``pythonshell[.bat]``
---------------------

This script is a shortcut to using the :ref:`Python shell <plugins_miscellaneous_pythonShell>` plugin.
Thus,

::

  $ ./pythonshell


is an alias for:

::

  $ ./OpenCOR -c PythonShell "$@"
