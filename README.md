# 🧺 Smart Laundry Basket

An **Arduino-based IoT laundry management system** designed to automate everyday laundry tasks through **sensor-driven control, real-time monitoring, and wireless connectivity**.

The system combines proximity detection, weight measurement, odor monitoring, motor control, and wireless communication to create a smarter and more convenient laundry experience.

---

## 🎯 Project Overview

The Smart Laundry Basket transforms a traditional laundry basket into an automated IoT-enabled system.

The system can:

* 👋 Detect when someone approaches the basket
* 🚪 Automatically open and close the lid
* ⚖️ Measure the amount of laundry inside
* 🌫️ Detect odor or air-quality changes
* 📱 Send basket information to a connected mobile device
* 📡 Communicate through Wi-Fi and Bluetooth

```text id="0o7b4n"
              👋 User
                │
                ▼
        ┌───────────────┐
        │   Ultrasonic  │
        │    Sensor     │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │ Arduino / MCU │
        └───────┬───────┘
                │
       ┌────────┼────────┐
       ▼        ▼        ▼
    🚪 Lid    ⚖️ Weight  🌫️ Odor
    Control   Tracking   Detection
       │        │        │
       └────────┼────────┘
                ▼
       📡 Wi-Fi / Bluetooth
                │
                ▼
          📱 Mobile Device
```

---

# ✨ Key Features

## 🚪 1. Automated Lid Control

The basket automatically opens its lid when an object or hand is detected nearby.

**How it works:**

* HC-SR04 ultrasonic sensor measures proximity
* Arduino evaluates the distance
* DC motor is activated when the threshold is reached
* Lid opens automatically
* After a defined period without detection, the lid closes

⚡ **Target response time:** Under 1 second

---

## ⚖️ 2. Real-Time Weight Monitoring

A **load cell and HX711 amplifier** are used to measure the amount of laundry inside the basket.

The system can:

* Measure the current laundry weight
* Track changes in basket load
* Provide real-time weight information
* Help users determine when the basket needs to be emptied

The prototype achieved up to **95% measurement accuracy** under the tested conditions.

---

## 🌫️ 3. Odor Detection

A gas sensor monitors the air inside the laundry basket to identify changes associated with unpleasant odors.

When the measured value exceeds the configured threshold:

```text id="2d6g5z"
Gas Sensor
     ↓
Read Air Quality
     ↓
Compare with Threshold
     ↓
 ┌───┴────────┐
 │            │
Normal      Threshold
 │            │
 ▼            ▼
Continue    🚨 Alert
Monitoring
```

The system can trigger:

* 🔊 Buzzer alert
* 📱 Mobile notification
* ⚠️ Odor status update

---

## 📡 4. Wi-Fi & Bluetooth Connectivity

The basket supports wireless communication for remote monitoring.

Users can receive information such as:

* ⚖️ Current fill/weight level
* 🌫️ Odor status
* 🚪 Lid activity
* 🚨 Alerts
* 📊 Sensor readings

This allows the physical basket to communicate its current state to a connected mobile device.

---

# 🔧 Hardware Components

| Component                        | Purpose                      |
| -------------------------------- | ---------------------------- |
| 🤖 **Arduino Uno**               | Main microcontroller         |
| 📏 **HC-SR04 Ultrasonic Sensor** | Proximity detection          |
| ⚖️ **Load Cell**                 | Laundry weight measurement   |
| 🔌 **HX711 Amplifier**           | Load cell signal processing  |
| 🌫️ **MQ-Series Gas Sensor**     | Odor / air-quality detection |
| ⚙️ **DC Motor + Driver**         | Automated lid mechanism      |
| 📡 **ESP8266 / ESP32**           | Wi-Fi communication          |
| 📶 **HC-05 Bluetooth Module**    | Bluetooth communication      |
| 🔊 **Buzzer**                    | Audible alerts               |

---

# ⚙️ How It Works

### 1️⃣ Proximity Detection

The ultrasonic sensor continuously measures the distance between the basket and nearby objects.

When the measured distance falls below the configured threshold, the system activates the lid mechanism.

### 2️⃣ Automated Lid Operation

The Arduino sends a control signal to the motor driver, causing the DC motor to open the lid.

When no nearby object is detected for the configured period, the motor closes the lid.

### 3️⃣ Weight Measurement

