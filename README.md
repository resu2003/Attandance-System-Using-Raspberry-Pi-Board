# Attandance System Using Raspberry Pi Board: -
## Hardware Requirements
- Raspberry Pi 3+ (The extra computing power 'oomph' that the Pi provides is invaluable)
- Raspberry Pi Official Camera Module V2 (You can also use the Raspberry Pi High-Quality Camera)
- Micro SD Card
- Power Supply
- Monitor
- HDMI Cord
- Mouse and Keyboard

## Software Requirements
- Raspberry Pi OS
- OpenCV
- pip
- cmake
- build-essential
- pkg-config
- git

## Installation

### Download & Flash Raspberry OS onto the Micro SD Card using Raspberry Pi Imager.
Connect the Raspberry Pi to the monitor with peripheries and make sure that the Pi Camera is installed in the correct slot. Open up the Raspberry Pi Configuration menu (found using the top left Menu and scrolling over preferences) and enable the Camera found under the Interfaces tab. After enabling, reset the Raspberry Pi.

Copy or clone git module files into any directory in the Raspberry OS. Now you can initiate the face detection module.

### Packages to Install

> :exclamation: This will be a long stream of terminal commands forewarning. This will also take a substantial amount of time.

```sh
pip install picamera[array]
sudo apt-get update
sudo apt-get upgrade
sudo apt install cmake build-essential pkg-config git
sudo apt install libjpeg-dev libtiff-dev libjasper-dev libpng-dev libwebp-dev libopenexr-dev
sudo apt install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libdc1394-22-dev libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev
sudo apt install libgtk-3-dev libqtgui4 libqtwebkit4 libqt4-test python3-pyqt5
sudo apt install libatlas-base-dev liblapacke-dev gfortran
sudo apt install libhdf5-dev libhdf5-103
sudo apt install python3-dev python3-pip python3-numpy
```

## Running the Module

Before loading the module, set up all the required packages mentioned in the Packages section. Locate the file named `dataset_picam.py` in the root directory (e.g., `home/pi/facedetection-RapsberryPi-IOT/dataset_picam.py`). Right-click on the file and open that Python script with either Thonny or Geany. Edit the line:

```python
name = 'R Praneeth'  # replace with your name
```

Change the value of the `name` variable to your target person's name and save the file. Go back to the parent directory and locate the folder called "dataset" and create a subfolder with the name you just changed in the Python script, because this is where the dataset training images will be saved.

Jump back to the Python editor (`dataset_picam.py`) and run the code. This will then open up a little window and a terminal window which you can use to save images of your face. Press the Spacebar key to take a picture (take around 10) and then the Q key to close the window. Now the images of your face will be stored in the folder you created for your name.

Open up a new terminal using the black console button on the top left and type the following commands, pressing enter after each line:

```sh
cd facedetection-RapsberryPi-IOT
python train_model.py
```

This will start the training process which you can see occurring for each image that you took of your face. After completion, the Raspberry Pi will have learned what your face looks like. Open a new terminal. Then type the following and press enter after each step:

```sh
cd facedetection-RapsberryPi-IOT
python facial_recog.py
```

A small window will pop up with a live stream of the Raspberry Pi Camera searching for faces, and when it finds one, it will draw a square box around the face. It will also determine if it is a known face, displaying "Unknown" if it is not a known face and the name of the person if it is.

NOTE: If you tip your head to the side a couple of degrees, it will completely disable facial recognition, and if you cover your nose, it struggles as well. Close the terminal window or press Ctrl + C on the keyboard to stop the script running.

## Help and Reference
#### Files inside this project:
- dataset_picam.py: Python Script used to capture train data images when using the Raspberry PI camera module.
- dataset_nrmlcam.py: Python Script used to capture train data images using other camera modules.
- facial_recog.py: Main Python script, running this will initiate the Face Recognition Module.
- train_model.py: Python Script for training test data to Computer Vision using machine learning.
- haarcascade_frontalface_default.xml: XML file that contains face recognition codecs.
- dataset_folder: This is the parent folder of individual target person subfolders where test data images are stored.
- photo_folder: This is where output images will be saved.
#### For learning more about OpenCV visit openv.org. Project reference link here.




