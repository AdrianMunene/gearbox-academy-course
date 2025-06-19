---
title: Wired Communication Protocols I
nav_order: 8
---
[Home](index.md)

# Module 7: Wired Communication Protocols I

## Introduction

This module builds upon your understanding of wired communication by introducing practical interfacing between microcontrollers like the Raspberry Pi Pico and ESP32 using the SPI (Serial Peripheral Interface) protocol. You'll also explore a simple embedded project involving OLED displays.

---

## 7.1 Interfacing to the Pi Pico and ESP32 using SPI

### What is SPI?

SPI (Serial Peripheral Interface) is a high-speed, full-duplex synchronous communication protocol used for short-distance communication with peripheral devices like displays, sensors, and memory modules.

### Key Pins in SPI:
- **MOSI** – Master Out Slave In
- **MISO** – Master In Slave Out
- **SCK** – Serial Clock
- **CS/SS** – Chip/Slave Select

---

### Connecting an OLED Display to Raspberry Pi Pico (SSD1306)

**Wiring (example using SPI):**
- VCC → 3.3V
- GND → GND
- SCK → GP2
- MOSI → GP3
- CS → GP5
- DC → GP4
- RES → GP0

**Python Example (main.py):**
```python
from machine import Pin, SPI
import ssd1306
import framebuf
import time

spi = SPI(0, sck=Pin(2), mosi=Pin(3))
oled = ssd1306.SSD1306_SPI(128, 64, spi, dc=Pin(4), res=Pin(0), cs=Pin(5))

oled.fill(0)
oled.text("Hello, Pico!", 0, 0)
oled.show()
```

**Library Required:** `ssd1306.py` — a driver file for the OLED display.

---

### Connecting OLED to ESP32 using SPI

**Wiring and setup are similar**, but you’ll use ESP32-compatible GPIOs (e.g., D5, D18, D19, D21).

**MicroPython Sample:**
```python
from machine import Pin, SPI
import ssd1306

spi = SPI(1, sck=Pin(18), mosi=Pin(23))
oled = ssd1306.SSD1306_SPI(128, 64, spi, dc=Pin(4), res=Pin(16), cs=Pin(5))

oled.fill(0)
oled.text("ESP32 OLED", 0, 0)
oled.show()
```

---

## 7.2 Simple Embedded System Project I

This capstone activity combines knowledge from prior modules:

### Example Project:
**Mini Weather Display Station**
- Sensor: DHT11/DHT22 or BME280 (for temperature/humidity)
- Display: OLED (SSD1306)
- Controller: Raspberry Pi Pico or ESP32

**Features:**
- Real-time environmental readings
- Display updates every few seconds
- Use of SPI and GPIO in a single project

---

## Takeaway

This module emphasizes hands-on application of SPI communication in real-world scenarios. By integrating displays and sensors using SPI, learners gain practical insight into embedded design. Completing a small system project solidifies concepts from Modules 1 through 6.

[Module 6](module6.md) - [Module 8](module8.md)
