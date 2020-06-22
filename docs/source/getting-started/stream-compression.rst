.. _steam:

Stream and Compression
=======================


| You can view the camera's video stream on your Driver Station's dashboard software.
| There are few things to keep in mind when using the video stream.

* While running a pipeline, some visual items might be drawn on the image (ie contours' bounding rect)
* Different pipelines can have different resolutions, make sure the image doenst "move" or change size when switching pipelines
* When chaning pipelines it might take up to a few seconds for the camera to change resolution, exposure and brightness settings. Expect around one second of downtime
* At all times during a match the communication bandwidth limit is 4 Mb/s. Make sure you DON'T exceed this value and keep a safe buffer under it

Opening the Stream
---------------------

In order to get the link to the stream for your dashboard software right-click on the stream in the UI and click ``Copy image address``

.. image:: /images/UI/copyStreamAddr.png
   :width: 600

The copied URL should be ``http://PROCESSORSIPADDR:1181/stream.mjpg``. You can put his URL in a MJPG stream in your dashboard software

Bandwidth Reduction
--------------------

| Managing the bandwidth usage of the stream is a balance between stream quality and bandwidth.
| Chameleon vision supports 3 video settings to lower the stream's bitrate

1. :ref:`FPS Limiting<learn-ui-stream>`
2. :ref:`Stream Resolution<learn-ui-stream>`
3. :ref:`MJPEG Compression<compression>`

.. _compression:

MJPEG Compression
~~~~~~~~~~~~~~~~~~~
| The ``CameraServer`` allows the user to specify a compression value between 0 (VERY high compression) and 100 (uncompressed)
| The higher the compression the lower the bitrate of the stream but the stream quailty goes down as well.

.. image:: /images/UI/streamCompression.gif
	:width: 700

| You can see the bitrate readout changing when selecting different compression values
| To select the compression amount use by sending a URL parameter ``compression`` -i.e.
| Uncompressed ``http://PROCESSORSIPADDR:1181/stream.mjpg?compression=100`` 
| Max compression ``http://PROCESSORSIPADDR:1181/stream.mjpg?compression=0``
