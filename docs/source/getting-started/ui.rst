User Interface
==============

Opening the UI
------------------

In order to connect to the UI you will need to enter in a web browser the Chameleon Vision's computer IP followed by ``:``  and the :ref:`webserver port<webserver-port>`

For example if the coprocessor's ip is 10.15.77.13 and the port is 5888 then enter in the browser ``10.15.77.13:5888``

.. _learn-ui:

Getting familiar with the UI
-----------------------------

The user interface has two main tabs:

- The Vision tab: allows teams to tune their pipeline values, it updates in real-time.
- The Settings tab: configures networking and camera settings that dont change often like the camera's resolution

.. image:: /images/UI/homePage.PNG
   :width: 600

.. image:: /images/UI/generaltab.PNG
   :width: 600

.. _learn-ui-vision:

Vision tab
^^^^^^^^^^^^

The vision tab updates the processed image in real-time to help you tune and ajust the vision values


.. image:: /images/UI/video.gif

When configuring the vision pipeline, there are four main steps (one per tab): input, thresholding, contour sorting and output.



Camera and pipeline selection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

| Choose one camera from the drop-down menu.
| The list contains :ref:`detected cameras<detected-cameras>`.

| Every camera has at least one pipeline but you can add more 
| You might want to rename the camera and the pipeline(s) so it will be clearer which camera is which and the pipeline's purpose
| When you change and ajust values in the following steps you will change the settings of the pipeline currently selected

.. image:: /images/UI/cameraPipelineSelect.PNG


.. _learn-ui-input:

Input
~~~~~~

The input tab adjust camera exposure settings and camera orientation:

.. image:: /images/UI/lowExposure.PNG
   :width: 600

.. _learn-ui-threshold:

Threshold
~~~~~~~~~~

The thresholding tab allows teams to adjust the Hue/Saturation/Value settings to only allow in parts of the image that are the same color as the vision tape, as well as allows teams to erode or dilate the contours to eliminate small speckles

For a more indepth explaination of erode and dilate visit `opencv's page <https://docs.opencv.org/2.4/doc/tutorials/imgproc/erosion_dilatation/erosion_dilatation.html#morphological-operations>`_


.. image:: /images/UI/hsvPart1.PNG
   :width: 600

.. image:: /images/UI/hsvPart2.PNG
   :width: 600


.. _learn-ui-contours:

Contours
~~~~~~~~~

The contours tab has sliders which constrain the contours which can be considered for sorting. Teams can adjust the minimum or maximum area, aspect ratio (the ratio of width to height of bounding rect of the object) or extent (the ratio of contour area to bounding rectangle area). This tab also allows teams to select only one target or to group two together. Another filtering option is Speckle rejection, it ignores small contours "speckles" compared to the lagest contour seen

.. image:: /images/UI/singleGroup.PNG
   :width: 600

.. image:: /images/UI/dualGroup.PNG
   :width: 600


.. _learn-ui-output:

Output
~~~~~~~~

The output tab controls how the contours which make it through thesholding and filtering are sent as the target. teams can sort contours by leftmost/rightmost/topmost/bottommost, larget, smallest, or closest to the crosshair(Centermost).

.. image:: /images/UI/rightmostSort.PNG
   :width: 600

.. image:: /images/UI/smallestSort.PNG
   :width: 600


This tab also allows teams to perform crosshair calibration. Instead of ofsetting values in code, teams can line up their robot perfectly by hand, click "calibrate A" and "calibrate B", and the crosshair will be set to the current position. If the robot needs to shoot gamepieces into a goal from different distances, teams can calibrate A at their closest scoring position and B at their furthest scoring location, and the crosshair will linearly interpolate between the two offsets based on distance (area) from the target.

.. _learn-ui-binary-image:

Image / Binary Image
~~~~~~~~~~~~~~~~~~~~~

On the right in the vision tab you will see the camera's image, this is the image published. You can also choose ``Threshold`` to see a binay image of the threshold filtering (HSV erode % dilate). A white represents a pixel that passed the threshold filtering and a black one is a pixel that didn't pass the filtering. You can also see the FPS, pitch and yaw of the target

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

Driver mode
~~~~~~~~~~~~~

Driver mode is a option that the vision processing wont run and wont disturb the driver so he could use the camera. In this tab you can set the brightness and exposure for each :ref:`detected cameras<detected-cameras>`.

.. note::
   It might take a couple of seconds for the camera to switch it's exposure settings so switching driver mode on or off can cause a problem with the vision processing/ the driver's view for a few seconds

Saving changes
------------------

After configuring and tuning your pipeline settings the changes will be saved automatically, alternatively it can be saved by pressing the ``Save`` button.

.. note::
	On version 1.1.4 or older, the changes are NOT saved automatically at all. They are only saved when the client closes it's session (close the browser tab or refresh the page).
