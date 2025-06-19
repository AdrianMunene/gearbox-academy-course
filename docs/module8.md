---
title: Wired Communication Protocols II
nav_order: 9
---
[Home](index.md)


# Wired Communication Protocols II

This module continues the exploration of wired communication, focusing on the I²C protocol. You'll interface sensors like AHT10 and DHT11 with both the Raspberry Pi Pico and ESP32, and apply your skills in embedded system projects involving serial communication.

---

## 8.1 Interfacing the RP2040 and ESP32 using I²C

### What is I²C?

I²C (Inter-Integrated Circuit) is a two-wire communication protocol commonly used to connect multiple slave devices to one or more master devices. It uses:
- **SDA (Serial Data)**
- **SCL (Serial Clock)**

### Connecting an AHT10 Sensor via I²C

**Wiring (Raspberry Pi Pico):**
- VCC → 3.3V
- GND → GND
- SDA → GP0
- SCL → GP1

**MicroPython Example for Pico:**
```python
from machine import I2C, Pin
import ahtx0
import time

i2c = I2C(0, scl=Pin(1), sda=Pin(0))
sensor = ahtx0.AHT10(i2c)

while True:
    print("Temperature:", sensor.temperature)
    print("Humidity:", sensor.relative_humidity)
    time.sleep(2)
```

**ESP32 with Arduino IDE:**
- Install the AHT10 library
- Use provided example code to read temperature and humidity data

### Alternative: DHT11 Sensor with Pico
```python
from machine import Pin
import dht
import time

sensor = dht.DHT11(Pin(15))

while True:
    sensor.measure()
    print("Temp:", sensor.temperature(), "°C")
    print("Humidity:", sensor.humidity(), "%")
    time.sleep(2)
```

---

## 8.2 Simple Embedded System Project III

### Example Project: Environmental Monitor

- Microcontroller: Raspberry Pi Pico or ESP32
- Sensor: AHT10 or DHT11
- Communication: I²C
- Output: Serial plot or OLED display

This project demonstrates real-time environmental data acquisition using I²C sensors, suitable for indoor monitoring.

---

## 8.3 Simple Embedded System Project IV

### Serial Communication in Practice

- Use the UART protocol to display data on a serial monitor
- Interface two microcontrollers or send sensor data to a PC

**Arduino Code Example:**
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  Serial.println("Sensor reading...");
  delay(1000);
}
```

**MicroPython on Raspberry Pi Pico:**
```python
from machine import UART
import time

uart = UART(0, baudrate=9600)

while True:
    uart.write("Sending data over UART\n")
    time.sleep(1)
```

---

## Takeaway

This module reinforced communication skills using I²C and UART. By integrating sensors like AHT10 and DHT11 with Pico or ESP32, learners expand their ability to build modular, sensor-rich systems. Serial communication provides a basic yet powerful tool for debugging and data visualization.

[Module 7](module7.md) - [Module 9](module9.md)
