---
title: Wireless Communication Protocols
nav_order: 10
---
[Home](index.md)

## Introduction to Wireless Communication Protocols

This module introduces wireless communication with the ESP32 microcontroller, focusing on Wi-Fi-based applications. You will learn to connect the ESP32 to a network, upload data to the cloud, control peripherals remotely, and develop web-based interfaces.

---

## 9.1 ESP32 Connect to Wi-Fi

The ESP32 can connect to 2.4GHz Wi-Fi networks, enabling internet-based communication and control.

### Arduino Code Example:
```cpp
#include <WiFi.h>

const char* ssid = "Your_SSID";
const char* password = "Your_PASSWORD";

void setup() {
  Serial.begin(115200);
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("Connected to WiFi");
}

void loop() {
}
```

---

## 9.2 ESP32 Data Upload

Use platforms like **ThingSpeak** to visualize data online.

### Code Snippet (HTTP POST to ThingSpeak):
```cpp
#include <WiFi.h>
#include <HTTPClient.h>

const char* serverName = "http://api.thingspeak.com/update";
String apiKey = "YOUR_API_KEY";

void loop() {
  if(WiFi.status()== WL_CONNECTED){
    HTTPClient http;
    http.begin(serverName + "?api_key=" + apiKey + "&field1=25");
    int httpResponseCode = http.GET();
    http.end();
  }
  delay(15000); // 15s update interval
}
```

---

## 9.3 ESP32 Remote Control

Control peripherals (e.g., LEDs) via commands sent through the web or serial input.

### Example: Toggle LED via Serial
```cpp
#define LED 2

void setup() {
  pinMode(LED, OUTPUT);
  Serial.begin(115200);
}

void loop() {
  if (Serial.available()) {
    char command = Serial.read();
    if (command == '1') digitalWrite(LED, HIGH);
    else if (command == '0') digitalWrite(LED, LOW);
  }
}
```

---

## 9.4 ESP32 Web Server

Build a local web server to control or monitor GPIO devices.

### Basic Web Server Example:
```cpp
#include <WiFi.h>
#include <WebServer.h>

const char* ssid = "Your_SSID";
const char* password = "Your_PASSWORD";

WebServer server(80);

void setup() {
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) delay(500);

  server.on("/", [](){
    server.send(200, "text/html", "<h1>Hello from ESP32</h1>");
  });

  server.begin();
}

void loop() {
  server.handleClient();
}
```

---

## 9.5 Simple Embedded System Project V

**Project Idea:** Create a web interface to display sensor readings (e.g., temperature and humidity from a DHT sensor).

- Read data via GPIO or I²C
- Serve real-time values on a web page

---

## 9.6 Simple Embedded System Project VI

**Project Idea:** Create a web dashboard with control buttons to toggle actuators like LEDs, relays, or buzzers from a browser interface.

---

## Takeaway

Wireless communication via the ESP32 enables embedded systems to integrate with modern cloud platforms and user interfaces. By combining Wi-Fi connectivity, data upload, remote control, and web hosting, you can build full-fledged IoT applications with real-world relevance.

[Module 8](module8.md) - [Module 10](module10.md)
