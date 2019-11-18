Command line Information
==============================

| When you run the program, a lot of information will be displayed in the command line
| This information is mainly for debugging and is not needed most of the time

.. note::
	| Some output prints is not controlled by Chameleon vision directly and is printed by external libraries.
	| Please ignore these lines, and pay attention to the output that's explained here


..  _webserver-port:

Webserver port
------------------

| When the program initializes it will print the webserver in a similar form ``Starting Webserver at port XXXX`` where XXXX is the port (Default 5800)
| this port is needed when connecting to the UI.



Platform
----------

| The first output line onstart is the platfrom, example, ``Starting Chameleon Vision on platform Windows x64``

| If you get this message ``Unknown Platform. OS: ...`` or an incorrect platfrom, please contact a developer in our discord server


..  _detected-cameras:

Camera initialization
-------------------------

| For each camera ``CS: YOUR_CAMERA_NAME: Connecting to USB camera on YOUR_CAMERA_PATH`` will be printed and also the time it took to initialize it (it should be less than a second)

| If your camera hasn't appeared in this print there is probably a problem somewhere with it, please contact a developer in the discord server

Network management
------------------

| On linux devices the program can change the network adapter settings to settings that enable the coprocessor to work on the robot
| On windows this feature isn't supported so it might warn the user about it


Networktable State
------------------------
The program will print if it connected or couldn't connect to the networktable specified in the :ref:`arguments<command-line-arguments>`