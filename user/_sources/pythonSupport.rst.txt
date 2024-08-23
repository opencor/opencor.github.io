.. _pythonSupport:

================
 Python support
================

OpenCOR comes bundled with `Python <https://python.org/>`__, providing OpenCOR with `Python <https://python.org/>`__ support.
The following `Python <https://python.org/>`__ packages are included:

- `Matplotlib <https://matplotlib.org/>`__: a comprehensive library for creating static, animated, and interactive visualizations in `Python <https://python.org/>`__;
- `NumPy <https://numpy.org/>`__: the fundamental package for scientific computing with `Python <https://python.org/>`__; and
- `SciPy <https://scipy.org/>`__: the fundamental algorithms for scientific computing in `Python <https://python.org/>`__.

Some code illustrating the use of the OpenCOR `Python <https://python.org/>`__ module and wrappers can be found `here <https://github.com/opencor/opencor/tree/master/src/plugins/support/PythonSupport/tests/data/>`__.

Install a Python package
------------------------

Additional `Python <https://python.org/>`__ packages can be installed either from the :ref:`CLI <userInterfaces_commandLineInterface>` (using the ``jupyterconsole[.bat]`` :ref:`script <userInterfaces_commandLineInterfacePythonRelatedScriptsJupyterconsole>`) or through the :ref:`GUI <userInterfaces_graphicalUserInterface>` (using the :ref:`Python Console window <plugins_miscellaneous_pythonConsoleWindow>` plugin):

.. code-block:: shell

   !pip install package_name

Python module
-------------

A `Python <https://python.org/>`__ module, ``opencor``, is available and can be used to handle simulations in OpenCOR:

- ``open_simulation(file_name_or_url)``: open and return a ``Simulation`` object for the given local or remote `CellML <https://cellml.org/>`__ file, `SED-ML <https://sed-ml.github.io/>`__ file, or `COMBINE archive <https://co.mbine.org/documents/archive>`__.
- ``close_simulation(simulation)``: close the given ``Simulation`` object.
- ``simulation()``: return the active ``Simulation`` object, if any.

  **Note:** ``simulation()`` is only available when using the :ref:`Python Console window <plugins_miscellaneous_pythonConsoleWindow>` plugin.

Python wrappers
---------------

The following OpenCOR classes have `Python <https://python.org/>`__ wrappers that can be used to handle a simulation, some simulation data, some simulation results, a data store, and a data store variable:

- ``Simulation``:

  - ``clear_results()``: clear the simulation results.
  - ``data()``: return the simulation data as a ``SimulationData`` object.
  - ``issues()``: return a list of issues with the simulation.
  - ``release_all_values()``: release all the values retrieved as a `NumPy array <https://numpy.org/doc/stable/reference/generated/numpy.array.html>`__ (see ``DataStoreVariable.values()``).
  - ``release_values(values)``: release the values retrieved as a `NumPy array <https://numpy.org/doc/stable/reference/generated/numpy.array.html>`__ (see ``DataStoreVariable.values()``).
  - ``reset(all = True)``: reset all the model parameters (``all = True``) or only the state model parameters (``all = False``).
  - ``results()``: return the results as a ``SimulationResults`` object.
  - ``run()``: run the simulation.
  - ``valid()``: return whether the simulation is valid.

..

- ``SimulationData``:

  - ``algebraic()``: return the algebraic values as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreValue`` objects.
  - ``constants()``: return the constant values as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreValue`` objects.
  - ``ending_point()``: return the ending point.
  - ``nla_solver_name()``: return the name of the NLA solver.
  - ``nla_solver_property(name)``: return the value of the given NLA solver property.
  - ``ode_solver_name()``: return the name of the ODE solver.
  - ``ode_solver_property(name)``: return the value of the given ODE solver property.
  - ``point_interval()``: return the point interval.
  - ``rates()``: return the rate values as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreValue`` objects.
  - ``set_ending_point(value)``: set the ending point to the given value.
  - ``set_nla_solver(name)``: set the NLA solver to the given NLA solver name.
  - ``set_nla_solver_property(name, value)``: set the given NLA solver property to the given value.
  - ``set_ode_solver(name)``: set the ODE solver to the given ODE solver name.
  - ``set_ode_solver_property(name, value)``: set the given ODE solver property to the given value.
  - ``set_point_interval(value)``: set the point interval to the given value.
  - ``set_starting_point(value)``: set the starting point to the given value.
  - ``starting_point()``: return the starting point.
  - ``states()``: return the state values as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreValue`` objects.

    **Note:** ``set_ode_solver()``, ``set_ode_solver_property()``, ``set_nla_solver()``, and ``set_nla_solver_property()`` do not currently update the :ref:`GUI <userInterfaces_graphicalUserInterface>`.

..

- ``SimulationResults``:

  - ``algebraic()``: return the algebraic values as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreVariable`` objects.
  - ``constants()``: return the constant values as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreVariable`` objects.
  - ``data_store()``: return the associated data store as a ``DataStore`` object.
  - ``rates()``: return the rate values as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreVariable`` objects.
  - ``states()``: return the state values as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreVariable`` objects.
  - ``voi()``: return the variable of integration as a ``DataStoreVariable`` object.

..

- ``DataStore``:

  - ``variables()``: return the variables as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreVariable`` objects.
  - ``voi()``: return the variable of integration as a ``DataStoreVariable`` object.
  - ``voi_and_variables()``: return the variable of integration and variables as a `Python dictionary <https://docs.python.org/3.7/tutorial/datastructures.html#dictionaries>`__ of ``DataStoreVariable`` objects.

..

- ``DataStoreValue``:

  - ``set_value(value)``: set the value.
  - ``uri()``: return the `URI <https://en.wikipedia.org/wiki/Uniform_Resource_Identifier>`__.
  - ``value()``: return the value.

..

- ``DataStoreVariable``:

  - ``name()``: return the name.
  - ``runs_count()``: return the number of runs.
  - ``type()``: return the type of the variable (``1``: variable of integration, ``2``: state, ``3``: rate, ``4``: constant, ``5``: computed constant, and ``6``: algebraic).
  - ``unit()``: return the unit.
  - ``uri()``: return the `URI <https://en.wikipedia.org/wiki/Uniform_Resource_Identifier>`__.
  - ``value(position, run = -1)``: return the value at the given position and for the given run (``run = -1`` corresponds to the last run).
  - ``values(run = -1)``: return the values for the given run (``run = -1`` corresponds to the last run) as a `NumPy array <https://numpy.org/doc/stable/reference/generated/numpy.array.html>`__.
  - ``values_count(run = -1)``: return the number of values for the given run (``run = -1`` corresponds to the last run).
