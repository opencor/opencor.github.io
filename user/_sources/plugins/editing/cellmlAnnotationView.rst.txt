.. _plugins_editing_cellmlAnnotationView:

=============================
 CellMLAnnotationView plugin
=============================

The CellMLAnnotationView plugin can be used to annotate `CellML <https://cellml.org/>`__ files by associating one or several ontological terms to a given `CellML <https://cellml.org/>`__ element.
To open a `CellML <https://cellml.org/>`__ file that does not contain any annotations gives:

.. image:: pics/CellMLAnnotationViewScreenshot01.png
   :align: center
   :scale: 25%

All the `CellML <https://cellml.org/>`__ elements that can be annotated are listed on the left of the view.
Right click on any of them to get a popup menu, which you can use to expand/collapse all the child nodes, as well as remove the metadata associated with the current `CellML <https://cellml.org/>`__ element or any `CellML <https://cellml.org/>`__ element in the `CellML <https://cellml.org/>`__ file:

.. image:: pics/CellMLAnnotationViewScreenshot02.png
   :align: center
   :scale: 25%

Annotate a CellML element
-------------------------

To annotate, say, the ``sodium_channel`` component, you first need to select it:

.. image:: pics/CellMLAnnotationViewScreenshot03.png
   :align: center
   :scale: 25%

Next, you need to specify a `BioModels.net qualifier <https://co.mbine.
org/standards/qualifiers>`__.
If you do not know which one to use, click on the |oxygenCategoriesApplicationInternet| button to get some information about the current `BioModels.net qualifier <https://co.mbine.
org/standards/qualifiers>`__:

.. |oxygenCategoriesApplicationInternet| image:: ../../pics/oxygen/categories/applications-internet.png
   :class: inlineicon
   :width: 16px

.. image:: pics/CellMLAnnotationViewScreenshot04.png
   :align: center
   :scale: 25%

From there, go through the list of `BioModels.net qualifiers <https://co.mbine.
org/standards/qualifiers>`__ until you find the one that suits your needs best (e.g., ``bio:isVersionOf``):

.. image:: pics/CellMLAnnotationViewScreenshot05.png
   :align: center
   :scale: 25%

Now, you need to retrieve some possible ontological terms to describe the ``sodium_channel`` component.
For this, you need to enter a search term (e.g., ``sodium channel``; note: `regular expressions <https://en.wikipedia.org/wiki/Regular_expression>`__ are supported).
As can be seen, OpenCOR returns 12 possible ontological terms:

.. image:: pics/CellMLAnnotationViewScreenshot06.png
   :align: center
   :scale: 25%

A quick look through the list tells us that you might want to use the one for ``voltage-gated sodium channel complex``.
If you want to know more about the `GO <http://geneontology.org/>`__ resource, you can click on the corresponding link:

.. image:: pics/CellMLAnnotationViewScreenshot07.png
   :align: center
   :scale: 25%

Similarly, if you want to know more about the `GO <http://geneontology.org/>`__ identifier:

.. image:: pics/CellMLAnnotationViewScreenshot08.png
   :align: center
   :scale: 25%

Now, assuming that you are happy with your choice, you can associate the ontological term with the ``sodium_channel`` component by clicking on the corresponding |oxygenActionsListAdd| button:

.. |oxygenActionsListAdd| image:: ../../pics/oxygen/actions/list-add.png
   :class: inlineicon
   :width: 16px

.. image:: pics/CellMLAnnotationViewScreenshot09.png
   :align: center
   :scale: 25%

The ontological term you have added cannot be added anymore, but it can be removed by clicking on the corresponding |oxygenActionsListRemove| button.

.. |oxygenActionsListRemove| image:: ../../pics/oxygen/actions/list-remove.png
   :class: inlineicon
   :width: 16px

Now, say that you also want to add another ontological term.
You can do so by clicking on the corresponding |oxygenActionsListAdd| button, but also by entering its resource-id duple (e.g., ``go/GO:0005248``; i.e. ``<resource>/<id>``) in the term field.
OpenCOR will recognise this "term" as being a resource-id duple and will offer you to add the corresponding ontological term directly:

.. image:: pics/CellMLAnnotationViewScreenshot10.png
   :align: center
   :scale: 25%

Unrecognised annotations
------------------------

Annotations consist of `RDF triples <https://w3.org/TR/rdf-concepts/#section-triples>`__, which are made of a subject, a predicate and an object.
OpenCOR recognises `RDF triples <https://w3.org/TR/rdf-concepts/#section-triples>`__, which subject identifies a `CellML <https://cellml.org/>`__ element while it expects the predicate to be a `BioModels.net qualifier <https://co.mbine.
org/standards/qualifiers>`__ and the object an ontological term.

Ontological terms used to be identified using MIRIAM `URNs <https://en.wikipedia.org/wiki/Uniform_Resource_Name>`__, but these have now been deprecated in favour of `identifiers.org <https://identifiers.org/>`__ `URIs <https://en.wikipedia.org/wiki/Uniform_Resource_Identifier>`__.
OpenCOR recognises both, but it will only serialise annotations using `identifiers.org <https://identifiers.org/>`__ `URIs <https://en.wikipedia.org/wiki/Uniform_Resource_Identifier>`__.

Now, it may happen that a file contains annotations that are not recognised by OpenCOR.
In this case, OpenCOR will display the annotations as a simple list of `RDF triples <https://w3.org/TR/rdf-concepts/#section-triples>`__:

.. image:: pics/CellMLAnnotationViewScreenshot11.png
   :align: center
   :scale: 25%

If you ever come across such a type of annotations and think that OpenCOR ought to recognise it then please do `get in touch <https://opencor.ws/contactUs.html>`__.
