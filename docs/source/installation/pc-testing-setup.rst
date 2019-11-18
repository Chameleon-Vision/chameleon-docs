.. _pc-install:

PC testing
================


JDK installation
-----------------

The program requires java JDK version 12 or newer

How do you know that version are you running?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Run java -version in your command line,

You should get a similar result

.. image:: /images/installation/java-version.png

Installing JDK 12
^^^^^^^^^^^^^^^^^^^

Windows
~~~~~~~~

Download jdk 12 from this `link <https://www.oracle.com/technetwork/java/javase/downloads/index.html>`_ and install 



Linux
~~~~~~~~~

Follow `this <https://bell-sw.com/pages/liberica_install_guide-12.0.2/>`_ guide 

Download and run
----------------------------------	

To download the latest .jar file click `here
<https://sourceforge.net/projects/chameleon-vision/files/latest/download/>`_

Rename the file you downloaded to chameleon-vision.jar

Open a command line in the folder with the JAR file you just downloaded then run

.. code-block:: bash

	java -jar chameleon-vision.jar --unmanage-network

.. warning::
	
	When running the program on testing computer, use the ``--unmanage-network``  :ref:`argument<command-line-arguments>`
	Otherwise your network settings might be changed

