# libneon

[![Component Registry](https://components.espressif.com/components/eaarjun/libneon/badges)](https://components.espressif.com/components/eaarjun/libneon)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

**libneon** is a lightweight, dependency-free Neopixel (WS2812/WS2812B) driver library for the ESP-IDF framework. It utilizes the ESP32's built-in RMT (Remote Control) peripheral for highly accurate, non-blocking LED signal generation. 

This library includes built-in visual effects and is designed to be highly efficient and easy to integrate into your embedded projects.

## Features
* **Zero Dependencies:** Pure ESP-IDF implementation.
* **Hardware-Driven:** Uses the RMT peripheral to perfectly time the Neopixel data protocol without keeping the CPU busy.
* **Built-in Effects:** Includes pre-programmed lighting effects and color gradients.
* **Multi-Target Support:** Fully compatible with `esp32`, `esp32c3`, and `esp32s3`.

## Installation

You can easily add this component to your ESP-IDF project using the ESP Component Registry manager. 

Run the following command in your project directory:

```bash
idf.py add-dependency "eaarjun/libneon^1.0.0"
