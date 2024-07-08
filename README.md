<p align="center">
<img src="https://github.com/Smart-Blueprints/IoT-itegration-of-KS0085/assets/64748988/87f10600-e8b9-48b8-9e1f-84e65e170176" width="50%">
</p>

## Introduction 

Welcome to our development project! Here, we integrate the Keystudio KS0085 layout with the Thingsboard platform using an ESP32 as the central node in our smart layout. This project aims to create a seamless and efficient smart environment, leveraging the power of IoT and cloud platforms. The software architecture is based on the development of source code to be programmed into the microcontroller and the configuration on the IoT platform. This guide details the steps required to set up the IDE, as well as the libraries and classes used for communication with the ThingsBoard platform and the control of sensors and actuators.

## Key Components 

1. **Keystudio KS0085 Layout**: This versatile and user-friendly layout provides a range of sensors and actuators for various applications.
2. **ESP32**: A powerful and efficient microcontroller, serving as the central node for data collection, processing, and communication.
3. **Thingsboard**: An open-source IoT platform for data visualization, processing, and remote management of connected devices.

## Features

- Real-time data collection and visualization 
- Remote control and management of sensors and actuators 
- Scalable and flexible architecture for various use cases 
- Easy integration with other IoT devices and platforms 

## Table of Content

1. [Setting Up the Development Environment](#setting-up-the-development-environment)
2. [ESP32 Source Code Analysis](#esp32-source-code-analysis)
3. [Libraries Used](#libraries-used)
4. [Key Code Features](#key-code-features)
5. [Configuration in ThingsBoard](#configuration-in-thingsboard)

---

## Setting Up the Development Environment

To program the ESP32 Dev Kit 1 with the Arduino IDE, follow these steps:

### 1. Installing Modules to Handle ESP32 Boards 

The steps for this installation may vary depending on the operating system, but generally involve:

1. **Open the Arduino IDE** and navigate to `File > Preferences`.
2. **Add the additional board URL** in the "Additional Boards Manager URLs" field:

3. **Go to `Tools > Board > Boards Manager...`** and search for "ESP32".
4. **Select and install** the `esp32` package.

### 2. Selecting the Target Board 

1. **Go to `Tools > Board`** and select `ESP32 Dev Module`.
2. **Configure additional options** as needed (e.g., the COM port).

### 3. Start Programming 

Once the board packages are installed, you can start programming the microcontroller using the C++ programming language in the Arduino IDE.

---

## ESP32 Source Code Analysis

This section examines the essential libraries used, the critical functions implemented, and the logic behind the bidirectional communication between the ESP32 and ThingsBoard.The complete code is provided in the folder codes of this repo.

### Essential Libraries 

Some of the libraries used include:

- `WiFi.h`: For WiFi connection.
- `PubSubClient.h`: For MQTT communication with ThingsBoard.
- `DHT.h`: For reading temperature and humidity sensors.

### Critical Functions 

Some of the critical functions implemented are:

- **WiFi Setup**: Configures and connects the ESP32 to a WiFi network.
- **MQTT Communication**: Manages communication with ThingsBoard via the MQTT protocol.
- **Sensor and Actuator Control**: Implements logic for reading sensor data and controlling actuators.

### Communication Logic 

The logic behind bidirectional communication includes:

1. **Establish WiFi Connection**.
2. **Connect to ThingsBoard**.
3. **Send Sensor Data** to ThingsBoard.
4. **Receive Commands from ThingsBoard** to control actuators.

---

## Libraries Used

`WiFi.h`

- Provides functions to establish and manage WiFi connections on the ESP32.
- Enables communication with the local network and the ThingsBoard platform.

`ThingsBoard.h`

- Facilitates integration with ThingsBoard.
- Allows sending sensor data and controlling actuators via the MQTT protocol.

`Arduino_MQTT_Client.h`

- Provides functionalities for MQTT communication.

The combination of these libraries offers a robust framework for communicating with ThingsBoard and controlling sensors and actuators in the KS0085 layout.

---

## Key Code Features

The code provided to the ESP32 includes the following functionalities:

### 1. Hardware Setup 

- Initializes GPIO pins for sensors and actuators.
- Configures the pins as inputs or outputs as needed.

### 2. WiFi and ThingsBoard Connection 

- The device connects to a WiFi network using the provided credentials.
- Establishes a connection with the ThingsBoard server using the device access token.

### 3. Sending Data to ThingsBoard 

- Sensor data (gas, light, soil moisture, rain, and motion detection) is periodically sent to ThingsBoard in JSON format.
- This allows real-time data visualization and analysis on the platform.

### 4. Receiving Shared Attributes 

- The device listens for changes in shared attributes from ThingsBoard.
- Processes these changes to control actuators and layout components (two LEDs, fan, relay, and servomotors for the door and window).

### 5. Main Loop (`loop()`) 

- Acquires sensor data.
- Sends data to ThingsBoard.
- Executes shared attribute handling functions.

---

## Configuration in ThingsBoard

To efficiently collect sensor data and control actuators, follow these steps in ThingsBoard:

### 1. Creating an Account on ThingsBoard 

- Visit [thingsboard.cloud](https://thingsboard.cloud).
- Sign up using a Google, Facebook, GitHub account, or an email address.
- The credentials used for this project are:
  - **Email:** smart_home@etlgr.com
  - **Password:** smart_home

### 2. Creating the Device and MQTT Binding 

- Once the account is created, create a device in ThingsBoard that will represent the ESP32.
- A unique access token will be generated, which will act as the authentication key for the MQTT connection between the ESP32 and ThingsBoard.

### 3. Configuring the Dashboard 

- Configure a dashboard in ThingsBoard to visualize sensor data and control actuators.
- Use **Simple Value** and **Chart Card** widgets to display sensor values over time.
- Add an **Update Multiple Attributes** widget that includes switches to control LEDs, fan, relay, and servomotors.
- For each widget, configure the device and the associated parameter name.

With this guide, you will have a fully functional system to interact with the ThingsBoard platform and control the components of the KS0085 layout.



We hope this project inspires you to explore the endless possibilities of IoT and smart environments. Happy tinkering 💙!

