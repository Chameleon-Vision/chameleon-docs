.. _pc-install:

PC testing
================


JDK installation
-----------------

The program requires java JDK version 12 or newer

How do you know that version are you running?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Run java -version in your command line,

You sould get a similar result

.. image:: /images/installation/java-version.png

Installing JDK 12
^^^^^^^^^^^^^^^^^^^
Windows
~~~~~~~~
TBA



Linux
~~~~~~~~~

.. code-block:: bash

	sudo apt update
	sudo apt install bellsoft-java12

Download and run
----------------------------------	

To download the latest .jar file click here_.

.. _here: https://sourceforge.net/projects/chameleon-vision/files/latest/download/

Remame the file you downloaded to chameleon-vision.jar

Open a command line in the folder with the JAR file you just downloaded then run

.. code-block:: bash

	java -jar chameleon-vision.jar --unmanage-network

.. warning::
	
	When running the program on testing computer, use the ``--unmanage-network``  :ref:`argument<command-line-arguments>`
	Otherwise your network settings might be changed

