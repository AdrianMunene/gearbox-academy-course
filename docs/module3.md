---
title: Electrical Components, Electrical Circuits, ESP32 and Raspberry Pi Pico
nav_order: 4
---
[Home](index.md)

## Introduction to Electronic Circuits and Components
Electronic circuits are the foundation of embedded systems and IoT devices. They consist of various components that work together to control electrical signals.

### Basic Electronic Components
- Resistors – Limit the flow of electric current  
- Capacitors – Store and release electrical energy  
- Inductors – Store energy in a magnetic field when current flows through them  
- Diodes – Allow current to flow in one direction only  
- Transistors – Act as switches or amplifiers  
- Integrated Circuits (ICs) – Contain multiple electronic components on a single chip  
- Microcontrollers (MCUs) – Programmable devices used for processing inputs and outputs  

### Electrical Properties
- Voltage (V) – The difference in electric potential  
- Current (I) – The flow of electric charge (measured in Amperes)  
- Resistance (R) – The opposition to current flow (measured in Ohms)  
- Power (P) – The rate of energy consumption (P = V × I)  
## Overview of ESP32 and Raspberry Pi Pico
ESP32 and Raspberry Pi Pico are two widely used microcontrollers with different capabilities.

### ESP32 Overview
- Dual-core processor (Xtensa LX6 or RISC-V in some models)  
- Built-in Wi-Fi and Bluetooth  
- Supports multiple interfaces: GPIO, SPI, I2C, UART, ADC, DAC  
- Low-power operation for IoT applications  
#### ESP32 Pinout Diagram
![ESP32 Pinout](./images/Pasted%20image%2020250326083734.png)

### Raspberry Pi Pico Overview
- RP2040 dual-core ARM Cortex-M0+ processor  
- Supports USB connectivity for direct programming  
- 26 multi-function GPIO pins  
- No built-in Wi-Fi or Bluetooth (requires external modules)  
#### Raspberry Pi Pico Pinout Diagram
![Raspberry Pi Pico Pinout](./images/Pasted%20image%2020250326083451.png)

### Understanding GPIO (General-Purpose Input/Output)
GPIOs allow microcontrollers to interact with external components.

- Input Mode – Reads data from sensors or buttons  
- Output Mode – Controls LEDs, buzzers, or relays  
- PWM (Pulse Width Modulation) – Simulates analog output using digital signals  
- I2C, SPI, and UART – Communication protocols for connecting peripherals  

## Introduction to the Arduino IDE and Programming the ESP32
The Arduino IDE is a user-friendly environment for writing and uploading code to microcontrollers.

- Use Serial Monitor for debugging  
- Interface sensors using `analogRead()` and `digitalRead()`  
- Connect to Wi-Fi using the `WiFi.h` library for IoT applications  

## Takeaway
This module introduced the fundamental concepts of electronic circuits, microcontroller hardware (ESP32 & Raspberry Pi Pico), and the basics of programming microcontrollers using the Arduino IDE. Understanding electronic components and GPIO operations is crucial for embedded system development, and mastering the ESP32 allows for advanced IoT applications.

[Module 2](module2.md) --- [Module 4](module4.md)
