<p align="center">
  <img src="./img.png" alt="Project Banner" width="100%">
</p>

# Smart Medicine Box

## Basic Details

### Team Name: HerNova

### Team Members
- Member 1: Navdha Vasanth - College Of Engineering Thalassery
- Member 2: Manjima N - College Of Engineering Thalassery

### Hosted Project Link
[mention your project hosted link here]

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

![Architecture Diagram](docs/architecture.png)
*Explain your system architecture - components, data flow, tech stack interaction*

**Application Workflow:**

![Workflow](docs/workflow.png)
*Add caption explaining your workflow*

---

### For Hardware:

#### Schematic & Circuit

![Circuit](Add your circuit diagram here)
*Add caption explaining connections*

![Schematic](Add your schematic diagram here)
*Add caption explaining the schematic*

#### Build Photos

![Team](Add photo of your team here)

![Components](Add photo of your components here)
*List out all components shown*

![Build](Add photos of build process here)
*Explain the build steps*

![Final](Add photo of final product here)
*Explain the final build*

---

## Additional Documentation

### For Web Projects with Backend:

#### API Documentation

**Base URL:** `https://api.yourproject.com`

##### Endpoints

**GET /api/endpoint**
- **Description:** [What it does]
- **Parameters:**
  - `param1` (string): [Description]
  - `param2` (integer): [Description]
- **Response:**
```json
{
  "status": "success",
  "data": {}
}
```

**POST /api/endpoint**
- **Description:** [What it does]
- **Request Body:**
```json
{
  "field1": "value1",
  "field2": "value2"
}
```
- **Response:**
```json
{
  "status": "success",
  "message": "Operation completed"
}
```

[Add more endpoints as needed...]

---

### For Mobile Apps:

#### App Flow Diagram

![App Flow](docs/app-flow.png)
*Explain the user flow through your application*

#### Installation Guide

**For Android (APK):**
1. Download the APK from [Release Link]
2. Enable "Install from Unknown Sources" in your device settings:
   - Go to Settings > Security
   - Enable "Unknown Sources"
3. Open the downloaded APK file
4. Follow the installation prompts
5. Open the app and enjoy!

**For iOS (IPA) - TestFlight:**
1. Download TestFlight from the App Store
2. Open this TestFlight link: [Your TestFlight Link]
3. Click "Install" or "Accept"
4. Wait for the app to install
5. Open the app from your home screen

**Building from Source:**
```bash
# For Android
flutter build apk
# or
./gradlew assembleDebug

# For iOS
flutter build ios
# or
xcodebuild -workspace App.xcworkspace -scheme App -configuration Debug
```

---

### For Hardware Projects:

#### Bill of Materials (BOM)

| Component | Quantity | Specifications | Price | Link/Source |
|-----------|----------|----------------|-------|-------------|
| Arduino Uno | 1 | ATmega328P, 16MHz | ₹450 | [Link] |
| LED | 5 | Red, 5mm, 20mA | ₹5 each | [Link] |
| Resistor | 5 | 220Ω, 1/4W | ₹1 each | [Link] |
| Breadboard | 1 | 830 points | ₹100 | [Link] |
| Jumper Wires | 20 | Male-to-Male | ₹50 | [Link] |
| [Add more...] | | | | |

**Total Estimated Cost:** ₹[Amount]

#### Assembly Instructions

**Step 1: Prepare Components**
1. Gather all components listed in the BOM
2. Check component specifications
3. Prepare your workspace
![Step 1](images/assembly-step1.jpg)
*Caption: All components laid out*

**Step 2: Build the Power Supply**
1. Connect the power rails on the breadboard
2. Connect Arduino 5V to breadboard positive rail
3. Connect Arduino GND to breadboard negative rail
![Step 2](images/assembly-step2.jpg)
*Caption: Power connections completed*

**Step 3: Add Components**
1. Place LEDs on breadboard
2. Connect resistors in series with LEDs
3. Connect LED cathodes to GND
4. Connect LED anodes to Arduino digital pins (2-6)
![Step 3](images/assembly-step3.jpg)
*Caption: LED circuit assembled*

**Step 4: [Continue for all steps...]**

**Final Assembly:**
![Final Build](images/final-build.jpg)
*Caption: Completed project ready for testing*

---

### For Scripts/CLI Tools:

#### Command Reference

**Basic Usage:**
```bash
python script.py [options] [arguments]
```

**Available Commands:**
- `command1 [args]` - Description of what command1 does
- `command2 [args]` - Description of what command2 does
- `command3 [args]` - Description of what command3 does

**Options:**
- `-h, --help` - Show help message and exit
- `-v, --verbose` - Enable verbose output
- `-o, --output FILE` - Specify output file path
- `-c, --config FILE` - Specify configuration file
- `--version` - Show version information

**Examples:**

```bash
# Example 1: Basic usage
python script.py input.txt

# Example 2: With verbose output
python script.py -v input.txt

# Example 3: Specify output file
python script.py -o output.txt input.txt

# Example 4: Using configuration
python script.py -c config.json --verbose input.txt
```

#### Demo Output

**Example 1: Basic Processing**

**Input:**
```
This is a sample input file
with multiple lines of text
for demonstration purposes
```

**Command:**
```bash
python script.py sample.txt
```

**Output:**
```
Processing: sample.txt
Lines processed: 3
Characters counted: 86
Status: Success
Output saved to: output.txt
```

**Example 2: Advanced Usage**

**Input:**
```json
{
  "name": "test",
  "value": 123
}
```

**Command:**
```bash
python script.py -v --format json data.json
```

**Output:**
```
[VERBOSE] Loading configuration...
[VERBOSE] Parsing JSON input...
[VERBOSE] Processing data...
{
  "status": "success",
  "processed": true,
  "result": {
    "name": "test",
    "value": 123,
    "timestamp": "2024-02-07T10:30:00"
  }
}
[VERBOSE] Operation completed in 0.23s
```

---

## Project Demo

### Video
[Add your demo video link here - YouTube, Google Drive, etc.]

*Explain what the video demonstrates - key features, user flow, technical highlights*

### Additional Demos
[Add any extra demo materials/links - Live site, APK download, online demo, etc.]

---

## AI Tools Used (Optional - For Transparency Bonus)

If you used AI tools during development, document them here for transparency:

**Tool Used:** [e.g., GitHub Copilot, v0.dev, Cursor, ChatGPT, Claude]

**Purpose:** [What you used it for]
- Example: "Generated boilerplate React components"
- Example: "Debugging assistance for async functions"
- Example: "Code review and optimization suggestions"

**Key Prompts Used:**
- "Create a REST API endpoint for user authentication"
- "Debug this async function that's causing race conditions"
- "Optimize this database query for better performance"

**Percentage of AI-generated code:** [Approximately X%]

**Human Contributions:**
- Architecture design and planning
- Custom business logic implementation
- Integration and testing
- UI/UX design decisions

*Note: Proper documentation of AI usage demonstrates transparency and earns bonus points in evaluation!*

---

## Team Contributions

- [Name 1]: [Specific contributions - e.g., Frontend development, API integration, etc.]
- [Name 2]: [Specific contributions - e.g., Backend development, Database design, etc.]
- [Name 3]: [Specific contributions - e.g., UI/UX design, Testing, Documentation, etc.]

---

## License

This project is licensed under the [LICENSE_NAME] License - see the [LICENSE](LICENSE) file for details.

**Common License Options:**
- MIT License (Permissive, widely used)
- Apache 2.0 (Permissive with patent grant)
- GPL v3 (Copyleft, requires derivative works to be open source)

---

Made with ❤️ at TinkerHub
