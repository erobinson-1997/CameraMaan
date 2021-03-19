# CameraMaan
CameraMaan is a camera operated by a servo controlled arm. CameraMaan uses a multi-threaded solution to control the servos and track moving objects.

![alt text](https://i.imgur.com/XSCKQHv.jpeg)

# Files

### start_up/ 
This contains a startup script that tests the servos after turning the device on. 

### CameraMaan/
This contains a directory called CameraMaan_app, which only contains the Makefile and the executable. 

The entry point for the code is in CameraMaan.cpp

There is also a pair of files for controlling the servos:
dxl_controller.cpp    dxl_controller.h

