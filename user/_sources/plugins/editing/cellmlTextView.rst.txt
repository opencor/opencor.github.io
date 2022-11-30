.. _plugins_editing_cellmlTextView:

=======================
 CellMLTextView plugin
=======================

The CellMLTextView plugin can be used to edit `CellML <https://cellml.org/>`__ files using a text editor that supports the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>`.
If you open a `CellML <https://cellml.org/>`__ file, it will look something like:

.. image:: pics/CellMLTextViewScreenshot01.png
   :align: center
   :scale: 25%

Apart from using a specific format, the view has the same features as the :ref:`Raw CellML <plugins_editing_rawCellMLView>` view with one exception: ``CellML Validation`` only validates against the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>`, not `CellML <https://cellml.org/>`__ *per se*.

Compatibility with COR
----------------------

People familiar with `COR <https://opencor.ws/cor>`__ will find that the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>` is compatible with the COR format, although it supports additional features:

- :ref:`Comments <plugins_editing_cellmlTextView_comments>`;
- The ``import`` element (i.e. support for `CellML 1.1 <https://cellml.org/specifications/cellml_1.1>`__);
- The ``cmeta:id`` attribute on all `CellML <https://cellml.org/>`__ elements (i.e. support for `CellML <https://cellml.org/>`__ annotation);
- The ``degree`` qualifier for the ``diff`` element (i.e. support for higher-order derivatives);
- The ``notanumber`` and ``infinity`` constants; and
- An unlimited number of group types (in `COR <https://opencor.ws/cor>`__, a group can only specify one ``encapsulation`` and/or one ``containment`` type).

However, note that the COR format has some limitations that are also present in the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>`:

- The ``reaction`` element is not supported (its use is not only discouraged, but it has also been removed from `CellML 2.0 <https://cellml.org/specifications/cellml_2.0>`__, which is not yet supported by OpenCOR);
- A ``component`` element may contain a set of ``math`` elements, but when serialised back, only one ``math`` element will remain, with all the equations in that one and unique ``math`` element.

.. _plugins_editing_cellmlTextView_comments:

Comments
--------

You can (un)comment a piece of code by pressing ``Ctrl``\ +\ ``/``.
If no text is selected or if it consists of one or several full lines then the comment will be rendered as ``// XXX``.
For instance:

.. code-block:: cellmlText

   def model my_model as
       // A single line comment
       ...
   enddef;

Alternatively, if one or several lines are partially selected then the comment will be rendered as ``/* XXX */``.
For instance:

.. code-block:: cellmlText

   def model my/*_super_duper*/_model as
       ...
   enddef;

Note that ``/* XXX */`` comments are only for convenience and are not serialised back to `CellML <https://cellml.org/>`__.
Indeed, such comments can be inserted anywhere, including within an equation.
For instance:

.. code-block:: cellmlText

   ode(V, time) = -(i_Na+i_K+i_Leak/*+i_Stim*/)/Cm;

It is therefore impossible to determine where such comments should be included when serialised back.

``// XXX`` comments can also be inserted anywhere, but unlike ``/* XXX */`` comments they are serialised back.
However, the rendering of certain elements is such that when serialised back, ``// XXX`` comments may be included in the parent element of those elements, and either before or after those elements, depending on the situation.

.. _plugins_editing_cellmlTextView_cellmlTextFormat:

CellML Text format
------------------

The :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>` offers, for the large part, a one-to-one mapping to the `CellML <https://cellml.org/>`__ format with the view of making it easier to create and edit `CellML <https://cellml.org/>`__ files.

Model structure
~~~~~~~~~~~~~~~

To define a model of name ``my_model``, we use:

.. code-block:: cellmlText

   def model my_model as
       ...
   enddef;

The model definition sits between ``as`` and ``enddef;``, and can consist of :ref:`imports <plugins_editing_cellmlTextView_imports>`, :ref:`unit definitions <plugins_editing_cellmlTextView_unitDefinitions>`, :ref:`component definitions <plugins_editing_cellmlTextView_componentDefinitions>`, :ref:`group definitions <plugins_editing_cellmlTextView_groupDefinitions>`, and :ref:`mapping definitions <plugins_editing_cellmlTextView_mappingDefinitions>`.

