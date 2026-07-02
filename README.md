# Smart-Laundry-Basket

An Arduino Uno-based IoT laundry basket that automates lid control, tracks laundry weight, detects odor build-up, and supports remote monitoring over Wi-Fi and Bluetooth.

Overview
This project automates everyday laundry management by combining sensor-driven automation with wireless connectivity. The basket opens its lid automatically when someone approaches, tracks how full it is by weight, flags unpleasant odors before they become a problem, and reports status to a connected mobile device.

Features
 * Automated lid control — an ultrasonic sensor detects hand/object proximity and triggers a DC motor to open and close the lid, with lid response time under 1 second.
 * Real-time weight tracking — a load cell measures laundry load in the basket with up to 95% measurement accuracy, helping users know when it's time for a wash.
 * Odor detection — a gas sensor continuously monitors air quality inside the basket and triggers an alert when unpleasant odors are detected.
 * Wi-Fi & Bluetooth connectivity — basket status (fill level, odor alerts, lid activity) can be monitored and controlled remotely from a mobile device.
   
Hardware Used
Components; 
Arduino Uno
Main microcontroller
Ultrasonic sensor (HC-SR04)
Proximity detection for lid automation
Load cell + HX711 amplifier
Weight measurement
Gas sensor (MQ series)
Odor / air quality detection
DC motor + driver
Lid open/close mechanism
Wi-Fi module (ESP8266/ESP32)
Wireless data transmission
Bluetooth module (HC-05)
Local mobile pairing/control

How It Works
* The ultrasonic sensor continuously scans for objects within a set proximity threshold.
When triggered, the DC motor opens the lid; after a timeout with no motion detected, it closes automatically.
* The load cell reads current weight and streams it to the connected app in real time.
* The gas sensor samples air quality on a fixed interval; readings above a defined threshold fire a buzzer alert and push a notification over Wi-Fi/Bluetooth.
* All sensor data is aggregated on the Arduino and transmitted to a paired mobile device for remote visibility.
  
