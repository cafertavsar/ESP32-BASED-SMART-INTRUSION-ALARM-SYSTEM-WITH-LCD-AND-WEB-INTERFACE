# ESP32-Based Smart Intrusion Alarm System with LCD and Web Interface

## Project Description
This project is a smart security system built using the ESP32 development board. The system uses a PIR sensor for motion detection and an LDR sensor to monitor ambient light. It can automatically arm or disarm itself based on environmental conditions. Alerts are provided in real-time via a buzzer and an LED, while the system status is displayed on an I2C LCD. A responsive web-based control interface, accessible over Wi-Fi, allows users to manage the system conveniently.

## Key Features
- **Motion Detection**: Detects human motion using a PIR sensor.
- **Automatic Arming/Disarming**: Automatically arms/disarms based on light levels detected by the LDR sensor.
- **Real-Time LCD Display**: Displays system status and timestamps synced via NTP.
- **Web Interface**: Intuitive interface with controls for Arm, Disarm, Mute, and Test.
- **Alert Mechanism**: Buzzer and LED notifications for motion detection.
- **Wi-Fi Connectivity**: Hosts a local web server with a responsive HTML interface.
- **System Time Sync**: Synchronizes time using NTP (GMT+3).

## Hardware Components
- ESP32 Development Board
- PIR Motion Sensor (e.g., HC-SR501)
- KY-018 LDR Sensor (or equivalent analog LDR module)
- 16x2 I2C LCD Module (address 0x27)
- Passive Buzzer
- LED
- 10kΩ Resistors (for LDR voltage divider if needed)
- Breadboard and jumper wires
- 5V USB Power Supply

## Software Tools
- **Arduino IDE**
- **ESP32 Board Package**
- **Required Libraries**:
  - `WiFi.h`
  - `Wire.h`
  - `LiquidCrystal_I2C.h`
  - `WiFiUdp.h`
  - `NTPClient.h`

## How the System Works

### Motion Detection
- The PIR sensor detects human motion.
- If the system is armed, an alarm is triggered.

### Ambient Light Detection
- The LDR sensor monitors environmental light levels:
  - If the area is dark (LDR < 800), the system arms itself.
  - If the area is bright (LDR > 2000), the system disarms.

### LCD Display
- The I2C LCD shows the current time (via NTP) and system status:
  - `SISTEM PASIF` → Disarmed
  - `ALARM PASIF` → Armed but idle
  - `ALARM AKTIF!!!` → Alarm triggered

### Web Interface
- Accessible via the ESP32's IP address.
- Provides the following controls:
  - `/ARM` → Arm the system
  - `/DISARM` → Disarm the system
  - `/TEST` → Trigger a test alarm
  - `/MUTE` → Mute the buzzer

### Alert Mechanism
- When the system is armed and motion is detected:
  - The LED flashes.
  - The buzzer sounds (unless muted).
  - The alarm state is displayed on the LCD.

## Web Interface Preview
The web interface includes:
- Live system status (`KURULDU` or `PASIF`).
- Four control buttons for manual operation.
- Displays the ESP32's IP address in the footer.
- Modern responsive styling with inline CSS.

## Flow Summary
1. ESP32 connects to Wi-Fi.
2. LCD is initialized and NTP time is synchronized.
3. LDR determines whether to arm/disarm the system.
4. PIR sensor checks for motion when the system is armed.
5. If motion is detected, the alarm triggers.
6. The web interface allows manual overrides.

## Possible Improvements
- Add email or Telegram notifications for alerts.
- Implement a password-protected web interface.
- Enable real-time logging to an SD card or cloud service.
- Integrate with platforms like Blynk or Firebase.
- Use an OLED screen for a more detailed display.

---
This project provides a robust and user-friendly solution for home or office security. With its modular design and potential for further enhancements, it serves as a great starting point for IoT-based security systems.
