# Deep Soccer using Deepstream-5.1

Individual safety is of paramount importance at all times, whether at work or at home.
To avoid any catastrophes, work sites have zones designated as prohibitive or restricted zones.
Persons entering such prohibited zones are in great danger. Industries or concerned authorities must assure employee protection by implementing preventive measures such as providing suitable safety equipment, and providing occupational health and safety training.
However, no workplace is completely safe from accidents, particularly for construction workers.
When a person enters the restricted zone by accident, an alarm is generated in this situation.
As a result, these systems are vital in guaranteeing worker safety.
This app, built on Nvidia's Deepsteam SDK, would also help corporate buildings, commercial complexes , industries, unmanned areas to detect and help person safety.

![Person_Safety](resource/person_safety.png)

## Index

1. [Introduction](#Introduction)

2. [Deepstream Setup](#Deepstream-Setup)
    1. [Install System Dependencies](#Install-System-Dependencies)
    2. [Install Deepstream](#Install-Deepstream)
3. [Running the Application](#Running-the-Application)
    1. [Clone the repository](#Cloning-the-repository)
    2. [Download the weights file](#download-the-weights-file)
    3. [Build the application](#build-the-application)
    4. [Run with different input sources](#Run-with-different-input-sources)
4. [Citations](#citations)

## Introduction

An Intelligent Video Analytics Pipeline powered by Deepstream and NVIDIA Jetson Xavier NX. 

![Jetson Nano](resource/jetson.jpg)

This project is a proof-of-concept, trying to detect is person inside the restricted area.

## Deepstream Setup

This post assumes you have a fully functional Jetson device. If not, you can refer the documentation [here](https://docs.nvidia.com/jetson/jetpack/install-jetpack/index.html).

### 1. Install System Dependencies

```sh
sudo apt install \
libssl1.0.0 \
libgstreamer1.0-0 \
gstreamer1.0-tools \
gstreamer1.0-plugins-good \
gstreamer1.0-plugins-bad \
gstreamer1.0-plugins-ugly \
gstreamer1.0-libav \
libgstrtspserver-1.0-0 \
libjansson4=2.11-1
```

### 2. Install Deepstream

Download the DeepStream 5.1 Jetson Debian package `deepstream-5.1_5.1.0-1_arm64.deb`, to the Jetson device from [here](https://developer.nvidia.com/deepstream-getting-started). Then enter the command:

```sh
sudo apt install deepstream-5.1_5.1.0-1_arm64.deb
```

For more information, go to the get started page of Deepstream [here](https://docs.nvidia.com/metropolis/deepstream/dev-guide/index.html).

## Running the Application

### 1. Clone the repository

This is a straightforward step, however, if you are new to git, I recommend glancing threw the steps.

First, install git

```sh
sudo apt install git
```

Next, clone the repository

```sh
# Using HTTPS
https://github.com/MANJUSHREE-GS/Person_Safety_Detection.git
# Using SSH
git@github.com:MANJUSHREE-GS/Person_Safety_Detection.git
```

### 2. Download the weights file

Download the weights file from [google-drive](https://drive.google.com/file/d/1nZds8loc4XdG4KQGdgoU-xyOgwJqv9m-/view?usp=sharing) and place it in `models/YOLOv4` directory.

### 3. Build the application

First, build the application by running the following command:

```sh
make clean && make -j$(nproc)
```

This will generate the binary called `person_safety`. This is a one-time step and you need to do this only when you make source-code changes.

### 4. Run with different input sources

Next, create a file called `inputsources.txt` and paste the path of videos or rtsp url.

```sh
file:///home/zxcv/Downloads/specialization.mp4
rtsp://admin:admin%5346@194.162.5.14:554/stream
```

Now, run the application by running the following command:

```sh
./person_safety
```

## Citations

* [AlexeyAB/darknet](https://github.com/AlexeyAB/darknet)
* [AkashJames](https://github.com/kn1ghtf1re/YOLOv4-Deepstream)


Please find the Links of a Demo video, [here](https://youtu.be/qECftC_X5t4)