.. _plugins_editing_cellmlTextView_imports:

Imports
~~~~~~~

To define an import for units and components defined in a `CellML <https://cellml.org/>`__ file, which `URI <https://en.wikipedia.org/wiki/Uniform_resource_identifier>`__ is ``my_imported_model_uri``, we would use:

.. code-block:: cellmlText

   def import using "my_imported_model_uri" for
       ...
   enddef;

To import a unit originally named ``my_reference_unit`` and renamed ``my_imported_unit`` in our model, we would use:

.. code-block:: cellmlText

   unit my_imported_unit using unit my_reference_unit;

Similarly, to import a component originally named ``my_reference_component`` and renamed ``my_imported_component`` in our model, we would use:

.. code-block:: cellmlText

   comp my_imported_component using comp my_reference_component;

Putting everything together, we would have:

.. code-block:: cellmlText

   def import using "my_imported_model_uri" for
       unit my_imported_unit using unit my_reference_unit;
       comp my_imported_component using comp my_reference_component;
   enddef;

.. _plugins_editing_cellmlTextView_unitDefinitions:

Unit definitions
~~~~~~~~~~~~~~~~

To define a base unit of name ``my_base_unit``, we would use:

.. code-block:: cellmlText

   def unit my_base_unit as base unit;

To define a unit of name ``my_unit``, based on some other units, we would use:

.. code-block:: cellmlText

   def unit my_unit as
       unit my_other_unit {...};
       unit second {...};
       unit litre {...};
       unit volt {...};
       ...
   enddef;

``my_other_unit`` refers to a user-defined unit while ``second`` is an `SI <https://en.wikipedia.org/wiki/International_System_of_Units>`__ base unit, ``litre`` a convenience unit and ``volt`` an `SI <https://en.wikipedia.org/wiki/International_System_of_Units>`__-derived unit .
The following `SI <https://en.wikipedia.org/wiki/International_System_of_Units>`__ base (in bold) and -derived units, as well as convenience units (in italics), can be used:

.. table::
   :class: units

   +------------+------------+--------------+----------+---------+-----------------+
   | **ampere** | becquerel  | **candela**  | celsius  | coulomb | *dimensionless* |
   +------------+------------+--------------+----------+---------+-----------------+
   |   farad    |   *gram*   |     gray     |  henry   |  hertz  |      joule      |
   +------------+------------+--------------+----------+---------+-----------------+
   |   katal    | **kelvin** | **kilogram** | *liter*  | *litre* |      lumen      |
   +------------+------------+--------------+----------+---------+-----------------+
   |    lux     | **meter**  |  **metre**   | **mole** | newton  |       ohm       |
   +------------+------------+--------------+----------+---------+-----------------+
   |   pascal   |   radian   |  **second**  | siemens  | sievert |    steradian    |
   +------------+------------+--------------+----------+---------+-----------------+
   |   tesla    |    volt    |     watt     |  weber   |         |                 |
   +------------+------------+--------------+----------+---------+-----------------+

Additional information can be provided within curly brackets.
Thus, ``prefix``, ``exponent``, ``multiplier``, and ``offset`` values of :math:`p`, :math:`e`, :math:`m`, and :math:`o` can be used on a unit :math:`u` to define a new unit equal to :math:`m \cdot (p \cdot u)^e+o`.
For example, to define ``my_unit`` as being equal to :math:`3 \cdot (milli \cdot my\_other\_unit)^{-1}+7`, we would use:

.. code-block:: cellmlText

   def unit my_unit as
       unit my_other_unit {pref: milli, expo: -1, mult: 3, off: 7};
   enddef;

By default, ``pref``, ``expo``, ``mult``, and ``off`` have a value of :math:`0`, :math:`1.0`, :math:`1.0`, and :math:`0.0`, respectively.
``pref`` can either be an integer or have any of the following values:

