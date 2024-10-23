# Intruderdetection
# ESP32 Intruder Detection Project

## Overview
This project demonstrates the use of the ESP32 microcontroller and ESP32-CAM module for real-time intruder detection. The application leverages machine learning for object detection, specifically designed to identify unauthorized access in a designated area.

## Table of Contents
- [Features](#features)
- [Hardware Requirements](#hardware-requirements)
- [Software Requirements](#software-requirements)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Contributing](#contributing)
- [License](#license)

## Features
- Real-time object detection using a trained model.
- Wi-Fi connectivity for remote monitoring.
- Inference results displayed in the Serial Monitor.

## Hardware Requirements
- ESP32-CAM Module
- FTDI USB to TTL converter
- Jumper wires
- Power supply (5V)

## Software Requirements
- Arduino IDE
- ESP32 Board Package for Arduino
- Edge Impulse Studio for model training
- Python (optional, for additional scripts)

## Installation

### Set Up Arduino IDE:
1. Install the latest version of the Arduino IDE.
2. Add the ESP32 board package by navigating to `File > Preferences > Additional Board Manager URLs` and adding the following link:
https://dl.espressif.com/dl/package_esp32_index.json
3. Open `Tools > Board > Board Manager`, search for "ESP32," and install it.

### Connect the ESP32-CAM:
1. Use the FTDI USB to TTL converter to connect the ESP32-CAM to your computer.
2. Make the appropriate connections (GND to GND, VCC to 5V, TX to RX, RX to TX).

### Upload Code:
1. Open the provided Arduino sketch in the IDE.
2. Modify the Wi-Fi credentials in the sketch.
3. Select the appropriate board (ESP32 Wrover Module) and port, then upload the code.

### Model Training and Deployment:
1. Use Edge Impulse Studio to train your object detection model based on your dataset.
2. Export the model as TensorFlow Lite and upload it to the ESP32.

### Code Modification:
- Make the following changes in `conv.cpp` and `depthwise_conv.cpp` files:

```cpp
data_dims_t input_dims = {
 {.width = input_width, .height = input_height,
  .channels = input_depth, .extra = 1}
};

data_dims_t output_dims = {
 .width = output_width, .height = output_height,
 .channels = output_depth, .extra = 1
};

data_dims_t filter_dims = {
 .width = filter_width, .height = filter_height,
 .channels = 0, .extra = 0
};
```


Ensure these changes are reflected in the files you downloaded from Edge Impulse. If you encounter issues, it's advisable to apply these changes manually.
Usage
After uploading the code and deploying the model, open the Serial Monitor in Arduino IDE to view the IP address assigned to the ESP32-CAM. The model will process the incoming video stream and perform inference, detecting any intrusions based on the trained model's predictions.

## How It Works
The ESP32-CAM utilizes a machine learning model trained to detect intrusions. The model is developed using Edge Impulse for data acquisition and training. Once deployed to the ESP32, it processes the incoming video stream in real time and identifies any intruders based on the model's predictions. The results of the predictions are displayed in the Serial Monitor of the Arduino IDE, allowing users to monitor detected intrusions effectively.



