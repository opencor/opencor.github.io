.. _plugins_solver_cvodeSolver:

====================
 CVODESolver plugin
====================

The CVODESolver plugin uses `CVODE <https://computing.llnl.gov/projects/sundials/cvode>`__ to solve `ODEs <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__ and it can be customised through the following properties:

- **Maximum step:** the maximum step used by the solver (default: :math:`0`).

  **Note:** the default value of :math:`0` means that `CVODE <https://computing.llnl.gov/projects/sundials/cvode>`__ will try to use as big a step as possible.

..

- **Maximum number of steps:** the maximum number of (internal) steps used by the solver between two given points (default: :math:`500`).

  **Note:** the default value of :math:`500` should be big enough for most models.
  However, some (very) stiff models may require this value to be increased.

..

- **Integration method:** the integration method used by the solver (default: ``BDF``)

  **Note #1:** ``BDF`` and ``Adams-Moulton`` can be used.

  **Note #2:** ``BDF`` can be used with either stiff or non-stiff models while ``Adams-Moulton`` should only be used with non-stiff models.

..

- **Iteration type:** the type of iteration used by the solver (default: ``Newton``).

  **Note #1:** ``Newton`` and ``Functional`` can be used.

  **Note #2:** ``Newton`` can be used with either stiff or non-stiff models while ``Functional`` should only be used with non-stiff models.

  **Note #3:** to use a ``Newton`` iteration requires solving a system of linear equations and therefore requires specifying a linear solver.

..

- **Linear solver:** the linear solver used by the solver during a ``Newton`` iteration (default: ``Dense``).

  **Note #1:** ``Dense``, ``Banded``, ``Diagonal``, ``GMRES``, ``BiCGStab``, and ``TFQMR`` can be used.

  **Note #2:** ``Banded`` requires specifying both an upper and a lower half-bandwidth value.

  **Note #3:** ``GMRES``, ``BiCGStab``, and ``TFQMR`` require specifying whether to use a preconditioner.

..

- **Preconditioner:** the preconditioner, if any, used by the solver when using a ``GMRES``, ``BiCGStab``, or ``TFQMR`` linear solver during a ``Newton`` iteration (default: ``Banded``).

  **Note #1:** ``Banded`` and ``None`` can be used.

  **Note #2:** ``Banded`` requires specifying both an upper and a lower half-bandwidth value.

..

- **Upper half-bandwidth:** the upper half-bandwidth value used by the ``Banded`` linear solver or preconditioner (default: :math:`0`).

  **Note:** the upper half-bandwidth value must be between :math:`0` and :math:`n-1` with :math:`n` the number of ODEs in the model.

..

- **Lower half-bandwidth:** the lower half-bandwidth value used by the ``Banded`` linear solver or preconditioner (default: :math:`0`).

  **Note:** the lower half-bandwidth value must be between :math:`0` and :math:`n-1` with :math:`n` the number of ODEs in the model.

..

- **Relative tolerance:** the relative tolerance used by the solver (default: :math:`10^{-7}`).

..

- **Absolute tolerance:** the absolute tolerance used by the solver (default: :math:`10^{-7}`).

..

- **Interpolate solution:** whether the solver returns an interpolated solution (default: ``True``).

The default settings should work with most models.
However, some models may require some minor adjustments.
This is the case with cardiac cellular electrophysiological models that need a stimulus protocol to generate an action potential.
Such a protocol is likely to be ignored by `CVODE <https://computing.llnl.gov/projects/sundials/cvode>`__, if **Maximum step** and **Interpolate solution** are set to their default values of :math:`0` and ``True``, respectively.
To address this issue, you can either set **Maximum step** to the length of the stimulus protocol or **Interpolate solution** to ``False``.
The former approach will yield (slightly) less accurate results, but they will be obtained (much) faster.
