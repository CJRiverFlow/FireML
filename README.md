# Forest Fire detection with Machine Learning on Edge Devices.
### Wildfire detection using Tensorflow and OpenVINO on a Raspberry Pi.

Wildfires are unplanned and unwanted fires, including lightning-caused fires, unauthorized human-caused fires, and escaped prescribed fire projects.

<p align="center">
<img src="images/firefighters.jpg"  width="700" height="400">
</p>

Only from my country (Honduras) I can share the following statistics:
* Wildfires devastate a total of 22,132 hectares of forests in 2019
* By February 10th 2020, 17 fires have been reported in the country.

In one of the most recent catastrophies, the Forest Fires in **Australia** have destroyed more than 11 million hectares, killing millions of animals and at least 33 people died. 

<p align="center">
<img src="images/australian-fires.jpg"  width="700" height="400">
</p>

That's is why a reliable method to detect fires in less time is unvaluable to prevent its consecuences protecting the nature and people lives around it.


## Hardware
The main module of this prototype is build as follows: 

<p align="center">
<img src="images/rpi_hardware.jpg" width="50%" height="50%">
</p>

* Raspberry Pi 3b+
* Raspberry Pi Camera
* Pan-tilt Hat, camera holder and servo module.
* Neural Computer Stick (NCS 1 to boost inference)

Future tests:
* Drone
* Raspberry GSM module

Model was training in Coogle Colab with GPU Instance.


## Getting the data and format convertion.
I will be using a dataset of images with the labels in XML format from the FireNET project. As we will be using Tensorflow Detection API for this project we need to convert this data from .xml to TFRecord.

For this step I have prepare a Google Colab notebook with all the steps needed for this task. 

https://colab.research.google.com/drive/1Pa_gYtkOQ60drFRZoOIdHLahfEfOMTyw

## Using Tensorflow Object Detection API for Model Training.
Once we got the train.record and the test.record files we proceed with the enviroment preparation and the training of the Object Detection model, this process is clearly described in the following Google Colab Notebook:

https://colab.research.google.com/drive/1j5uQtf74f4ZWEinip5DavlWWtaqBbxGe

It is required also to upload the object-detection.pbtxt that you can find in this repository.

## Converting the Tensorflow API model with OpenVino.
Following the steps described in the official Openvino documentation is possible to convert and run in the raspberry pi with a better perfomance:

https://docs.openvinotoolkit.org/latest/_docs_MO_DG_prepare_model_convert_model_tf_specific_Convert_Object_Detection_API_Models.html 

I'm actually working on building a docker container to provide the trained model easy to use. I hope to be able to have this available soon.

## Testing the model

Testing on the Pi camera I have used the video input to test the model so I could get very good results, these are the first test on flame images:

<p align="center">
<img src="images/test1.png"  width="700" height="400">
</p>

<p align="center">
<img src="images/test2.png"  width="700" height="400">
</p>

I will be adding more test images on outside fires or videos available on internet in the next weeks.

## What this project is trying to achieve

This project is not limited to train a Deep Learning model to detect fire, I'm looking to work on a dron able to use electronics similar or better than the Raspberry Pi to detect fire during its **Programmed flying route** across a forest or protected area and when the model indicates the presence of fire it will a SMS with the coordinates to the Forest Ranger and a MMS with the photo of the model prediction, this is possible with a raspberry pi GSM module.

<p align="center">
<img src="images/drone-ranger.jpg"  width="600" height="400">
</p>