.. table::
   :class: prefixes

   +-------+-----------------+-------+------------------+
   | yotta | :math:`10^{24}` | deci  | :math:`10^{-1}`  |
   +-------+-----------------+-------+------------------+
   | zetta | :math:`10^{21}` | centi | :math:`10^{-2}`  |
   +-------+-----------------+-------+------------------+
   | exa   | :math:`10^{18}` | milli | :math:`10^{-3}`  |
   +-------+-----------------+-------+------------------+
   | peta  | :math:`10^{15}` | micro | :math:`10^{-6}`  |
   +-------+-----------------+-------+------------------+
   | tera  | :math:`10^{12}` | nano  | :math:`10^{-9}`  |
   +-------+-----------------+-------+------------------+
   | giga  | :math:`10^{9}`  | pico  | :math:`10^{-12}` |
   +-------+-----------------+-------+------------------+
   | mega  | :math:`10^{6}`  | femto | :math:`10^{-15}` |
   +-------+-----------------+-------+------------------+
   | kilo  | :math:`10^{3}`  | atto  | :math:`10^{-18}` |
   +-------+-----------------+-------+------------------+
   | hecto | :math:`10^{2}`  | zepto | :math:`10^{-21}` |
   +-------+-----------------+-------+------------------+
   | deka  | :math:`10^{1}`  | yocto | :math:`10^{-24}` |
   +-------+-----------------+-------+------------------+

.. _plugins_editing_cellmlTextView_componentDefinitions:

Component definitions
~~~~~~~~~~~~~~~~~~~~~

To define a component of name ``my_component``, we would use:

.. code-block:: cellmlText

   def comp my_component as
       ...
   enddef;

The component definition sits between ``as`` and ``enddef;``, and can consist of :ref:`unit definitions <plugins_editing_cellmlTextView_unitDefinitions>`, :ref:`variable definitions <plugins_editing_cellmlTextView_variableDefinitions>`, and :ref:`mathematical equations <plugins_editing_cellmlTextView_mathematicalEquations>`.

.. _plugins_editing_cellmlTextView_variableDefinitions:

Variable definitions
~~~~~~~~~~~~~~~~~~~~

To define a variable of name ``my_variable`` and of unit ``my_unit``, we would use:

.. code-block:: cellmlText

   var my_variable: my_unit {...};

Additional information can be provided within curly brackets: an initial value, a public interface, and/or a private interface.
For example, to initialise ``my_variable`` to :math:`3` and set its public and private interfaces to ``in`` and ``out``, respectively, we would use:

.. code-block:: cellmlText

   var my_variable: my_unit {init: 3, pub: in, priv: out};

By default, ``init`` has no value (i.e. the variable is not initialised) while ``pub`` and ``priv`` have a value of ``none`` (i.e. the variable belongs to the current component and is not visible to other components in the model).
``init`` can either take a real number as a value or the name of a variable defined in the current component.
Both ``pub`` and ``priv`` can take any of the following values: ``none``, ``in``, or ``out``.

.. _plugins_editing_cellmlTextView_mathematicalEquations:

Mathematical equations
~~~~~~~~~~~~~~~~~~~~~~

A mathematical equation must either have an identifier or an `ODE <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__ on its left hand side, i.e. :math:`x=...` or :math:`\frac{dx}{dt}=...`, respectively.
To write such equations, we would use:

.. code-block:: cellmlText

   x = ...;

and

.. code-block:: cellmlText

   ode(x, t) = ...;

The `ODE <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__ is a first-order `ODE <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__ and could also be written:

.. code-block:: cellmlText

   ode(x, t, 1{dimensionless})

As can be seen, the order of the `ODE <https://en.wikipedia.org/wiki/Ordinary_differential_equation>`__ is specified using a constant value of unit ``dimensionless``, which means that to have :math:`\frac{d^2 x}{dt^2}`, :math:`\frac{d^3 x}{dt^3}`, etc., we would use:

.. code-block:: cellmlText

   ode(x, t, 2{dimensionless})
   ode(x, t, 3{dimensionless})
   ...

The right-hand side of an equation can use any of the following mathematical operators, elements and constants:

