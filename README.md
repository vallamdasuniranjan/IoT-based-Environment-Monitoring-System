# 🌍 IoT-Based Environment Monitoring System

This project is an **IoT-enabled Environment Monitoring System** that uses an **ESP8266 (NodeMCU)** microcontroller to collect and transmit real-time environmental data including:

- 🌡️ **Temperature**
- 💧 **Humidity**
- 🌱 **Soil Moisture Level**

The data is displayed on a local **OLED screen** and also transmitted to the **Blynk IoT platform**, where it can be monitored from anywhere using a smartphone.

---

## 🔧 Features

- 📲 **Remote Monitoring** via Blynk app (Legacy)
- 🖥️ **OLED Display** (128x64) for real-time on-device feedback
- 🌡️ **DHT11 Sensor** for temperature and humidity
- 🌱 **Soil Moisture Sensor** (analog) for plant/soil condition
- 🌐 **Wi-Fi Connectivity** via ESP8266

---

## 🛠️ Components Used

| Component             | Description                     |
|----------------------|---------------------------------|
| ESP8266 (NodeMCU)     | Wi-Fi-enabled microcontroller    |
| DHT11 Sensor          | Temperature and humidity sensor |
| Soil Moisture Sensor  | Analog output for soil moisture |
| OLED Display (SSD1306)| 128x64 I2C OLED screen          |
| Blynk (Legacy App)    | IoT dashboard (Android/iOS)     |

---

## 📱 Blynk Setup

1. Install the **Blynk Legacy App** from Play Store or App Store.
2. Create a new project and choose **ESP8266** as device.
3. Add 3 Value Display widgets:
   - `V0` – Temperature
   - `V1` – Humidity
   - `V2` – Soil Moisture
4. Copy the **Auth Token** into your Arduino code.

---

## 🔌 Wiring Summary

| Device              | ESP8266 Pin  |
|--------------------|--------------|
| DHT11 Data          | D5 (GPIO14)  |
| Soil Moisture OUT   | A0           |
| OLED SDA (Data)     | D2 (GPIO4)   |
| OLED SCL (Clock)    | D1 (GPIO5)   |

> ⚠️ Ensure all components share a **common GND**.

---

## 🚀 Getting Started

1. Clone this repository.
2. Open the `.ino` file in **Arduino IDE**.
3. Install the required libraries:
   - `Blynk`
   - `Adafruit_SSD1306`
   - `Adafruit_GFX`
   - `DHT sensor library`
4. Enter your Wi-Fi credentials and Blynk Auth Token in the code.
5. Upload the code to your **ESP8266 NodeMCU**.
6. Open the Blynk app and start monitoring!

---

## 📷 Preview

> Add circuit diagrams, breadboard layout, and screenshots of the Blynk app interface here.
![IOT](https://github.com/user-attachments/assets/da840463-9e33-4d04-8a5f-0ef9e375ec2e)

---

## 🧠 Future Improvements

- Upgrade to **Blynk 2.0** or use **MQTT + Node-RED**
- Add **Air Quality Sensors (MQ135, MQ7)**
- Enable **Data Logging** with Google Sheets or Firebase
- Include **Battery Monitoring** for portable setups

---

## 📄 License

This project is open-source and free to use under the MIT License.
