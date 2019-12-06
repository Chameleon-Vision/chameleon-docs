..  _coprocessor-setup:

Coprocessor Setup
==================
For a non Raspberry Pi installation, please follow :ref:`Testing PC<pc-install>` instructions but do not use the ``--unmanage-network``  :ref:`argument<command-line-arguments>`

Raspberry Pi
------------

Software Install
^^^^^^^^^^^^^^^^
Follow the instructions `here <https://www.raspberrypi.org/documentation/installation/installing-images/>`_ on getting Raspbian on your SD card.
You may install the Desktop version, but for optimal performance we recommend Raspbian Buster Lite.

Ensure your Raspberry Pi is connected to a network with internet access via the Ethernet connection.

Log in to the Raspberry Pi (default username is ``pi``, and default password is ``raspberry``), and in the terminal, run these commands:

.. code-block:: bash

    wget https://git.io/JeDUk -O install.sh
    chmod +x install.sh
    sudo ./install.sh

Once the script has finished running, be sure to reboot.

.. code-block:: bash

    sudo reboot now

Congratulations! Your Raspberry Pi is now set up to run Chameleon Vision!

Once your Raspberry Pi has booted up again, you can run Chameleon Vision with this command in the terminal:

.. code-block:: bash

    sudo java -jar chameleon-vision.jar

And to get the latest version of Chameleon Vision...

.. code-block:: bash

    wget https://git.io/JeDUL -O update.sh
    chmod +x update.sh
    sudo ./update.sh

More information on getting Chameleon Vision to start automatically on boot-up is coming soon.
