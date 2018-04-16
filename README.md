# Inception Retraining

Dependencies:

TensorFlow

Python 2.7

Description
===========

This project demonstrates how to retrain Google's Inception V3 model to recognize new objects in a picture. In the signs3 folder are three kinds of photos that are 160 x 120 pixels. Left, right and empty. The goal of the retraining is to create a DNN that can recognize road signs for a Raspberry Pi + BrickPi v3 robot. The idea is to use the picamera to feed images to tensorflow and have the robot navigate using object recognition.

Installation on Windows 10
===========

1. Download Python 64bit for windows. Do not use 32bit! Tensorflow only works on 64bit. If you get an error can't install, double check your python is 64bit.
2. Open a powershell
3. Run pip install tensorflow
4. clone this repository
5. Run "python retrain_inception.py --image_dir=./signs3"

When the retraining is done, you will see a folder named "tmp" with the output results.

Testing the Retrained Model
===========
python tf_robot_test.py --graph=./tmp/output_graph.pb --labels=./tmp/output_labels.txt --input_layer=Placeholder --output_layer=final_result --image=./signs3/test_left01.jpg

General Notes
===========

The training dataset was created by hand with a picamera on my tribot with RP3B+ and BrickPi3. To improve the acuracy, I manually added noise to the background and grayed out sections. Google Inception was trained on ImageNet dataset, which is a collection of tagged photos 100x100 pixels. This means objects that are closer to 100x100 pixels work better than features 30x50. The images in the signs3 folder are 160x120 pixels. TensorFlow prepares the images before feeding it to the NN. If you decide to make your own dataset, keep in mind these tips.

1. try to get as many examples as possible. This is time consuming and there aren't any great tools for generating a bunch of great images for training

2. try to size the object so it is close to 100x100 pixels

3. have a variety of lighting and backgrounds

4. if your object is a natural thing like a flower, try to crop the photo to have just the flower

5. if your dataset is larger than 10,000 images use a NVidia GPU. I compared training with CPU and GPU. GPU training with 1070 is 20x faster than using a Core i7 6700 4.3Ghz with 64G of DDR4 RAM