- Relational operators:

  .. table::
     :class: mathematics

     +--------+--------------------------+----------------------------+
     | ``=``  | Equality (assignment)    | .. code-block:: cellmlText |
     |        |                          |                            |
     |        |                          |    x = y                   |
     +--------+--------------------------+----------------------------+
     | ``==`` | Equality (binary)        | .. code-block:: cellmlText |
     |        |                          |                            |
     |        |                          |    x == y                  |
     +--------+--------------------------+----------------------------+
     | ``<>`` | Inequality               | .. code-block:: cellmlText |
     |        |                          |                            |
     |        |                          |    x <> y                  |
     +--------+--------------------------+----------------------------+
     | ``>``  | Greater than             | .. code-block:: cellmlText |
     |        |                          |                            |
     |        |                          |    x > y                   |
     +--------+--------------------------+----------------------------+
     | ``<``  | Lower than               | .. code-block:: cellmlText |
     |        |                          |                            |
     |        |                          |    x < y                   |
     +--------+--------------------------+----------------------------+
     | ``>=`` | Greater than or equal to | .. code-block:: cellmlText |
     |        |                          |                            |
     |        |                          |    x >= y                  |
     +--------+--------------------------+----------------------------+
     | ``<=`` | Lower than or equal to   | .. code-block:: cellmlText |
     |        |                          |                            |
     |        |                          |    x <= y                  |
     +--------+--------------------------+----------------------------+

- Arithmetic operators:

  .. table::
     :class: mathematics

     +-----------+--------------------------+------------------------------+
     | ``+``     | Addition                 | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    x+y                       |
     +-----------+--------------------------+------------------------------+
     | ``-``     | Subtraction              | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    x-y                       |
     +-----------+--------------------------+------------------------------+
     | ``*``     | Multiplication           | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    x*y                       |
     +-----------+--------------------------+------------------------------+
     | ``/``     | Division                 | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    x/y                       |
     +-----------+--------------------------+------------------------------+
     | ``pow``   | Exponentiation (generic) | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    pow(x, 3{dimensionless})  |
     |           |                          |    pow(x, y)                 |
     +-----------+--------------------------+------------------------------+
     | ``sqr``   | Exponentiation (square)  | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    sqr(x)                    |
     +-----------+--------------------------+------------------------------+
     | ``root``  | Root (generic)           | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    root(x, 3{dimensionless}) |
     |           |                          |    root(x, y)                |
     +-----------+--------------------------+------------------------------+
     | ``sqrt``  | Root (square)            | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    sqrt(x)                   |
     +-----------+--------------------------+------------------------------+
     | ``abs``   | Absolute value           | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    abs(x)                    |
     +-----------+--------------------------+------------------------------+
     | ``exp``   | Exponential              | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    exp(x)                    |
     +-----------+--------------------------+------------------------------+
     | ``ln``    | Natural logarithm        | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    ln(x)                     |
     +-----------+--------------------------+------------------------------+
     | ``log``   | Logarithm                | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    log(x)                    |
     |           |                          |    log(x, 3{dimensionless})  |
     |           |                          |    log(x, y)                 |
     +-----------+--------------------------+------------------------------+
     | ``floor`` | Floor                    | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    floor(x)                  |
     +-----------+--------------------------+------------------------------+
     | ``ceil``  | Ceiling                  | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    ceil(x)                   |
     +-----------+--------------------------+------------------------------+
     | ``fact``  | Factorial                | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    fact(x)                   |
     +-----------+--------------------------+------------------------------+
     | ``rem``   | Remainder                | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    rem(x, 3{dimensionless})  |
     |           |                          |    rem(x, y)                 |
     +-----------+--------------------------+------------------------------+
     | ``min``   | Minimum                  | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    min(x, 3{dimensionless})  |
     |           |                          |    min(x, y)                 |
     |           |                          |    min(x, y, z)              |
     +-----------+--------------------------+------------------------------+
     | ``max``   | Maximum                  | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    max(x, 3{dimensionless})  |
     |           |                          |    max(x, y)                 |
     |           |                          |    max(x, y, z)              |
     +-----------+--------------------------+------------------------------+
     | ``gcd``   | Greatest common divisor  | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    gcd(x, 3{dimensionless})  |
     |           |                          |    gcd(x, y)                 |
     |           |                          |    gcd(x, y, z)              |
     +-----------+--------------------------+------------------------------+
     | ``lcm``   | Least common multiple    | .. code-block:: cellmlText   |
     |           |                          |                              |
     |           |                          |    lcm(x, 3{dimensionless})  |
     |           |                          |    lcm(x, y)                 |
     |           |                          |    lcm(x, y, z)              |
     +-----------+--------------------------+------------------------------+

