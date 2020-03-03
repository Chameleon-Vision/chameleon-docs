.. _solvePNP:

SolvePNP
==========

Chameleon Vision includes everything you need to get started with 3D pose reconstruction with the 2020 Infinite Recharge upper vision targets. 


.. image:: /images/solvepnp/box.png
   :alt: Example view of solvePNP with a 2020 FRC vision target.

Before the 3D features are enabled, the camera must be calibrated. Do this from the Cameras tab, as illustrated `in this informational video <https://www.youtube.com/watch?v=gCnwO6idKq4>`_, using the provided chessboard image printed using your printer's "fit to page" mode and a pair of calipers or a ruler.
This must be done per resolution that solvePNP is to be used with. 

The reason we need to first callibrate the camera is because cameras distorts images to a certain degree. The types of distortion are:

- Radical distortion

   - Radical distortion results in straight lines to appear bent or curved and is the most common type.

- Tangential distortion

   - Tangential distortion results in objects appearing farther away or closer than they are in real life. This is due to the lens of the camera not being aligned with the plane of the image.

By finding how much radical or tangential distortion there is, we can then undistort any image from the camera.
In order to measure the amount of distortion, we can take pictures of an image with a known shape and see how much the camera distorts that image.
We can then use that information to correct the distortion errors.

For example, below you can see a chessboard that is undistorted. To the right, you can see a radical and tangential distortions
of the same chessboard taken from a pinhole camera. 

.. image:: /images/solvepnp/distortion.PNG
   :alt: Calibration using the provided chessboard image.


Before callibrating:

- Make sure the chessboard is 8 x 8 with the length and width of EACH sqaure is the same and correctly inputted into Chameleon
- Collect images from different areas, tilts and distances, tilts of +/- 45 degrees is recommended, however, rotating too much may result in inaccurate data 
- Lighting: make sure no shadows are being cast onto the chessboard, and the chessboard is recieving even lighting
- Make sure you see rainbow stripes from the corners of the chessboard before you take a snapshot.

.. image:: /images/solvepnp/Thumb.PNG
   :alt: Calibration using the provided chessboard image.


After you complete the callibration process, on the command line, you'll see:

- Camera Matrix

   - The camera matrix is a 3 by 3 matrix as show below
   - .. image:: /images/solvepnp/camera_matrix.PNG
   - **fx** and **fy** : These are the focal lengths of the camera expressed in pixels
   - **cx** and **cy** : These are the principal points and refer to the image center 
   - The camera matrix will be scaled proportionally to any change in resolution. For example, if resolution goes from 640 x 480 to 320 x 240 images
   
      - **fx** and **cx**: These will be multiplied by (new resolution x / old resolution x) or in the example, (320 / 640)
      - **fy** and **cy**: These will be multiplied by (new resolution y / old resolution y) or in the example, (240 / 480)

- Distortion Coefficents

   - distortion coefficents are vectors of up to 8 parameters, formated like : **k1, k2, p1, p2 [, k3 [, k4, k5, k6]]**
   - **k1, k2..** are radical distortion coefficents
   - **p1, p2...** are tangential distortion coefficents
   - The distortion do not change based off the camera resolution, so the distortion coefficents will be the same for 640 x 480 images and 320 x 240 images

Now that we have the camera matrix and distortion coefficents, the final parameter we need is the real world coordinates.
These coordinates are derived by using the corners of your target in 3D space, following the format:

   - -targetwidth/2, targetheight/2, 0
   - -targetwidth/2, -targetheight/2, 0
   - targetwidth/2, -targetheight/2, 0
   - targetwidth/2, targetheight/2, 0

These world coordinates for the 2020 season are premade for the Loading Bay and Upper port in the dropdown menu or can
be uploaded as a .csv file.

Now that we have callibrated the camera, and found the 3D world coordinates, we can now use this information to:

- Undistort an image received from the camera
- Using the 3D world coordinates and 2D target coordinates from the image, the SolvePNP() function returns the camera pose using the camera matrix and distortion coefficents
- Returns a re-projection .. error

OpenCV calculates reprojection error by projecting three-dimensional of chessboard points into the image using the final set of calibration parameters and comparing the position of the corners. An RMS error of 300 means that, on average, each of these projected points is 300 px away from its actual position.
The closer the error is to 0, the better the callibration. 

Before enabling 3D tracking, calculate the pitch between the horizontal axis and the optical axis of your camera and enter
it into the **Camera Pitch** field in the chameleon UI.

.. image:: /images/solvepnp/pitch.PNG


In the NT table, after enabling 3D tracking, you will see a **targetPose** double array. These are:

- pose[0]: X distance, which is the distance between the target and the camera in the direction of the optical axis (meters)
- pose[1]: Y distance, which is the distance from the target, perpendicular to the optical axis (meters)
- pose[2]: The angle between the target plane and the optical axis (degrees)

.. image:: /images/solvepnp/targetPose.PNG
   :alt: Source: Ligerbots vision


Now point your camera at a 2020 FRC vision target, enabled 3D from the 3D tab, and get started tracking!
It really is Just That Easy.
