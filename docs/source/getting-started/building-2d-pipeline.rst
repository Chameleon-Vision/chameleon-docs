Building a 2D Pipeline
========================

After :ref:`getting familiar with the UI<learn-ui>` you can create your pipeline.
We will go over all (except 3D) the :ref:`vision tabs<learn-ui-vision>` one by one

Step 0: :ref:`Settings<learn-ui-settings>`
-------------------------------------------

Before we start, make sure you have configured the settings correctly.
Ensure that your:

* team number is set correctly
* coprocessor has a static IP address (such as 10.TE.AM.13)

It is also best to have the maximum FPS.
This can generally be achieved by decreasing the resolution of the camera.

Step 1: :ref:`Input<learn-ui-input>`
--------------------------------------

Adding a green LED ring around the camera ensures that retro-reflector targets are bright and saturated, which makes them easier to see.
Lowering the camera's exposure and brightness will darken the rest of the field and make it much easier for the bright vision targets to be filtered.

.. note::
	Not all USB Cameras support exposure settings.


Step 2: :ref:`Threshold<learn-ui-threshold>`
-----------------------------------------------

In this step you will adjust the HSV threshold values.

Hue-Saturation-Value (HSV) is a way of digitally represented colours, similar to Red-Green-Blue (RGB).
However, HSV encodes the colour in terms of its hue, making it easier to filter out a certain colour.

We want to create a filter to select only pixels that are "greenish".

#. Select the :ref:`threshold image<learn-ui-binary-image>` to see the filter output. 
   This makes it easier to see what we're doing.
#. Adjust the slider until just the tape is visible.
   If the rest of the vision target is too bright, try decreasing the camera exposure.
#. Widen the colour filters to give leeway as the lighting between fields differs.


Step 3: :ref:`Contours<learn-ui-contours>` 
-----------------------------------------------

Once the background has be filtered out we can treat the remaining white pixels as "contours".
Each contour has:

* area
* ratio between width and height
* height
* width

It is possible to filter out contours which do not meet the specifying criteria of the above properties.
In 2016 the vision targets were a U shape, which had a different W/H ratio compared to the 2017 targets, which were rectangular.

Sometimes the vision targets can be pairs, such as in 2019, where both targets were on an angle.
Chameleon Vision allows two contours to be merged into one contour.

The bounding rectangle of the contour will be drawn on the output.

Step 4: :ref:`Output<learn-ui-output>`
------------------------------------------

Depending on your camera's placement you might want the final contour/contours to be the topmost / buttommost / leftmost / rightmost / centermost

Now that we have built the pipeline, we want to receive the results in the RoboRIO.
This information is sent via :ref:`NetworkTables<networktables>`.
See the :ref:`example robot code<robot-code>` for an example of how to use it.