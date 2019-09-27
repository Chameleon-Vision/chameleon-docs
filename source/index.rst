Chameleon-Vision
================

Chameleon Vision is free open-source software for FRC teams to use for
vision proccesing on their robots.

Getting started
---------------

See Deployment for notes on how to deploy the project on a live system.

| These instructions will get you a copy of the project up and running
  on your local machine for development and testing purposes.
| (Coming soon!)

### Prerequisites
-----------------

For the co-processor
^^^^^^^^^^^^^^^^^^^^

-  Java 12 Runtime (See Deployment - Software)
-  Avahi Daemon

For the driver station
^^^^^^^^^^^^^^^^^^^^^^

-  Bonjour

Deployment
----------

| Deploying is as simple as uploading the chameleon-vision-1.xx.jar file
  to your target device.
| Run the program with ``java -jar chameleon-vision-1.xx.jar``

Software
--------

Java 12
~~~~~~~

Follow the correct instructions for your platform from `BellSoft`_

Avahi Daemon (Linux systems)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

``sudo apt-get install avahi-daemon avahi-discover avahi-utils libnss-mdns mdns-scan``

Bonjour (Windows Systems)
~~~~~~~~~~~~~~~~~~~~~~~~~

Download and install Bonjour `from here`_

Hardware
--------

ARM Co-processors
~~~~~~~~~~~~~~~~~

| Currently only Raspberry Pi 3 or 4 models with at least 1GB of RAM are
  tested and supported.
| Additional ARM-based single board computers (Odroid, Nvidia Jetson,
  etc.) will be supported in the near future.

x86 Computers
~~~~~~~~~~~~~

| Currently any 64-Bit devices (Windows, Linux and Mac OS) are
  supported.
| 32 Bit devices are not supported.

Authors
-------

-  **Sagi Frimer** - *initial work* - websocket, settings manager, UI

-  **Ori Agranat** - *main coder* - vision loop, UI, websocket,
   networktables

-  **Omer Zipory** - *developer* - vision loop, websocket, networking

-  **Banks Troutman** - *developer* - vision loop, websocket, networking

-  **Matt Morley** - *developer* - documentation

Acknowledgments
---------------

-  `WPILib`_ - Specifically `cscore`_, `CameraServer`_, `NTCore`_, and
   `OpenCV`_.

-  `Apache Commons`_ - Specifically `Commons Math`_, and `Commons Lang`_

-  `Javalin`_

-  `Spring Framework`_

-  `JSON`_

-  `Google`_ - Specifically `Gson`_

License
-------

Usage of Chameleon Vision must fall under all terms of `Creative Commons
Attribution-NonCommercial-ShareAlike 4.0 International`_

.. _BellSoft: https://bell-sw.com/pages/liberica_install_guide-12.0.2/
.. _from here: https://support.apple.com/kb/DL999?locale=en_US
.. _WPILib: https://github.com/wpilibsuite
.. _cscore: https://github.com/wpilibsuite/allwpilib/tree/master/cscore
.. _CameraServer: https://github.com/wpilibsuite/allwpilib/tree/master/cameraserver
.. _NTCore: https://github.com/wpilibsuite/allwpilib/tree/master/ntcore
.. _OpenCV: https://github.com/wpilibsuite/thirdparty-opencv
.. _Apache Commons: https://commons.apache.org/
.. _Commons Math: https://commons.apache.org/proper/commons-math/
.. _Commons Lang: https://commons.apache.org/proper/commons-lang/
.. _Javalin: https://javalin.io/
.. _Spring Framework: https://spring.io/
.. _JSON: https://json.org
.. _Google: https://github.com/google
.. _Gson: https://github.com/google/gson
.. _Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International: https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode

.. toctree::
   :maxdepth: 1
   :caption: Contents

..    docs/test


.. Indices and tables
.. ==================

.. * :ref:`genindex`
.. * :ref:`modindex`
.. * :ref:`search`
