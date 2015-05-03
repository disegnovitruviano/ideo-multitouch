# Introduction #

This software interprets data from a webcam used in conjunction with an ftir screen to generate multitouch events for the IDEO Flash multitouch API it also compensates for camera alignment, rotation and fisheye

# Installation #
  * download and install [processing](http://www.processing.org)
  * download and unzip [MultitouchServerFTIR](http://ideo-multitouch.googlecode.com/files/MultitouchServerFTIR.zip) to your processing sketches folder
  * download and install [JMyron](http://webcamxtra.sourceforge.net/download.shtml)
  * if you're running on an Intel mac, download and install this [libJMyron.jnilib](http://www.jibberia.com/projects/) compiled for intel Macs
  * download and install [blobDetection](http://www.v3ga.net/processing/BlobDetection/index-page-download.html)
  * run the FTIR server in processing's "present mode"
  * perform a calibration (press 'c' to calibrate)
  * run the FTIR server (present mode not required)
  * minimize the FTIR server application and run Flash applications.

# Processing Pipeline #
  1. get web cam image
  1. perform background subtraction
  1. perform blob tracking
  1. map blob positions into calibrated space
  1. send touchEvents over socket

# Keyboard commands #
  * press 'c' to calibrate then touch each of the points as they pop up
  * press 'd' to cycle through levels of graphical information

# File architecture #
  * PerpsectiveCorrection handles calibration
  * [fastblur](http://incubator.quasimondo.com) does a fast (approximate) blur on the image
  * all other java files are matrix libraries used for calibration calculation.