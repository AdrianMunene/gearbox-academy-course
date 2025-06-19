---
title: Introduction to Python and Raspberry Pi Pico
nav_order: 5
---
[Home](index.md)

# Module 4: Introduction to Python and Raspberry Pi Pico

## Introduction

Python is a beginner-friendly, high-level programming language widely used for scripting, automation, and embedded development. When paired with the Raspberry Pi Pico microcontroller, Python (via MicroPython) becomes a powerful tool for rapid prototyping and learning embedded systems concepts.

## Why Python for Embedded Systems?

- Easy to read and write
- Extensive libraries and community support
- MicroPython allows Python to run directly on microcontrollers like the Pico

## Introduction to Raspberry Pi Pico

The Raspberry Pi Pico is a low-cost, high-performance microcontroller board built around the RP2040 chip.

### Key Features:
- Dual-core ARM Cortex-M0+ processor
- 264KB of SRAM and 2MB of flash memory
- 26 GPIO pins for interfacing with sensors and actuators
- USB connectivity for programming
- Supports MicroPython and C/C++

## Setting Up MicroPython on Raspberry Pi Pico

1. Download the MicroPython `.uf2` firmware from the Raspberry Pi website.
2. Press and hold the BOOTSEL button on the Pico and connect it to your PC via USB.
3. Drag and drop the `.uf2` file into the Pico storage device.
4. Use an IDE like **Thonny** to write and upload Python code.

## Writing Your First MicroPython Program

```python
from machine import Pin
import time

led = Pin(25, Pin.OUT)

while True:
    led.toggle()
    time.sleep(1)
```

This script blinks the onboard LED every second.

## Working with GPIO in MicroPython

- **Digital Input**: Reading button presses
```python
button = Pin(14, Pin.IN)
print(button.value())
```

- **Digital Output**: Controlling LEDs or relays
```python
led = Pin(15, Pin.OUT)
led.value(1)  # Turn ON
led.value(0)  # Turn OFF
```

- **PWM**: Dimming an LED or controlling servo
```python
from machine import PWM
pwm_led = PWM(Pin(16))
pwm_led.freq(1000)
pwm_led.duty_u16(32768)  # 50% duty cycle
```

## Takeaway

Python and the Raspberry Pi Pico provide a flexible and accessible environment for learning embedded systems. MicroPython bridges the gap between software programming and hardware control, making it ideal for students and hobbyists alike.

[Module 3](module3.md) - [Module 5](module5.md)
