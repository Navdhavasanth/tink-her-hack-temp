<p align="center">
  <img src="./img.png" alt="Project Banner" width="100%">
</p>

# Smart Medicine Bo

## Basic Details

### Team Name: HerNova

### Team Members
- Member 1: Navdha Vasanth - College Of Engineering Thalassery
- Member 2: Manjima N - College Of Engineering Thalassery

### Hosted Project Link
https://navdhavasanth.github.io/tink-her-hack-temp/

### Project Description
The Smart Medicine Box is an IoT-enabled device that helps patients adhere to their medication schedules using automated audio-visual alarms. It utilizes physical push buttons for the user to manually confirm when a dose is taken, logging the activity to track compliance. If a patient misses a scheduled dose, the system automatically sends a mobile alert to their caregiver, ensuring peace of mind and better health management.

### The Problem statement
Medication non-adherence—forgetting to take pills or taking the wrong dose—is a leading cause of hospitalizations and reduced quality of life, particularly for the elderly and those with chronic illnesses. Existing pill organizers are passive and cannot alert a caregiver if a dose is missed, leaving a dangerous gap in home-based healthcare monitoring.

### The Solution
The Smart Medicine Box provides an active monitoring system that automates the dosing process. By integrating a Real-Time Clock (RTC) with an ESP32/Arduino, the box triggers loud buzzers and flashing LEDs at exact prescribed times. Unlike traditional boxes, it requires the user to press a physical confirmation button after taking their pills, which stops the alarm and logs the event. If the button isn't pressed within a set window, the system automatically sends a remote notification to a caregiver’s phone, ensuring immediate intervention if a dose is missed.


## Technical Details

### Technologies/Components Used

**For Software:**
-Languages used: C++ (Arduino Framework), JSON (for API/WiFi configuration).
-Frameworks used: Arduino Core for ESP32/Arduino.
-Libraries used: * RTClib.h (to interface with the DS3231 clock).
-LiquidCrystal_I2C.h (for the LCD display).
    -WiFi.h & HTTPClient.h (for sending notifications to the caregiver).
    -EzButton.h (optional, but great for handling button debouncing).
-Tools used: Arduino IDE or VS Code (with PlatformIO), Serial Monitor (for debugging), and Fritzing (for circuit design).

**For Hardware:**
Main Components:
-Microcontroller: ESP32 DevKit V1 (chosen for built-in Wi-Fi) or Arduino Nano.
-Real-Time Clock: DS3231 RTC Module (includes a coin cell battery for time backup).
-Display: 16x2 I2C LCD Screen (to show the current time and "Take Meds" messages).
-Input: Momentary Push Buttons (to confirm medication intake).
-Alerts: 5V Active Buzzer and 5mm High-Brightness LEDs (Red/Green).
-Power: 9V Battery or a 5V Micro-USB power adapter.

Specifications:
-Input Voltage: 5V – 9V DC.
-Communication: I2C Protocol (shared by LCD and RTC to save pins).
-Button Logic: Active-LOW (using internal pull-up resistors).
-Connectivity: 2.4GHz Wi-Fi (for IoT alerts).

Tools Required:
-Soldering Iron & Solder: To secure connections on a perf-board or PCB.
-Breadboard & Jumper Wires: For initial prototyping and testing the button logic.
-Multimeter: To check continuity and ensure the buttons are triggering correctly.
-Hot Glue Gun / Small Screws: To mount the buttons and electronics inside your box enclosure.
-Wire Strippers: For preparing the leads to the buttons and LEDs.

---

## Features

-Precise Scheduling: High-accuracy RTC module ensures alarms go off at the exact time.
-Audio-Visual Alerts: Loud buzzer and flashing LEDs catch the user's attention.
-Physical Confirmation: Push button requires the user to interact with the box to stop the alarm.
-Remote Caregiver Alerts: Wi-Fi notifications are sent if a dose is not confirmed within a set time.

## Implementation

### For Software:

-Time Sync: Initialize the RTC module via the RTClib library to set the current time during the first run.
-Alarm Loop: Run a continuous loop() that compares the current time from the RTC to the scheduled alarm times stored in the code.
-Button Interrupts: Program the buttons to trigger an Interrupt Service Routine (ISR). This immediately stops the buzzer and LEDs when pressed.
-IoT Notification Logic: If the current time exceeds an alarm time by 30 minutes without a button press, trigger a HTTP POST request to a service like IFTTT to send a notification

### For Hardware:

#### Components Required

-Microcontroller: ESP32 DevKit V1 (Wi-Fi capable) or Arduino Nano.
-RTC Module: DS3231 (for accurate timekeeping with coin cell backup).
-Input: 7x Momentary Push Buttons (Tactile switches for 7 days).
-Output: 1x 5V Active Buzzer, 7x LEDs (5mm, Green).
-Display: 16x2 I2C LCD Module.
-Prototyping: Breadboard, Jumper Wires (Male-to-Female/Male-to-Male), Resistors (220$\Omega$ for LEDs).

#### Circuit Setup

