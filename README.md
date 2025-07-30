# 🌐 Gateway Node for Multi-Protocol IoT System
This repository contains a C++/Arduino-based application that acts as a Gateway Node in a multi-protocol IoT system. It runs on the ESP32-S3 and demonstrates real-time sensor data acquisition and communication using a combination of:

📡 LoRa (long-range wireless)
🔌 RS-485 (Modbus-style wired)
🌐 MQTT (cloud communication)
🔷 BLE (optional extension)
🟢 CAN (for industrial integration, optional)

## Description

The gateway parses, classifies, and forwards data to the cloud (e.g., ThingsBoard) or local networks in real time using FreeRTOS for task management and efficient concurrency.

**Key Features:**

✅ LoRa reception and parsing of remote sensor packets (temperature, humidity)

✅ RS-485 data acquisition from industrial nodes (BMP280, SHT4x, etc.)

✅ CAN bus interface for motor/sensor communication (via MCP2515 or on-chip CAN)

✅ MQTT integration (public IP, payload packaging, cloud publishing)

✅ BLE expansion support for short-range sensor communication

✅ NeoPixel feedback for command status indication

✅ NTP time synchronization for accurate timestamping

✅ Built on FreeRTOS (multi-tasked, non-blocking design)

📡 Protocol Summary
Protocol	Purpose	Status
LoRa	Long-range wireless	✅ Enabled
RS-485	Wired industrial data	✅ Enabled
CAN	Real-time control	⚙️ Optional
MQTT	Cloud connectivity	✅ Enabled
BLE	Mobile sensor input	⚙️ Optional

🔧 Platform
Board: ESP32-S3-WROOM
Framework: Arduino + FreeRTOS
Cloud: ThingsBoard / Custom MQTT Broker

⚙️ Actuator Node for IoT Control
This repository contains firmware for an Actuator Node designed to receive commands via MQTT and act upon them in real time. It can be integrated into a larger system involving LoRa, RS-485, and BLE communication layers.

🛠️ Features
✅ MQTT command reception and parsing (via cloud)

✅ Command-controlled NeoPixel status LED

✅ Support for commands like light on, light off, fan start, etc.

✅ Device ID filtering for multi-node control

✅ Future-ready: can be extended to relay control, PWM motors, servo, etc.

✅ FreeRTOS optional for concurrency and responsiveness
