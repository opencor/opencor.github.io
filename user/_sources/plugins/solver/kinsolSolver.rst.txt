.. _plugins_solver_kinsolSolver:

=====================
 KINSOLSolver plugin
=====================

The KINSOLSolver plugin uses `KINSOL <https://computing.llnl.gov/projects/sundials/kinsol>`__ to solve systems of `non-linear algebraic <https://en.wikipedia.org/wiki/Nonlinear_system#Nonlinear_algebraic_equations>`__ (NLA) equations and it can be customised through the following properties:

- **Maximum number of iterations:** the maximum number of iterations used by the solver to solve the system (default: :math:`200`).

..

- **Linear solver:** the linear solver used by the solver (default: ``Dense``).

  **Note #1:** ``Dense``, ``Banded``, ``GMRES``, ``BiCGStab``, and ``TFQMR`` can be used.

  **Note #2:** ``Banded`` requires specifying both an upper and a lower half-bandwidth value.

..

- **Upper half-bandwidth:** the upper half-bandwidth value used by the ``Banded`` linear solver (default: :math:`0`).

  **Note:** the upper half-bandwidth value must be between :math:`0` and :math:`n-1` with :math:`n` the number of NLA equations in the system.

..

- **Lower half-bandwidth:** the lower half-bandwidth value used by the ``Banded`` linear solver (default: :math:`0`).

  **Note:** the lower half-bandwidth value must be between :math:`0` and :math:`n-1` with :math:`n` the number of NLA equations in the system.
