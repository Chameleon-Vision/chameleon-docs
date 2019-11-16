User Interface
==============

Opening the UI
------------------

In order to connect to the UI you will need to enter in a web browser the Chameleon Vision's computer IP followed by ``:``  and the :ref:`webserver port<webserver-port>`

For example if the coprocessor's ip is 10.15.77.13 and the port is 5888 then enter in the browser ``10.15.77.13:5888``

The user interface has two main tabs: Vision and Settings. The Vision tab allows teams to tune their pipeline settings, and the settings tab configures networking and camera resolution:

.. image:: /images/UI/homePage.PNG
   :width: 600

.. image:: /images/UI/generaltab.PNG
   :width: 600

Configuring vision settings
---------------------------

.. image:: /images/UI/video.gif

When configuring the vision pipeline, there are four main steps (one per tab): input, thresholding, contour sorting and output.

The input tab adjust camera exposure settings and camera orientation:

.. image:: /images/UI/lowExposure.PNG
   :width: 600

The thresholding tab allows teams to adjust the Hue/Saturation/Value settings to only allow in parts of the image that are the same color as the vision tape, as well as allows teams to erode or dilate the contours to eliminate small speckles:

.. image:: /images/UI/hsvPart1.PNG
   :width: 600

.. image:: /images/UI/hsvPart2.PNG
   :width: 600

The contours tab has sliders which constrain the contours which can be considered for sorting. teams can adjust the minimum or maximum area, aspect ratio (the ratio of width to height of bounding rect of the object) or extent (the ratio of contour area to bounding rectangle area). This tab also allows teams to select only one target or to group two together.

.. image:: /images/UI/singleGroup.PNG
   :width: 600

.. image:: /images/UI/dualGroup.PNG
   :width: 600

The output tab controls how the contours which make it through thesholding and filtering are sent as the target. teams can sort contours by leftmost/rightmost/topmost/bottommost, larget, smallest, or closest to the crosshair.

.. image:: /images/UI/rightmostSort.PNG
   :width: 600

.. image:: /images/UI/smallestSort.PNG
   :width: 600

This tab also allows teams to perform crosshair calibration. Instead of ofsetting values in code, teams can line up their robot perfectly by hand, click "calibrate A" and "calibrate B", and the crosshair will be set to the current position. If the robot needs to shoot gamepieces into a goal from different distances, teams can calibrate A at their closest scoring position and B at their furthest scoring location, and the crosshair will linearly interpolate between the two offsets based on distance (area) from the target.