The load cell continuously measures the weight of the laundry.

The HX711 amplifier converts the load cell's signal into readable data for the Arduino.

### 4️⃣ Odor Monitoring

The gas sensor periodically samples the air inside the basket.

If the reading exceeds the configured threshold, the system activates an alert.

### 5️⃣ Wireless Communication

Sensor readings and system status are transmitted through Wi-Fi or Bluetooth to a connected mobile device.

```text id="3xq6wy"
Sensors
   │
   ├── Proximity
   ├── Weight
   └── Odor
          │
          ▼
    ┌─────────────┐
    │   Arduino   │
    │    Uno      │
    └──────┬──────┘
           │
    ┌──────┴───────┐
    ▼              ▼
Motor Control   Wireless
    │           Communication
    ▼              │
🚪 Lid             ▼
              📱 Mobile Device
```

---

# 🧠 System Logic

The overall system follows a simple event-driven control approach:

```text id="8g7g5n"
        START
          │
          ▼
   Read Sensor Data
          │
    ┌─────┼─────────┐
    ▼     ▼         ▼
Proximity Weight    Odor
    │     │         │
    ▼     ▼         ▼
Open/Close  Update  Check
   Lid      Status Threshold
                      │
                      ▼
                 🚨 Alert?
                      │
             ┌────────┴────────┐
             ▼                 ▼
            YES                NO
             │                 │
             ▼                 ▼
       Send Alert          Continue
             │             Monitoring
             └──────┬──────────┘
                    ▼
             Wireless Update
                    │
                    ▼
             📱 Mobile Device
```

---

# 🛠️ Technologies

### 🤖 Embedded & IoT

`Arduino Uno` `ESP8266 / ESP32` `HC-05 Bluetooth`

### 📡 Sensors

`HC-SR04` `Load Cell` `HX711` `MQ-Series Gas Sensor`

### ⚙️ Automation

`DC Motor` `Motor Driver` `Sensor-Based Control`

### 💻 Software

`Arduino Programming` `Embedded C/C++` `Wireless Communication`

---

# 📚 Concepts Demonstrated

| Area                        | Concepts                                        |
| --------------------------- | ----------------------------------------------- |
| 🤖 **Embedded Systems**     | Microcontroller programming, sensor integration |
| 🌐 **IoT**                  | Wireless monitoring and connected devices       |
| 📡 **Communication**        | Wi-Fi and Bluetooth                             |
| ⚙️ **Automation**           | Sensor-based automated control                  |
| 📊 **Monitoring**           | Real-time sensor data                           |
| 🔌 **Hardware Integration** | Sensors, motor, amplifier, controller           |
| 🚨 **Event Handling**       | Threshold-based alerts                          |

---

# 🎓 Learning Outcomes

Through this project, I gained practical experience in:

* Integrating multiple sensors into a single embedded system
* Designing automated, condition-based workflows
* Working with load cells and signal amplifiers
* Controlling motors using sensor inputs
* Implementing wireless communication
* Processing and monitoring real-time sensor data
* Designing IoT-oriented solutions
* Integrating hardware and software components into one system

---

# 🔮 Future Improvements

Potential improvements include:

* 📱 Develop a dedicated mobile application
* ☁️ Add cloud-based sensor data storage
* 📊 Create a dashboard for historical laundry data
* 🔔 Implement smarter notification rules
* 🔋 Add battery monitoring and power optimization
* 🤖 Introduce predictive laundry-fill and odor alerts
* 🌐 Add a web-based IoT monitoring dashboard

---

# 👤 Author

### Kenuli Bulathsinghela

📧 **Email:** [kenulibulathsinghela@gmail.com](mailto:kenulibulathsinghela@gmail.com)

💼 **LinkedIn:** [linkedin.com/in/kenulibulathsinghela](https://linkedin.com/in/kenulibulathsinghela)

💻 **GitHub:** [github.com/KenuliBulathsinghela](https://github.com/KenuliBulathsinghela)

🌐 **Portfolio:** [kenuli-bulathsinghela-portfolio.onrender.com](https://kenuli-bulathsinghela-portfolio.onrender.com)

---

<p align="center">

### 🧺 Sense • Automate • Connect

<i>Combining sensors, embedded systems, and IoT to automate everyday tasks.</i>

</p>

