.. _plugins_tools_cellmlTools:

====================
 CellMLTools plugin
====================

The CellMLTools plugin consists of various `CellML <https://cellml.org/>`__-related tools, which can be accessed both through the :ref:`CLI <userInterfaces_commandLineInterface>` and the :ref:`GUI <userInterfaces_graphicalUserInterface>`.

CellML file export
------------------

A CellML file can be exported to different:

- formats:

  - `CellML 1.0 <https://www.cellml.org/specifications/cellml_1.0>`__

- languages:

  - `C <https://en.wikipedia.org/wiki/C_(programming_language)>`__
  - `FORTRAN 77 <https://en.wikipedia.org/wiki/Fortran#FORTRAN_77>`__
  - `MATLAB <https://en.wikipedia.org/wiki/MATLAB>`__
  - `Python <https://en.wikipedia.org/wiki/Python_(programming_language)>`__

An export can be initiated by selecting the ``Tools`` | ``CellML File Export To`` menu or by entering the following command:

.. code-block:: shell

   $ ./OpenCOR -c CellMLTools::export <file> <format>|<language>

with ``<file>`` either a local or a remote file and ``<format>``/``<language>`` taking one of the following values:

- ``<format>``:

  - ``cellml_1_0``: to export a `CellML 1.1 <https://www.cellml.org/specifications/cellml_1.1>`__ file to CellML 1.0

- ``<language>``:

  - ``c``: to export a CellML file to C
  - ``fortran_77``: to export a CellML file to FORTRAN 77
  - ``matlab``: to export a CellML file to MATLAB
  - ``python``: to export a CellML file to Python

Thus, to export ``myfile.cellml`` to CellML 1.0, you would use:

.. code-block:: shell

   $ ./OpenCOR -c CellMLTools::export myfile.cellml cellml_1_0

while to export ``https://mydomain.com/myfile.cellml`` to Python, you would use:

.. code-block:: shell

   $ ./OpenCOR -c CellMLTools::export https://mydomain.com/myfile.cellml python

|
| **Note #1:** the CellML 1.0 export is adapted from `Jonathan Cooper's CellML 1.1 to 1.0 converter <https://cellml.org/tools/jonathan-cooper-s-cellml-1-1-to-1-0-converter/versionconverter-tar.bz2/view>`__ and therefore has the same limitations.
| **Note #2:** the export to different languages is done using the `CellML API <https://github.com/cellmlapi/cellml-api/>`__.
  It should be fine in most cases, but be aware that there may be issues.
  For instance, in a MATLAB export, if a model defines an `ODE <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__ as a constant, say ``dX/dt = 0``, then the exporter will export ``0`` as a constant of value ``0``.
  Then, due to 0- *vs.* 1-based indexing, that constant gets computed twice if there are other constants in the model.
  The end result is that ``dX/dt`` is not equal to ``0`` but to the value of the other constant.

Validate CellML file
--------------------

The validation of a `CellML <https://cellml.org/>`__ file can be done by entering the following command:

.. code-block:: shell

   $ ./OpenCOR -c CellMLTools::validate myfile.cellml

Both errors and warnings, if any, get listed and an exit code value of ``0`` means that the `CellML <https://cellml.org/>`__ file is valid (i.e. no errors were found).
