.. _networktables:

NetworkTables
===============

NetworkTables is a communication protocol used between the roboRIO and other devices on the network.
For more information, see the `frc-docs article <https://frc-docs.readthedocs.io/en/latest/docs/software/networktables/networktables-intro.html>`_.

NetworkTables acts like shared folder which is accessable by all connected devices.
Every folder can have sub-folders which can also have files.
These are called "tables", "subtables", and "entries".
Each entry has both a name, type, and a value.

A program called OutlineViewer can be used to view the NetworkTable entries and is included with your WPILib install.

.. image:: /images/outlineviewer.png
   :width: 600

Chameleon Vision stores its entries in a table called `chameleon-vision`.
Each camera will be in a subtable with it's name, say, `TurretCam`.
The TurretCam table will contain the pipeline information, detailed below.

- pitch (double)
    The vertical angle to the target in degrees.

- yaw (double)
    The horizontal angle to the target in degrees.

- pipeline (editable double)
    The index of the current pipeline Chameleon Vision should run.
    Change this to switch between pipelines.

- timestamp (double)
    The time the result was taken.
    For more details, see :ref:`here<timestamp>`.

- driver_mode (editable boolean)
    Setting this to true enables the :ref:`Driver Mode<camera-adjustments>`.

- is_valid (boolean)
    Whether or not a a target was found.
