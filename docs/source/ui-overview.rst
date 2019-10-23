User Interface
==============

The user interface has two main tabs: Vision and Settings. The Vision tab allows users to tune their pipeline settings, and the settings tab configures networking and camera resolution:

.. image:: images/homePage.png

.. image:: images/generaltab.png

Configuring vision settings
---------------------------

.. image:: images/video.gif

When configuring the vision pipeline, there are four main steps (one per tab): input, thresholding, contour sorting and output.

The input tab adjust camera exposure settings and camera orientation:

.. image:: images/lowExposure.png

The thresholding tab allows users to adjust the Hue/Saturation/Value settings to only allow in parts of the image that are the same color as the vision tape, as well as allows users to erode or dilate the contours to eliminate small speckles:

.. image:: images/hsvPart1.png

.. image:: images/hsvPart2.png

The contours tab has sliders which constrain the contours which can be considered for sorting. Users can adjust the minimum or maximum area, aspect ratio (the ratio of width to height of bounding rect of the object) or extent (the ratio of contour area to bounding rectangle area). This tab also allows users to select only one target or to group two together.

.. image:: images/singleGroup.png

.. image:: images/dualGroup.png

The output tab controls how the contours which make it through thesholding and filtering are sent as the target. Users can sort contours by leftmost/rightmost/topmost/bottommost, larget, smallest, or closest to the crosshair.

.. image:: images/rightmostSort.png

.. image:: images/smallestSort.png