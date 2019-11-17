.. _networktables:

Networktables
================


| Network tables are a way of communication between the RoboRIO and other devices on the robot's network like the driver's PC and the coprocessor that runs Chameleon Vision.

| You can think of Network tables as a shared folder accessable from all network devices.
| Each folder can have another folder(s) and or data(s) inside. Each data field has a `key` and a `value`
| To view the network table you can use a java program from WPI lib called outlineviewer.

.. explanation about what it is, and outlineviewer...

.. image:: /images/outlineviewer.png
   :width: 600

| You can see the base folder `Root` that has `chameleon-vision` and `CameraPublisher` under it.
| Under `chameleon-vision` there is the camera name, in this case `TurretCam` and under it there are the pipeline results.

+------------+------------+------------------------------+
|   key      | value type | purpose                      |
+============+============+==============================+
|    pitch   |   double   | Target's vertical angle      |
+------------+------------+------------------------------+
|     yaw    |   double   | Target's horizontal angle    |
+------------+------------+------------------------------+
|  pipeline  |   double   | Index of pipeline to execute |
+------------+------------+------------------------------+
|  timestamp |   double   | Result timestamp             |
+------------+------------+------------------------------+
| driver_mode|   boolean  | Should enable driver mode    |
+------------+------------+------------------------------+
|  is_valid  |   boolean  | Is result valid              |
+------------+------------+------------------------------+

Changeable values
-------------------
If a device on the network for example the RoboRIO or the driver's PC changes one of these values the program will react to it

- pipeline: the index number of the pipeline that the program should execute. If it changes the program will execute the pipeline that has a index as the number it recived.

- driver_mode: When the driver wants to use the camera for driving he can turn this boolean to `true` and Chamelon Vision will not process the image and wont draw on it. It will also set brightness and exposure to values defined under :ref:`camera ajustments<camera-ajustments>`


Values explained further
-------------------------------
- timestamp: by syncing the RoboRIO and the coprocessor's clock the RIO can see how long ago did the image that led to the pipeline results was taken. This can help overcome the delay that is caused because the processing time. You can read about it :ref:`here<timestamp>`

- is_valid: If the processing had an error i.e no target was found, `is_valid` will be set to `false`.