-I2C Devices: Connect the LCD and RTC modules to the ESP32 using the I2C protocol:
  -VCC to 3.3V/5V.
  -GND to GND.
  -SDA to GPIO 21.
  -SCL to GPIO 22.
-Push Buttons: Connect one pin of each button to a unique GPIO pin (e.g., GPIO 13, 14, 25, 26, 27, 32, 33) and the other pin to GND.
-Alerts: Connect the Buzzer positive pin to a GPIO pin (e.g., GPIO 18) and negative to GND. Connect LEDs through 220$\Omega$ resistors to their respective GPIO pins.
-Power: Connect the main power source to the USB port or the VIN pin (if using 5V).

## Project Documentation

### For Software:

#### Screenshots 
<img width="1913" height="913" alt="Screenshot 2026-02-28 081853" src="https://github.com/user-attachments/assets/a26c5c2d-bace-4efe-93bc-7b78f49cf644" />

<img width="1914" height="906" alt="Screenshot 2026-02-28 081939" src="https://github.com/user-attachments/assets/f77fefb3-9c1d-4876-b685-64fdad474ab6" />

<img width="1919" height="904" alt="Screenshot 2026-02-28 082037" src="https://github.com/user-attachments/assets/73636f5c-6554-4dab-9aa1-2e1ac634cb38" />

<img width="1919" height="904" alt="Screenshot 2026-02-28 082213" src="https://github.com/user-attachments/assets/0a8f0779-a685-4c77-b2ee-5a89595cf171" />

#### Diagrams

**System Architecture:**

![WhatsApp Image 2026-02-28 at 10 56 12 AM](https://github.com/user-attachments/assets/911079b5-f32a-453a-8945-54edb85f4ead)

*Explain your system architecture - components, data flow, tech stack interaction*

**Application Workflow:**

<img width="572" height="1908" alt="medflowdia drawio" src="https://github.com/user-attachments/assets/b7172410-fb1e-4489-9a7f-e7b4d79da503" />

*Add caption explaining your workflow*

---

### For Hardware:

#### Schematic & Circuit

![WhatsApp Image 2026-02-28 at 11 00 02 AM](https://github.com/user-attachments/assets/145ea037-0f09-4ed5-be5c-7d2f1f11b562)

*Add caption explaining connections*
#### Build Photos

Team Photo
![WhatsApp Image 2026-02-28 at 11 07 52 AM](https://github.com/user-attachments/assets/090d8e2b-37f6-4d9d-b169-b57d43bc3007)


#### Installation Guide

**For Android (APK):**

1.Install Arduino IDE
2.Install ESP32 board from Board Manager
3.Install libraries:
4.RTClib
5.WiFi
6.LiquidCrystal_I2C (if LCD used)
7.Upload code
8.Set correct medicine time in code

### For Hardware Projects:

#### Bill of Materials (BOM)

| Component | Quantity | Specifications | Price |
|-----------|----------|----------------|-------|
| ESP32 | 1 | WiFi + Bluetooth | ₹350 |
| DS3231 RTC | 1 | I2C Module | ₹150 | 
| Ultrasonic Sensor HC-SR04r | 1| 2–400 cm | ₹80|
| Breadboard | 1 | 830 tie |₹120 | 
| Jumper Wires | 20 | Male-to-Male | ₹100 | 
| Buzzer |1|5V Active |₹20| 

**Total Estimated Cost:** ₹830

#### Assembly Instructions

1.Connect RTC to ESP32 (SDA→21, SCL→22)
2.Connect Buzzer to D23
3.Connect Red LED to D5 with resistor
4.Connect Green LED to D18 with resistor
5.Connect Push Button to D4
6.Connect Ultrasonic sensor to D5 (Trig) and D4 (Echo)
7.Power ESP32 via USB

#### Demo Output

**Example 1: Normal Reminder Flow**
System Initializing...
RTC Connected Successfully
Current Time: 18:59:50

Reminder in 10 seconds...
Pre-alert Activated!
Buzzer Beep...
Red LED Blinking...

Current Time: 19:00:00
Medicine Time Reached!
Buzzer ON
Waiting for user confirmation...

Medicine Taken!
Green LED ON
Buzzer OFF

Sending Confirmation SMS...
SMS Sent Successfully
System Reset for Next Schedule

**Example 2: Medicine Not Taken (Alert Case)**
Current Time: 19:00:00
Medicine Time Reached!
Buzzer ON
Waiting for user confirmation...

No confirmation detected.
Sending Alert SMS to Guardian...

Alert SMS Sent Successfully
System Entered Alert Mode

**Example 3: System Startup**
Booting Smart Medicine Box...
WiFi Connected
RTC Time Synced
System Ready
Next Medicine Time: 19:00:00


## Project Demo

### Video
[Add your demo video link here - YouTube, Google Drive, etc.]

*Explain what the video demonstrates - key features, user flow, technical highlights*


## Team Contributions

- Navdha Vasanth: Hardware Design & Firmware Development
- Manjima N: IoT Integration & Documentation

---

## License

This project is licensed under the MIT License .


---

Made with ❤️ at TinkerHub
