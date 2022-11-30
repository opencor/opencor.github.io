.. _plugins_index:

=========
 Plugins
=========

OpenCOR is a plugin-based application.
As can be seen by opening the Plugins dialog (either by selecting the ``Tools`` | ``Plugins...`` menu or by clicking `here <opencor://openPluginsDialog>`__) and by unselecting ``Show only selectable plugins`` (if necessary), OpenCOR comes with different types of plugins:

.. image:: pics/plugins01.png
   :align: center
   :scale: 25%

You can select which plugins you want to use.
However, plugins that are needed by other plugins cannot be directly selected (e.g., the :ref:`Core <plugins_miscellaneous_core>` plugin is needed by the :ref:`Help window <plugins_miscellaneous_helpWindow>` plugin).
Instead, they will be automatically selected if and only if they are needed by at least one other plugin.

Most of the selectable plugins come with some kind of a :ref:`GUI <userInterfaces_graphicalUserInterface>`, which is of one of two types:

- **View:** such a plugin is used to interact with a file, be it to edit it, simulate it or analyse it (e.g., the :ref:`CellML Annotation view <plugins_editing_cellmlAnnotationView>` and :ref:`Simulation Experiment view <plugins_simulation_simulationExperimentView>` plugins).
- **Window:** such a plugin can be docked around the central area, undocked or hidden, as illustrated :ref:`here <userInterfaces_graphicalUserInterface>` (e.g., the :ref:`PMR window <plugins_organisation_pmrWindow>` and :ref:`Help window <plugins_miscellaneous_helpWindow>` plugins).

If no plugins are selected then OpenCOR is an :ref:`empty shell <userInterfaces_graphicalUserInterface_opencorWithNoLoadedPlugins>`.

Data store
----------

Data store plugins are used to store and manipulate data:

.. rst-class:: internal reference

   - :ref:`BioSignalMLDataStore <plugins_dataStore_biosignalmlDataStore>`\ : a BioSignalML specific data store plugin.
   - :ref:`CSVDataStore <plugins_dataStore_csvDataStore>`\ : a `CSV <https://en.wikipedia.org/wiki/Comma-separated_values>`__ specific data store plugin.

There is also one non-selectable data store plugin:

- **DataStore:** a plugin that provides core data store facilities.

Editing
-------

Editing plugins are used to edit files:

.. rst-class:: internal reference

   - :ref:`CellMLAnnotationView <plugins_editing_cellmlAnnotationView>`\ : a plugin to annotate `CellML <https://cellml.org/>`__ files.
   - :ref:`CellMLTextView <plugins_editing_cellmlTextView>`\ : a plugin to edit `CellML <https://cellml.org/>`__ files using the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>`.
   - :ref:`RawCellMLView <plugins_editing_rawCellmlView>`\ : a plugin to edit `CellML <https://cellml.org/>`__ files using an `XML <https://w3.org/XML>`__ editor.
   - :ref:`RawSEDMLView <plugins_editing_rawSedmlView>`\ : a plugin to edit `SED-ML <https://sed-ml.github.io/>`__ files using an `XML <https://w3.org/XML>`__ editor.
   - :ref:`RawTextView <plugins_editing_rawTextView>`\ : a plugin to edit text-based files using a text editor.

There are also some non-selectable editing plugins:

- **CellMLEditingView:** a plugin that provides core `CellML <https://cellml.org/>`__ editing view facilities.
- :ref:`EditingView <plugins_editing_editingView>`\ : a plugin that provides core editing view facilities.
- **SEDMLEditingView:** a plugin that provides core `SED-ML <https://sed-ml.github.io/>`__ editing view facilities.

Miscellaneous
-------------

Miscellaneous plugins are plugins that do not fit in any other category:

.. rst-class:: internal reference

   - :ref:`HelpWindow <plugins_miscellaneous_helpWindow>`\ : a plugin to provide help.
   - :ref:`PythonConsoleWindow <plugins_miscellaneous_pythonConsoleWindow>`\ : a plugin to interact with `Python <https://python.org/>`__.
   - :ref:`WebBrowserWindow <plugins_miscellaneous_webBrowserWindow>`\ : a plugin to browse the Web.

There are also some non-selectable Miscellaneous plugins:

.. rst-class:: internal reference

   - **Compiler:** a plugin to support code compilation.
   - :ref:`Core <plugins_miscellaneous_core>`\ : the core plugin.
   - :ref:`JupyterKernel <plugins_miscellaneous_jupyterKernel>`\ : the `Jupyter <https://jupyter.org/>`__ kernel plugin.
   - :ref:`PythonShell <plugins_miscellaneous_pythonShell>`\ : the `Python <https://python.org/>`__ shell plugin.

Organisation
------------

Organisation plugins are used to organise files:

.. rst-class:: internal reference

   - :ref:`FileBrowserWindow <plugins_organisation_fileBrowserWindow>`\ : a plugin to access local files.
   - :ref:`FileOrganiserWindow <plugins_organisation_fileOrganiserWindow>`\ : a plugin to virtually organise files.
   - :ref:`PMRWindow <plugins_organisation_pmrWindow>`\ : a plugin to access `PMR <https://models.physiomeproject.org/>`__.
   - :ref:`PMRWorkspacesWindow <plugins_organisation_pmrWorkspacesWindow>`\ : a plugin to manage a user's `PMR <https://models.physiomeproject.org/>`__ workspaces.

Simulation
----------

Simulation plugins are used to simulate files:

.. rst-class:: internal reference

   - :ref:`SimulationExperimentView <plugins_simulation_simulationExperimentView>`\ : a plugin to edit and run a simulation experiment.

.. _plugins_solver:

Solver
------

