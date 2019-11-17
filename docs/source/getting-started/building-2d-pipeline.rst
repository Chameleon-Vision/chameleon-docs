Building a 2D pipeline
======================

| After reading :ref:`getting familiar with the UI<learn-ui>` you can create your pipeline
| We will go over all (except 3D) the :ref:`vision tabs<learn-ui-vision>` one by one

Step 0: :ref:`Settings<learn-ui-settings>`
-------------------------------------------

| Before we start on the pipeline, make sure that your team number is set, the network settings are good(For competition you want a static IP like 10.XX.XX.YY where XXXX is your team number and YY is the a last number in the IP address, check the FRC manual for YY options as it may change from year to year. Generally it can be 13-20).

| Also set the resolution to a low-very low and the FPS to the highest you can. High resolution isn't needed for FRC vision and speed is more important.

| You can also set the driver exposure and brightness settings. 

Step 1: :ref:`Input<learn-ui-input>`
--------------------------------------

If you put a green L.E.D ring around the camera, any retro reflector targets will appear very bright and saturated, sometimes even completely out of the camera's scope of brightness and it will just appear as white. Also there are many disturbances in the field like scoreboards, flashes, screens, light sources and so much more that you cant account for. By lowering the exposure of the camera the sensor will receive less light from the disturbances so they will be easier to ignore and the vision target will be in the camera's scope of brightness so it will be much easier to filter out the rest of the image.

.. note::
	Some USB cameras / USB cameras' drivers cannot change exposure

| TL;DR
| Its a good idea to keep your brightness and exposure low


Step 2: :ref:`Threshold<learn-ui-threshold>`
-----------------------------------------------

| In this step you need to adjust the HSV filtering values.
| Wait, What is HSV?

| HSV or Hue Saturation Value is a way to select a range of colors. We want to create a filter that allows only specific pixels with a "green-ish" color value to pass to the next step.
| You can select :ref:`threshold image<learn-ui-binary-image>` to see a binary image of what pixels passed this filter. Adjust the filtering slider accordingly. Keep in mind that you probably want to see the vision target from different angles and different distances.

| If the vision target seems too bright or white you will have problems because white doesn't fit any color range. Go back to step 1 to make the image darker.

A good general rule is to keep the filter a bit more "Wide" than you need. Because the field isn't lit the same in every event or maybe even different on the same field, its a good idea to add a bit of spare in each slider. In this step most of the background will be filtered, If you see a lot of it passing this step make the sliders more "narrow"

Step 3: :ref:`Contours<learn-ui-contours>` 
-----------------------------------------------

| Once we filter out most of the background we can treat the filtered pixels as shapes - contours.
| We could find the area of each contour, the ratio between it's width and height and filter contours who don't fall between the slider's values.
| We can also find the bounding rectangle of the shape, which is the ratio between the contour's area and the bounding rectangle area. In 2016 the vision targets had a ``U`` shape so the ratio between their area to their bounder rectangle was smaller than the vision target in 2017 that were rectangle shape.
| The bounding rectangle will be drawn on the image
| Many FRC vision target are pairs of targets. Sometimes they are angled like in 2019, both vision target were on angle so their intersection point is above them.

Step 4: :ref:`Output<learn-ui-output>`
------------------------------------------

| Depending on your camera's placement you might want the final contour/contours to be the topmost / buttommost / leftmost / rightmost / centermost
| You can also calibrate two points to account of the camera offset if its not centered. see the :ref:`output tab<learn-ui-output>` for an explanation.

Step 5: Reading results
------------------------

| Now that we have built the pipeline, we want to receive the results in the RoboRIO.
| This information is sent via :ref:`Networktables<networktables>`. See :ref:`Robot example code<robot-code>` to see how you can read it.