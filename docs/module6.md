---
title: Introduction to Wired Communication Protocols
nav_order: 7
---
[Home](index.md)

## Introduction to Wired Communication Protocols

Wired communication protocols are essential for data exchange between microcontrollers and peripheral devices such as sensors, displays, and actuators. Understanding these protocols allows developers to build systems that are modular, scalable, and robust.

---

## Communication Protocols in Embedded Systems

Communication protocols define rules for how data is transmitted between devices. In embedded systems, common wired communication protocols include:

- **UART (Universal Asynchronous Receiver/Transmitter)**  
  - Simple, asynchronous serial communication.  
  - Uses TX and RX lines.  
  - Widely used for debugging and sensor interfacing.

- **I²C (Inter-Integrated Circuit)**  
  - Two-wire communication: SDA (data) and SCL (clock).  
  - Supports multiple devices on the same bus (master-slave).  
  - Common in sensor modules and EEPROMs.

- **SPI (Serial Peripheral Interface)**  
  - Four-wire communication: MOSI, MISO, SCK, and SS.  
  - High-speed full-duplex communication.  
  - Suitable for displays and memory cards.

---

## Working with Communication Protocols (I²C, UART, SPI)

### I²C Example (RP2040):
```python
from machine import Pin, I2C

i2c = I2C(0, scl=Pin(1), sda=Pin(0), freq=100000)
devices = i2c.scan()

print("I2C devices found:", devices)
```

### UART Example (RP2040):
```python
from machine import UART

uart = UART(0, baudrate=9600)
uart.write('Hello UART')
```

### SPI Example (RP2040):
```python
from machine import SPI, Pin

spi = SPI(0, baudrate=500000, polarity=0, phase=0, sck=Pin(2), mosi=Pin(3), miso=Pin(4))
```

---

## Ultrasonic Sensor with Raspberry Pi Pico

Ultrasonic sensors measure distance by using sound waves. The HC-SR04 is a popular module.

### Circuit Connections:
- VCC to 5V
- GND to GND
- TRIG to GPIO
- ECHO to GPIO

### MicroPython Example:
```python
from machine import Pin, time_pulse_us
import time

trig = Pin(3, Pin.OUT)
echo = Pin(2, Pin.IN)

while True:
    trig.low()
    time.sleep_us(2)
    trig.high()
    time.sleep_us(10)
    trig.low()

    duration = time_pulse_us(echo, 1)
    distance = duration * 0.0343 / 2
    print("Distance: {:.2f} cm".format(distance))
    time.sleep(1)
```

---

## PIR Sensor with Raspberry Pi Pico

PIR (Passive Infrared) sensors detect motion by sensing infrared radiation changes.

### Circuit Connections:
- VCC to 5V
- GND to GND
- OUT to GPIO

### MicroPython Example:
```python
from machine import Pin
import time

pir = Pin(14, Pin.IN)

while True:
    if pir.value():
        print("Motion detected!")
    else:
        print("No motion")
    time.sleep(1)
```

---

## Takeaway

Understanding and implementing wired communication protocols is fundamental to embedded systems development. Whether using UART for debugging, I²C for sensor networks, or SPI for high-speed data transfer, these protocols expand the functionality of microcontrollers. Practical experience with sensors like ultrasonic and PIR builds the foundation for smart, responsive systems.

[Module 5](module5.md) - [Module 7](module7.md)
