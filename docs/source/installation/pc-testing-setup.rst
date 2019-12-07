.. _pc-install:

PC Testing
================


JDK Installation
-----------------

Chameleon Vision requires JDK Version 12 or newer.
To check whether you are running a compatible version, type ``$ java --version``. 
You should see a result similar to the one below:

.. code-block:: console

	$ java --version
	java version "12.0.2" 2019-07-07
	Java(TM) SE Runtime Environment (build 12.0.2+10)
	Java HotSpot(TM) 64-bit Server VM (build 12.0.2+10, mixed mode, sharing)

If your version is older than JDK 12, follow the instructions below.

Installing JDK 12
^^^^^^^^^^^^^^^^^^^

Windows
~~~~~~~~~

Download and run the installer from the `oracle website <https://www.oracle.com/technetwork/java/javase/downloads/index.html>`_ and follow the installation instructions.

Linux
~~~~~~~~~

Follow `this <https://bell-sw.com/pages/liberica_install_guide-12.0.2/>`_ guide.

Installing Chameleon Vision
-----------------------------

Chameleon Vision is available for download from the `GitHub repository. <https://github.com/Chameleon-Vision/chameleon-vision/releases>`_.
The file should be named ``chameleon-vision-X.X-RELEASE.jar``, varying with the current version number.

Then, open a terminal in the folder with the downloaded JAR file and run the following command, replacing ``X.X`` with the latest version number.

.. code-block:: console

	$ java -jar chameleon-vision-X.X-RELEASE.jar --unmanage-network

.. warning::

	Take care to use the ``--unmanage-network`` :ref:`argument<command-line-arguments>`, as without it it will change your network setup.
