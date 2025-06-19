---
title: Sensors and Actuators
nav_order: 6
---
[Home](index.md)

# Module 5: Sensors and Actuators

## Introduction

Sensors and actuators form the physical interface between an embedded system and the real world. Sensors collect data from the environment, while actuators perform actions based on that data. Understanding how to interface these components with a microcontroller like the RP2040 is fundamental to embedded systems.

---

## 5.1 Understanding Electronic Circuits and Components

### Key Electronic Components:
- **LEDs**: Emit light when powered; used for visual indicators.
- **Resistors**: Limit current to protect components.
- **Switches**: Mechanically open or close circuits.
- **Breadboard & Jumper Wires**: For prototyping without soldering.

### Simple LED Circuit:
A basic LED circuit includes an LED connected in series with a resistor to a GPIO pin and ground. This prevents the LED from burning out due to excessive current.

---

## 5.2 Introduction to Sensors and Actuators

### What is a Sensor?
A sensor detects physical changes in the environment (e.g., light, temperature, pressure) and outputs corresponding electrical signals.

### What is an Actuator?
An actuator receives an electrical signal and converts it into physical movement (e.g., motor rotation, LED illumination).

### Key Differences:
| Feature     | Sensor                      | Actuator                     |
|-------------|-----------------------------|------------------------------|
| Direction   | Input to system             | Output from system           |
| Function    | Sense physical environment  | Act upon the environment     |
| Examples    | Temperature, Light, Pressure| Motors, LEDs, Buzzers        |

---

## 5.3 Interfacing External LEDs, Switches, and Pushbuttons with RP2040

### Interfacing LEDs:
```python
from machine import Pin
import time

led = Pin(15, Pin.OUT)

while True:
    led.toggle()
    time.sleep(0.5)
```

### Interfacing a Pushbutton:
```python
button = Pin(14, Pin.IN, Pin.PULL_DOWN)

while True:
    if button.value():
        print("Button Pressed")
```

### Using PWM with Python:
```python
from machine import Pin, PWM
import time

pwm = PWM(Pin(15))
pwm.freq(1000)

while True:
    for duty in range(0, 65535, 1000):
        pwm.duty_u16(duty)
        time.sleep(0.01)
```

### Analog Inputs:
The RP2040 has ADC pins for reading analog sensor values (e.g., potentiometer, light sensor).

```python
from machine import ADC, Pin
import time

adc = ADC(Pin(26))  # GPIO26 is ADC0

while True:
    value = adc.read_u16()
    print("Analog value:", value)
    time.sleep(0.5)
```

---

## Takeaway

By learning to interface sensors and actuators with the RP2040, you gain practical skills for building interactive and automated systems. This includes understanding basic electronics, controlling outputs like LEDs, reading inputs from switches, and using PWM and ADC for richer control.

[Module 4](module4.md) - [Module 6](module6.md)
