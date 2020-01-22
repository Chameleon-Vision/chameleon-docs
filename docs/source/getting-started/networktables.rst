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

- targetPitch (double)
    The vertical angle to the target in degrees.

- targetYaw (double)
    The horizontal angle to the target in degrees.

- targetArea (double)
	The precentage of the target contour from the entire image
	
- targetPose (double array)
	The 3D target position as an array values are ordered by [x (meters),y (meters),angle (degrees)]
	
- targetFittedWidth (double) & targetFittedHeight (double)
	The width and height of the blue rectangle in pixels

- targetBoundingWidth (double) & targetBoundingHeight (double)
	The width and height of the red rectangle in pixels
	
- targetRotation (double)
	The angle of the blue rectangle in degrees

- pipeline (editable double)
    The index of the current pipeline Chameleon Vision should run.
    Change this to switch between pipelines.

- latency (double)
    The time delta that it took for the vision process to compute the image

- driverMode (editable boolean)
    Setting this to true enables the :ref:`Driver Mode<camera-adjustments>`.

- isValid (boolean)
    Whether or not a a target was found.

- auxTargets (array)
	A json array of the 5 best targets each of the targets has its own array.
	The array values are ordered as [pitch, yaw, area, bounding width, bounding height, fitted width, fitted height, target angle, target pose] and are the same type like the selected target 