- Logical operators:

  .. table::
     :class: mathematics

     +-----------+--------------+------------------------------+
     | ``and``   | And          | .. code-block:: cellmlText   |
     |           |              |                              |
     |           |              |    x and y                   |
     +-----------+--------------+------------------------------+
     | ``or``    | Or           | .. code-block:: cellmlText   |
     |           |              |                              |
     |           |              |    x or y                    |
     +-----------+--------------+------------------------------+
     | ``xor``   | Exclusive or | .. code-block:: cellmlText   |
     |           |              |                              |
     |           |              |    x xor y                   |
     +-----------+--------------+------------------------------+
     | ``not``   | Not          | .. code-block:: cellmlText   |
     |           |              |                              |
     |           |              |    not x                     |
     |           |              |    not(x and y)              |
     +-----------+--------------+------------------------------+

- Calculus elements:

  .. table::
     :class: mathematics

     +-----------+-----------------+--------------------------------+
     | ``ode``   | Differentiation | .. code-block:: cellmlText     |
     |           |                 |                                |
     |           |                 |    ode(x, t)                   |
     |           |                 |    ode(x, t, 2{dimensionless}) |
     +-----------+-----------------+--------------------------------+

- Trigonometric operators:

  .. table::
     :class: mathematics

     +-------------+--------------------------------+----------------------------+
     | | ``sin``   | | Sine                         | .. code-block:: cellmlText |
     | | ``sinh``  | | Hyperbolic sine              |                            |
     | | ``asin``  | | Inverse sine                 |    sin(x)                  |
     | | ``asinh`` | | Inverse hyperbolic sine      |    sinh(x)                 |
     |             |                                |    asin(x)                 |
     |             |                                |    asinh(x)                |
     +-------------+--------------------------------+----------------------------+
     | | ``cos``   | | Cosine                       | .. code-block:: cellmlText |
     | | ``cosh``  | | Hyperbolic cosine            |                            |
     | | ``acos``  | | Inverse cosine               |    cos(x)                  |
     | | ``acosh`` | | Inverse hyperbolic cosine    |    cosh(x)                 |
     |             |                                |    acos(x)                 |
     |             |                                |    acosh(x)                |
     +-------------+--------------------------------+----------------------------+
     | | ``tan``   | | Tangent                      | .. code-block:: cellmlText |
     | | ``tanh``  | | Hyperbolic tangent           |                            |
     | | ``atan``  | | Inverse tangent              |    tan(x)                  |
     | | ``atanh`` | | Inverse hyperbolic tangent   |    tanh(x)                 |
     |             |                                |    atan(x)                 |
     |             |                                |    atanh(x)                |
     +-------------+--------------------------------+----------------------------+
     | | ``sec``   | | Secant                       | .. code-block:: cellmlText |
     | | ``sech``  | | Hyperbolic secant            |                            |
     | | ``asec``  | | Inverse secant               |    sec(x)                  |
     | | ``asech`` | | Inverse hyperbolic secant    |    sech(x)                 |
     |             |                                |    asec(x)                 |
     |             |                                |    asech(x)                |
     +-------------+--------------------------------+----------------------------+
     | | ``csc``   | | Cosecant                     | .. code-block:: cellmlText |
     | | ``csch``  | | Hyperbolic cosecant          |                            |
     | | ``acsc``  | | Inverse cosecant             |    csc(x)                  |
     | | ``acsch`` | | Inverse hyperbolic cosecant  |    csch(x)                 |
     |             |                                |    acsc(x)                 |
     |             |                                |    acsch(x)                |
     +-------------+--------------------------------+----------------------------+
     | | ``cot``   | | Cotangent                    | .. code-block:: cellmlText |
     | | ``coth``  | | Hyperbolic cotangent         |                            |
     | | ``acot``  | | Inverse cotangent            |    cot(x)                  |
     | | ``acoth`` | | Inverse hyperbolic cotangent |    coth(x)                 |
     |             |                                |    acot(x)                 |
     |             |                                |    acoth(x)                |
     +-------------+--------------------------------+----------------------------+

