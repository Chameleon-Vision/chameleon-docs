..  _command-line-arguments:

Command-Line Arguments
======================

Chameleon Vision supports a few command-line arguments to enable or disable certain features, or to change operation parameters.

.. list-table:: Arguments Table
   :widths: 30 30 100
   :header-rows: 1

   * - Argument
     - Parameters
     - Description
   * - ``--nt-servermode``
     - None
     - Enables the internal NetworkTables Server.
   * - ``--nt-client-server``
     - IP address (i.e. ``10.8.32.2``)
     - Sets a manual IP address for the NT Client to connect to.
   * - ``--unmanage-network``
     - None
     - Disables the automatic network settings manager.

| To use this commands add the argument after the run command for example

.. code-block:: bash

  java -jar chameleon-vision.jar --nt-client-server 10.15.77.2