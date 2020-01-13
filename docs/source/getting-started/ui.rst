User Interface
==============

Opening the UI
----------------

To connect to the Chameleon Vision UI you will need to enter in the web address.
The web address is the ``<coprocessor-IP>:<port>``.
The port defaults to 5800 and the coprocessor's IP address will be in the form 10.TE.AM.XX.
If you are testing on a desktop computer you can use ``localhost`` in place of the IP address.
For example, an IP address of 10.15.77.13 and a port of 5800, the web address will be ``10.15.77.13:5800`.

.. _learn-ui:

Getting Familiar with the UI
------------------------------

The user interface has two main tabs, you can switch between them in the top-right corner:

- **Vision**: Allows teams to configure pipeline settings with a live preview.
- **Settings**: For configuring networking and camera settings.

.. image:: /images/UI/homePage.PNG
   :width: 600

.. image:: /images/UI/generaltab.PNG
   :width: 600

.. _learn-ui-vision:

Vision Tab
^^^^^^^^^^^^

The Vision tab displays the processed image in real-time to help teams tune and adjust the pipeline setup.

.. raw:: html
	
	<video width="640" controls>
		<source src="../_static/video.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>

There are five steps to configuring a vision pipeline:

#. Camera and Pipleine Selection
#. Input
#. Threshold
#. Conoturs
#. Output


Camera and Pipeline Selection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

On the left side there is a dropdown labelled "Camera".
This list contains all :ref:`detected cameras<detected-cameras>`.
The pen icon can be used to rename the camera.

On the right side there is a dropdown labelled "Pipeline".
These pipelines contain different settings and they can be easily switched between.
Any edited configurations will apply only to the selected pipeline.

.. image:: /images/UI/cameraPipelineSelect.png


.. _learn-ui-input:

Input
~~~~~~

The input tab allows the adjustment of camera exposure, brightness, and orientation:

.. image:: /images/UI/lowExposure.PNG
   :width: 600

.. _learn-ui-threshold:

Threshold
~~~~~~~~~~

The thresholding tab allows teams to adjust the Hue/Saturation/Value (HSV) thresholds.
This allows only parts of the images within the thresholds to be detected, such as when configured for vision tape.
Teams can also enable erode and dilate for eliminating speckles.

For a more in depth explanation of erode and dilate visit `opencv's page <https://docs.opencv.org/2.4/doc/tutorials/imgproc/erosion_dilatation/erosion_dilatation.html#morphological-operations>`_


.. image:: /images/UI/hsvPart1.PNG
   :width: 600

.. image:: /images/UI/hsvPart2.PNG
   :width: 600


.. _learn-ui-contours:

Contours
~~~~~~~~~

The contours tab has sliders which constrain the contours which can be considered for sorting. Teams can adjust the minimum or maximum area, aspect ratio (the ratio of width to height of bounding rectangle of the object) or extent (the ratio of contour area to bounding rectangle area). This tab also allows teams to select only one target or to group two together. Another filtering option is Speckle rejection, it ignores small contours "speckles" compared to the largest contour seen.

.. image:: /images/UI/singleGroup.PNG
   :width: 600

.. image:: /images/UI/dualGroup.PNG
   :width: 600


.. _learn-ui-output:

Output
~~~~~~~~

The output tab controls how the contours which make it through thesholding and filtering are sent as the target. Teams can sort contours by leftmost/rightmost/topmost/bottommost, largest, smallest, or closest to the crosshair (centermost).

.. image:: /images/UI/rightmostSort.PNG
   :width: 600

.. image:: /images/UI/smallestSort.PNG
   :width: 600


This tab also allows teams to perform crosshair calibration. Instead of offsetting values in code, teams can line up their robot perfectly by hand, click "calibrate A" and "calibrate B", and the crosshair will be set to the current position. If the robot needs to shoot gamepieces into a goal from different distances, teams can calibrate A at their closest scoring position and B at their furthest scoring location, and the crosshair will linearly interpolate between the two offsets based on distance (area) from the target.


3D 
~~~~~~

The 3D tab is used for :ref:`SolvePNP<solvePNP>`. This is an advanced feature which is not needed for 2D pipelines.

.. _learn-ui-binary-image:

Image / Binary Image
~~~~~~~~~~~~~~~~~~~~~

On the right in the vision tab you will see the camera's image, this is the image published. You can also choose ``Threshold`` to see a binary image of the threshold filtering (HSV erode % dilate). A white represents a pixel that passed the threshold filtering and a black one is a pixel that didn't pass the filtering. You can also see the FPS, pitch and yaw of the target



.. _learn-ui-settings:

Settings tab
^^^^^^^^^^^^

In the settings tab you change can settings in couple of categories

General
~~~~~~~~

Network settings and team number

Cameras
~~~~~~~~

Resolution and fps for each :ref:`detected cameras<detected-cameras>`

.. _camera-adjustments:

Camera Adjustments 
~~~~~~~~~~~~~~~~~~

This tab contains the Driver Mode and 3D settings for each camera.
Driver Mode disables the overlays on the streamed camera output, making it easier for the driver to see.
In this tab you can set the brightness and exposure for each :ref:`detected cameras<detected-cameras>`.

.. note::
   It might take a couple of seconds for the camera to switch its exposure settings so switching driver mode on or off can cause a problem with the vision processing/ the driver's view for a few seconds

You can also calibrate your 3D model as explained :ref:`here<solvePNP>`.

Saving changes
------------------

After configuring and tuning your pipeline settings the changes will be saved automatically, alternatively it can be saved by pressing the ``Save`` button.

.. note::
	On version 1.1.4 or older, the changes are NOT saved automatically at all. They are only saved when the client closes its session (close the browser tab or refresh the page).