- Constants:

  .. table::
     :class: mathematics

     +-----------+----------------+----------------------------+
     | ``true``  | True           | .. code-block:: cellmlText |
     |           |                |                            |
     |           |                |    true                    |
     +-----------+----------------+----------------------------+
     | ``false`` | False          | .. code-block:: cellmlText |
     |           |                |                            |
     |           |                |    false                   |
     +-----------+----------------+----------------------------+
     | ``nan``   | Not a number   | .. code-block:: cellmlText |
     |           |                |                            |
     |           |                |    nan                     |
     +-----------+----------------+----------------------------+
     | ``pi``    | Pi             | .. code-block:: cellmlText |
     |           |                |                            |
     |           |                |    pi                      |
     +-----------+----------------+----------------------------+
     | ``inf``   | Infinity       | .. code-block:: cellmlText |
     |           |                |                            |
     |           |                |    inf                     |
     +-----------+----------------+----------------------------+
     | ``e``     | Euler's number | .. code-block:: cellmlText |
     |           |                |                            |
     |           |                |    e                       |
     +-----------+----------------+----------------------------+

A piecewise statement can also be used.
For example, to define :math:`x` as being equal to :math:`y+z` when :math:`x > 0` and :math:`y-z` otherwise, we would use:

.. code-block:: cellmlText

   x = sel
       case x > 0{dimensionless}:
           y+z;
       otherwise:
           y-z;
   endsel;

or

.. code-block:: cellmlText

   x = sel(case x > 0{dimensionless}: y+z, otherwise: y-z);

The two syntaxes are equivalent, except that the former syntax can only be used in the top-level (of the right-hand side) of an equation while the latter syntax can be used anywhere (on the right hand-side of an equation).

.. _plugins_editing_cellmlTextView_groupDefinitions:

Group definitions
~~~~~~~~~~~~~~~~~

To define a group, we would use:

.. code-block:: cellmlText

   def group as ... for
       ...
   enddef;

A group must be typed as a containment and/or an encapsulation.
For example, to define a containment group, we would use:

.. code-block:: cellmlText

   def group as containment for
       ...
   enddef;

A containment group can be named.
For example, to define a containment group of name ``my_containment``, we would use:

.. code-block:: cellmlText

   def group as containment my_containment for
       ...
   enddef;

An encapsulation group is always nameless, so to define an encapsulation group, we would use:

.. code-block:: cellmlText

   def group as encapsulation for
       ...
   enddef;

A group can have more than one type.
For example, to define a group as both an encapsulation group and a containment group (of name ``my_containment``), we would use:

.. code-block:: cellmlText

   def group as encapsulation and containment my_containment for
       ...
   enddef;

A group definition is used whenever there is a need for a hierarchy of components.
Some components may include others.
For example, to define a group where both ``my_component1`` and ``my_component2`` are at the top level, and where ``my_component1`` includes ``my_component11``, ``my_component12`` and ``my_component13``, we would use:

.. code-block:: cellmlText

   def group as ... for
       comp my_component1 incl
           comp my_component11;
           comp my_component12;
           comp my_component13;
       endcomp;

       comp my_component2;
   enddef;

Similarly, to define a group where ``my_component1`` is at the top level, where ``my_component1`` includes both ``my_component11`` and ``my_component12``, and where ``my_component11`` includes ``my_component111``, we would use:

.. code-block:: cellmlText

   def group as ... for
       comp my_component1 incl
           comp my_component11 incl
               comp my_component111;
           endcomp;

           comp my_component12;
       endcomp;
   enddef;

.. _plugins_editing_cellmlTextView_mappingDefinitions:

Mapping definitions
~~~~~~~~~~~~~~~~~~~

To define some mappings between two components of name ``my_component1`` and ``my_component2``, we would use:

.. code-block:: cellmlText

   def map between my_component1 and my_component2 for
       ...
   enddef;

To map variables ``my_variable1a`` with ``my_variable2a``, ``my_variable1b`` with ``my_variable2b``, and ``my_variable1c`` with ``my_variable2c`` for components ``my_component1`` and ``my_component2``, respectively, we would use:

.. code-block:: cellmlText

   def map between my_component1 and my_component2 for
       vars my_variable1a and my_variable2a;
       vars my_variable1b and my_variable2b;
       vars my_variable1c and my_variable2c;
   enddef;

.. _plugins_editing_cellmlTextView_metadata:

Metadata
~~~~~~~~

