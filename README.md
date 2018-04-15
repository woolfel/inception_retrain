# Inception Retraining

Dependencies:
TensorFlow
Python 2.7

Description
===========

This project demonstrates how to retrain Google's Inception V3 model to recognize new objects in a picture. In the signs3 folder are three kinds of photos that are 160 x 120 pixels. Left, right and empty. The goal of the retraining is to create a DNN that can recognize road signs for a Raspberry Pi + BrickPi v3 robot. The idea is to use the picamera to feed images to tensorflow and have the robot navigate using object recognition.

Installation on Windows 10
===========

1. Download Python 64big for windows. Do not use 32bit, since Tensorflow only works on 64bit. If you get an error cann't install, double check your python is 64bit.
2. clone this repository
3. Run "python retrain_inception.py --image_dir=./signs3"

When the retraining is done, you will see a folder named "tmp" with the output results.

