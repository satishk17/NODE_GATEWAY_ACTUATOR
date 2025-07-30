# IoT Gateway, Sensor Node, and Actuator System
This repository contains firmware and configuration for an IoT system involving a Gateway, Sensor Node, and Actuator Node using LoRa, MQTT, RS-485, and Wi-Fi. Designed for ESP32-based microcontrollers and expandable to include BLE, CAN, and RS-232 interfaces.

# 📡 System Overview
The system demonstrates how distributed edge nodes collect and transmit sensor data to a central Gateway, which processes and forwards the data to cloud services via MQTT. The Gateway also receives commands and controls actuators in real-time (e.g., NeoPixels or RS-485 devices).

# 🔑 Key Features
✅ Gateway Node (ESP32):
LoRa Receiver for wireless sensor data.

Dual MQTT clients:

Local Broker (device data ingestion).

Cloud Broker (e.g., ThingsBoard via RS-485).

Wi-Fi enabled with dynamic public IP acquisition.

NeoPixel control via MQTT command.

UART streaming of sensor values to another host (debugging/logging).

✅ Sensor Node (ESP32 or custom MCU):
LoRa Transmitter sending temperature and humidity readings.

Can be powered via battery and send periodic updates.

Lightweight JSON message structure.

✅ Actuator Node (ESP32/RS-485):
Listens to MQTT commands and controls local hardware.

Parses messages from the Gateway or directly from the cloud.

🧠 How It Works
🔁 Sensor Node:
Reads temperature & humidity values from sensor.

Sends data as a LoRa packet to the Gateway.

# 🔁 Gateway Node:
Receives LoRa payload.

Parses and publishes structured data to MQTT broker.

Sends values over UART and logs via Serial.

Receives MQTT command messages and routes to actuators (e.g., via RS-485 or GPIO).

# 🔁 Actuator Node:
Waits for control messages.

Parses JSON and executes commands (e.g., turn on light).

⚙️ Getting Started
📦 Prerequisites
ESP32 (Gateway)

LoRa modules (SX127x series)

RS-485 transceivers (e.g., MAX485)

MQTT Broker (e.g., Mosquitto or ThingsBoard)

Optional: CAN transceivers or BLE modules

# 📥 Dependencies
Arduino IDE or PlatformIO

Libraries:

-PubSubClient
-LoRa
-ArduinoJson
-WiFi
-Adafruit_NeoPixel

🚀 Build & Upload
Gateway Node:

Clone repo:
git clone https://github.com/your-username/gateway-node.git

Open in Arduino IDE.

Set board to ESP32.

Upload to your device.

Sensor Node:

Open sensor_node.ino

Configure sensor type and LoRa settings.

Upload to ESP32 or other compatible board.

Actuator Node:

Open actuator_node.ino

Configure GPIO or RS-485 handling logic.

Upload and test command reception.

# 🧪 Testing the System
Use MQTT.fx or Mosquitto to simulate cloud MQTT commands.

Monitor LoRa communication using Serial logs.

Confirm RS-485 or NeoPixel activation.

Verify data upload to cloud (e.g., ThingsBoard dashboard).

# 🗃 Code Structure
plaintext
Copy
Edit
gateway-node/
├── main.cpp
├── lora_handler.cpp/h
├── mqtt_handler.cpp/h
├── uart_logger.cpp/h
├── neopixel_control.cpp/h
└── config.h

# 🧩 Future Expansion (Optional)
✅ BLE provisioning for initial Wi-Fi setup.

✅ CAN protocol integration for industrial data.

✅ Thread or Matter protocol for smart home applications.

✅ FreeRTOS implementation for multitasking.

# 🌐 Cloud Integration
Supports any MQTT 3.1/3.1.1 broker.

Tested with:

ThingsBoard Cloud

AWS IoT Core

Local Mosquitto Broker

# 📞 Command Format Example
MQTT Topic:
command/light/control

Payload:

json
Copy
Edit
{
  "device_id": "temphum",
  "command": "light on"
}