The :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>` does not support the editing of `CellML <https://cellml.org/>`__ annotations.
However, ``cmeta:id``'s are used to make the link between `CellML <https://cellml.org/>`__ elements and `CellML <https://cellml.org/>`__ annotations.
So, we need the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>` to support the use of ``cmeta:id``'s and this is done by enclosing a ``cmeta:id`` value (e.g., ``my_cmeta_id``) within curly brackets:

.. code-block:: cellmlText

   {my_cmeta_id}

which can then be used to annotate various `CellML <https://cellml.org/>`__ elements:

.. code-block:: cellmlText

   def model{my_model_cmeta_id} my_model as
       def import{my_import_cmeta_id} using "my_imported_model_uri" for
           unit{my_imported_unit_cmeta_id} my_imported_unit using unit my_reference_unit;

           comp{my_imported_component_cmeta_id} my_imported_component using comp my_reference_component;
       enddef;

       def unit{my_base_unit_cmeta_id} my_base_unit as base unit;

       def unit{my_unit_cmeta_id} my_unit as
           unit{my_other_unit_cmeta_id} my_other_unit {pref: milli, expo: -1, mult: 3, off: 7};
       enddef;

       def comp{my_component_cmeta_id} my_component as
           var{my_variable_cmeta_id} my_variable: my_unit {init: 3, pub: in, priv: out};

           a ={my_algebraic_equation_cmeta_id} b+c;
           ode(d, t) ={my_ode_equation_cmeta_id} e+f;
       enddef;

       def group{my_group_cmeta_id} as encapsulation{my_encapsulation_cmeta_id} and containment{my_containment_cmeta_id} my_containment for
           comp{my_component1_cmeta_id} my_component1 incl
               comp{my_component11_cmeta_id} my_component11;
               comp{my_component12_cmeta_id} my_component12;
               comp{my_component13_cmeta_id} my_component13;
           endcomp;

           comp{my_component2_cmeta_id} my_component2;
       enddef;

       def map{my_map_cmeta_id} between{my_between_cmeta_id} my_component1 and my_component2 for
           vars{my_varsa_cmeta_id} my_variable1a and my_variable2a;
           vars{my_varsb_cmeta_id} my_variable1b and my_variable2b;
           vars{my_varsc_cmeta_id} my_variable1c and my_variable2c;
       enddef;
   enddef;

CLI support
-----------

The CellMLTextView plugin relies on the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>`.
CLI support has therefore been added to it so that a `CellML <https://cellml.org/>`__ file can, from the command line, be imported to the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>`, and back.

For example, to import ``models/van_der_pol_model_1928.cellml`` to the :ref:`CellML Text format <plugins_editing_cellmlTextView_cellmlTextFormat>`, we would do the following:

::

   $ ./OpenCOR -c CellMLTextView::import models/van_der_pol_model_1928.cellml
   def model van_der_pol_model_1928 as
       def comp main as
           def unit per_second as
               unit second {expo: -1};
           enddef;

           var time: second;
           var x: dimensionless {init: -2};
           var y: dimensionless {init: 0};
           var epsilon: dimensionless {init: 1};

           ode(x, time) = y*1{per_second};
           ode(y, time) = (epsilon*(1{dimensionless}-sqr(x))*y-x)*1{per_second};
       enddef;
   enddef;

Similarly, and assuming the above import has been saved to a file named ``van_der_pol_model_1928.txt``, we could get our original `CellML <https://cellml.org/>`__ file by doing the following:

::

   $ ./OpenCOR -c CellMLTextView::export van_der_pol_model_1928.txt > van_der_pol_model_1928.cellml

For precaution, the new `CellML <https://cellml.org/>`__ file relies on `CellML 1.1 <https://cellml.org/specifications/cellml_1.1>`__, as confirmed by ``diff``:

::

   $ diff models/van_der_pol_model_1928.cellml van_der_pol_model_1928.cellml
   2c2
   < <model name="van_der_pol_model_1928" xmlns="http://www.cellml.org/cellml/1.0#" xmlns:cellml="http://www.cellml.org/cellml/1.0#">
   ---
   > <model name="van_der_pol_model_1928" xmlns="http://www.cellml.org/cellml/1.1#" xmlns:cellml="http://www.cellml.org/cellml/1.1#">
