.. _plugins_miscellaneous_jupyterKernel:

======================
 JupyterKernel plugin
======================

The JupyterKernel plugin provides a `Jupyter <https://jupyter.org/>`__ kernel, which is needed by the :ref:`Python shell <plugins_miscellaneous_pythonShell>` plugin.
Although there is a :ref:`CLI <userInterfaces_commandLineInterface>` interface, it is not meant to be used directly.

Kernel
------

A `Jupyter <https://jupyter.org/>`__ kernel can be started by entering the following command:

.. code-block:: shell

   $ ./OpenCOR -c JupyterKernel::kernel kernel.json

where ``kernel.json`` is the `connection file <https://jupyter-client.readthedocs.io/en/latest/kernels.html#connection-files>`__.
