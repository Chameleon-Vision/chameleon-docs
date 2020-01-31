..  _coprocessor-setup:

Coprocessor Setup
==================

.. note::
    If testing on a separate device, please follow the instructions in :ref:`PC Testing<pc-install>`.

Raspberry Pi
------------

Chameleon Vision can run on most operating systems available for the Raspberry Pi.
However, it is recommended that you install Rasbian Buster Lite, available `here <https://www.raspberrypi.org/downloads/raspbian/>`_.
Follow the `instructions <https://www.raspberrypi.org/documentation/installation/installing-images/>`_ to install Raspbian onto an SD card.

Ensure that the Raspberry Pi is connected via Ethernet to the Internet.
Log in to the Raspberry Pi (username ``pi`` and password ``raspberry``) and run the following commands in the terminal:

.. code-block:: console

    $ wget https://git.io/JeDUk -O install.sh
    $ chmod +x install.sh
    $ sudo ./install.sh
    $ sudo reboot now

Congratulations! Your Raspberry Pi is now set up to run Chameleon Vision!

Once the Raspberry Pi has rebooted, Chameleon Vision can be started with the following command:

.. code-block:: console

    $ sudo java -jar chameleon-vision.jar

When a new version of Chameleon Vision is released, update it by running the following commands:

.. code-block:: console

    $ wget https://git.io/JeDUL -O update.sh
    $ chmod +x update.sh
    $ sudo ./update.sh

Running Chameleon at Startup
----------------------------

An easy way to run Chameleon at startup is through a Cron job. Crontab is a unix program that lets you run different commands periodically, including at startup. To edit the list of Cron jobs, run the command
.. code-block:: console
    $ crontab -e
and pick your favorite text editor (if you don't know which one to use, pick nano).
Go to the end of the file and enter
.. code-block:: console
    @reboot sudo java -jar chameleon-vision.jar
    
as the last line. Exit the file (in nano, this is control+x, and then y to confirm).
This creates a cron job that will run the command to start Chameleon every time you turn on your pi.