Solver plugins are used to access various solvers:

.. rst-class:: internal reference

   - :ref:`CVODESolver <plugins_solver_cvodeSolver>`\ : a plugin that uses `CVODE <https://computing.llnl.gov/projects/sundials/cvode>`__ to solve `ODEs <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__.
   - :ref:`ForwardEulerSolver <plugins_solver_forwardEulerSolver>`\ : a plugin that implements the forward `Euler method <https://en.wikipedia.org/wiki/Euler_method>`__ to solve `ODEs <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__.
   - :ref:`FourthOrderRungeKuttaSolver <plugins_solver_fourthOrderRungeKuttaSolver>`\ : a plugin that implements the fourth-order `Runge-Kutta method <https://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods>`__ to solve `ODEs <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__.
   - :ref:`HeunSolver <plugins_solver_heunSolver>`\ : a plugin that implements the `Heun's method <https://en.wikipedia.org/wiki/Heun's_method>`__ to solve `ODEs <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__.
   - :ref:`KINSOLSolver <plugins_solver_kinsolSolver>`\ : a plugin that uses `KINSOL <https://computing.llnl.gov/projects/sundials/kinsol>`__ to solve `non-linear algebraic systems <https://en.wikipedia.org/wiki/Nonlinear_system#Nonlinear_algebraic_equations>`__.
   - :ref:`SecondOrderRungeKuttaSolver <plugins_solver_secondOrderRungeKuttaSolver>`\ : a plugin that implements the second-order `Runge-Kutta method <https://en.wikipedia.org/wiki/Runge%E2%80%93Kutta_methods>`__ to solve `ODEs <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__.

Support
-------

Non-selectable support plugins are used to support various third-party libraries:

- **CellMLSupport:** a plugin to support `CellML <https://cellml.org/>`__.
- **COMBINESupport:** a plugin to support `COMBINE <https://co.mbine.org/>`__.
- **PMRSupport:** a plugin to support `PMR <https://models.physiomeproject.org/>`__.
- **PythonQtSupport:** a plugin to support `PythonQt <https://mevislab.github.io/pythonqt/>`__.
- **PythonSupport:** a plugin to support `Python <https://python.org/>`__.
- **QScintillaSupport:** a plugin to support `QScintilla <https://riverbankcomputing.com/software/qscintilla/intro>`__.
- **SEDMLSupport:** a plugin to support `SED-ML <https://sed-ml.github.io/>`__.
- **SimulationSupport:** a plugin to support simulations.
- **StandardSupport:** a plugin to support various standards.
- **ZIPSupport:** a plugin to support the `ZIP format <https://en.wikipedia.org/wiki/ZIP_(file_format)>`__.

Third-party
-----------

Non-selectable third-party plugins are used to access to various third-party libraries:

- **CellMLAPI:** a plugin to access the `CellML API <https://github.com/cellmlapi/cellml-api/>`__.
- **libBioSignalML:** a plugin to access BioSignalML.
- **libgit2:** a plugin to access `libgit2 <https://libgit2.github.com/>`__.
- **libNuML:** a plugin to access `libNuML <https://github.com/NuML/NuML/>`__.
- **libSBML:** a plugin to access `libSBML <http://sbml.org/Software/libSBML/>`__.
- **libSEDML:** a plugin to access `libSEDML <https://github.com/fbergmann/libSEDML/>`__.
- **LibXDiff:** a plugin to access `LibXDiff <http://www.xmailserver.org/xdiff-lib.html>`__.
- **LLVMClang:** a plugin to access `LLVM <https://llvm.org/>`__ and `Clang <https://clang.llvm.org/>`__.
- **OAuth:** a plugin to access `OAuth for Qt <https://github.com/pipacs/o2>`__.
- **OpenSSL:** a plugin to access `OpenSSL <https://openssl.org/>`__.
- **Python:** a plugin to access `Python <https://python.org/>`__.
- **PythonPackages:** a plugin to access some `Python <https://python.org/>`__ packages.
- **PythonQt:** a plugin to access `PythonQt <https://mevislab.github.io/pythonqt/>`__.
- **QScintilla:** a plugin to access `QScintilla <https://riverbankcomputing.com/software/qscintilla/intro>`__.
- **Qwt:** a plugin to access `Qwt <https://qwt.sourceforge.io/>`__.
- **SUNDIALS:** a plugin to access the `ARKode <https://computing.llnl.gov/projects/sundials/arkode>`__, `CVODES <https://computing.llnl.gov/projects/sundials/cvodes>`__, `IDAS <https://computing.llnl.gov/projects/sundials/idas>`__, and `KINSOL <https://computing.llnl.gov/projects/sundials/kinsol>`__ solvers from the `SUNDIALS <https://computing.llnl.gov/projects/sundials>`__ library.
- **zlib:** a plugin to access `zlib <https://zlib.net/>`__.

Tools
-----

Tools plugins are used to access to various tools:

.. rst-class:: internal reference

   - :ref:`CellMLTools <plugins_tools_cellmlTools>`\ : a plugin to access various `CellML <https://cellml.org/>`__-related tools.

Widget
------

Non-selectable widget plugins are used to access various *ad hoc* widgets:

.. rst-class:: internal reference

   - **EditorWidget:** a plugin to edit and display text.
   - **GraphPanelWidget:** a plugin to plot graphs.
   - **MathMLViewerWidget:** a plugin to visualise `MathML <https://w3.org/Math>`__ documents.
   - **QScintillaWidget:** a plugin to support `QScintilla <https://riverbankcomputing.com/software/qscintilla/intro>`__.
   - **ToolBarWidget:** a plugin to display a tool bar.
   - **WebViewerWidget:** a plugin to visualise Web documents.
