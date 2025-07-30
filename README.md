#  IoT Gateway, Sensor Node, and Actuator System
This repository contains firmware and configuration for a complete FreeRTOS-based IoT system implemented on ESP32 microcontrollers. The system includes a Gateway, Sensor Nodes, and Actuator Nodes communicating via LoRa, MQTT, RS-485, ESP_NOW and Wi-Fi. Designed for scalability and real-time responsiveness, it is extendable to BLE, CAN, RS-232, and Matter/Thread protocols.

# System Overview
- This project demonstrates a real-world edge-to-cloud IoT architecture:
- Sensor Nodes collect environmental data (temperature, pressure, presence, light,humidity).
- Data is transmitted wirelessly (via LoRa/ESP-NOW/RS-485) to a central Gateway.
- The Gateway parses, logs, displays, and forwards the data to a cloud MQTT broker.
- The system receives remote commands to control Actuator Nodes via MQTT.

All devices run under FreeRTOS, leveraging the built-in multitasking support on ESP32 platforms to handle concurrent tasks such as communication, sensor reading, display updates, and actuation.

# Key Features
  =>  Gateway Node (ESP32-S3 / ESP32-C6)
  - Receives LoRa packets from Sensor Nodes.
  - Publishes JSON data to MQTT broker over Wi-Fi.
  - Controls NeoPixel or toggles sensors via MQTT command.
  - UART output for real-time monitoring/logging.
  - Interfaces with Actuators via RS-485 or GPIO.
  - Subscribes to MQTT topics and routes control commands.
  - Fully multi-threaded using FreeRTOS tasks for:
  - LoRa reception
  - MQTT publish/subscribe
  - RS-485 interaction

 =>  Sensor Node (ESP32-S3)
  - Reads data from:
  - BMP280 (Temperature & Pressure)
  - Presence Sensor (PIR or IR)
  - Light/RGB sensors (optional)
  - Displays current status on an I²C OLED.
  - Transmits data over:
  - LoRa
  - ESP-NOW
  - RS-485
  - Battery-efficient periodic transmission

🧠 Managed with FreeRTOS tasks:
Sensor polling
OLED updates
LoRa/RS-485 communication

=>  Actuator Node (ESP32-S3 / RS-485)
  - Waits for ESP_NOW or RS-485 command messages.
  - Parses JSON control commands.
  - Controls:
  - Relays
  - Motors
  - Lights

# =>  How It Works
 **Gateway Node**
 - Receives LoRa packets.
 - Parses and logs over UART.
 - Publishes data to cloud via MQTT.
 - Listens for MQTT commands and dispatches to actuators (via RS-485 or GPIO).

**Sensor Node**
- Periodically reads sensors: BMP280, presence sensor, lux/RGB.
- Displays values on OLED.
- Sends data using LoRa, ESP-NOW, or RS-485.
- Operates in FreeRTOS tasks for low-latency processing.

**Actuator Node**
- Listens for control messages from Gateway.
- Parses JSON payload.
- Triggers GPIO or RS-485-based actions.

#  Getting Started
Prerequisites
- ESP32 / ESP32-S3 Boards
- SX127x LoRa Modules
- BMP280 Sensor ( altitude and pressure [hpa])
- HTU Sensor ( temperature and humidity )
- BH1750 Sensor ( lightmeter sensor [lux])
- TCS34725 Sensor ( rgb color sensor )
- Presence Sensor HLK-LD2410 ( human body motion [m])
- I²C OLED Display (SSD1306 or SH1106)
- RS-485 Transceivers (e.g., MAX485)
- MQTT Broker (e.g., Mosquitto, AWS IoT, ThingsBoard)
- Presence Sensor (e.g., PIR or IR)

# 📥 Dependencies
Install these Arduino libraries via Library Manager:
- PubSubClient
- LoRa
- ArduinoJson
- WiFi
- Adafruit_BMP280
- Adafruit_GFX
- Adafruit_SSD1306
- Adafruit_NeoPixel
- esp_now
- BH1750
- Adafruit_TCS34725
- SPI
- U8g2lib
- Adafruit_HTU21DF

(Optional: ESP-NOW / Modbus libraries for advanced protocols)

🚀 Build & Upload
Gateway Node
bash
Copy
Edit
git clone https://github.com/your-username/gateway-node.git
Open in Arduino IDE.

Select board: ESP32-S3 or ESP32-C6.
- Configure:
- Check pin numbers and wifi credentials

## Code Structure

- gateway-node
- Sensor-node
- actuator-node


