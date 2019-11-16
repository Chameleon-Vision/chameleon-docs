Features
==========

Camera Features
------------------

Chameleon Vision support almost any :ref:`USB camera<supported-cameras>`

.. note::
	
	The Pi Cam and web cameras are NOT supported currently


Control USB cameras
^^^^^^^^^^^^^^^^^^^^

Chameleon Vision can set resolution, fps, brightness and exposure for each USB camera that it has :ref:`detected<detected-cameras>`

It also publishes the camera view, which is divisable to save bandwith. Also it can flip the image by 180 degrees if the camera is mounted upside-down


Driver mode settings
^^^^^^^^^^^^^^^^^^^^^^

The vision cameras can be used by the robot's driver to see better
When driver mode is enabled the brightness and exposure is reverted and no vision marks are drawn on the image


Vision Features
-----------------

Filtering
^^^^^^^^^^^^^^^^

Filter out your target from the background with HSV filtering, area, width height ratio and so much more

.. note::

	It's recommended to install a green L.E.D strip around the camera

Multiple Target with intersection point can filter out even more

Camera offset calibration
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sometimes its not possible and inconvinet to place the camera in the center of the robot,
With a very short calibration Chameleon vision can account for that offset

