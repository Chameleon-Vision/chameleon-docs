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

Run on Startup With Systemd
---------------------------

Create a Service

.. code-block:: console

    $ sudo nano /etc/systemd/system/chameleon.service
	    [Unit]
	    Description=Chameleon Vision
        Wants=network-online.target
	    After=network-online.target

	    [Service]
	    Type=simple
	    ExecStart=
	    ExecStart=java -jar /home/pi/chameleon.jar

	    [Install]
	    WantedBy=multi-user.target

Enable the Daemon and its Dependencies

.. code-block:: console

    $ sudo systemctl daemon-reload
    $ sudo systemctl enable systemd-networkd-wait-online.service
    $ sudo systemctl start chameleon.service
    $ sudo systemctl enable chameleon.service
