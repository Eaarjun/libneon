# libneon

[![Component Registry](https://components.espressif.com/components/eaarjun/libneon/badges)](https://components.espressif.com/components/eaarjun/libneon)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

**libneon** is a lightweight, dependency-free Neopixel (WS2812/WS2812B) driver library for ESP-IDF.
It uses the ESP32's built-in RMT peripheral for accurate, non-blocking LED control.

It also includes a small animation engine with built-in effects, so you can get something running quickly without writing everything from scratch.

---

## ✨ Features

* **Zero Dependencies** – pure ESP-IDF implementation
* **Hardware-Driven** – precise timing via RMT (no CPU blocking)
* **Built-in Effects** – gradients, pulse, spinner, composite animations
* **Modular Design** – clean separation of encoder, effects, and examples
* **Multi-Target Support:**

  * ESP32
  * ESP32-C3
  * ESP32-S3
  * ESP32-C6

---

## 📦 Installation

Add the component via ESP Component Registry:

```bash
idf.py add-dependency "eaarjun/libneon^1.0.2"
```

---

## 🚀 Quick Start

```cpp
#include <neo/encoder.hpp>
#include <examples.hpp>

extern "C" void app_main()
{
    neo::led_encoder encoder(
        neo::encoding::ws2812b,
        neo::make_rmt_config(GPIO_NUM_8)
    );

    examples::run_all(encoder, 16);
}
```

---

## ⚠️ Important (C++ Setup)

ESP-IDF creates a default `test.c`, but **libneon uses C++**.

Rename:

```bash
main/test.c → main/test.cpp
```

Then update `main/CMakeLists.txt`:

```cmake
idf_component_register(
    SRCS "test.cpp"
    INCLUDE_DIRS "."
    REQUIRES libneon
)
```

---

## 🎨 Built-in Examples

You can run animations directly:

```cpp
#include <neo/examples.hpp>

example_simple_blink(GPIO_NUM_8, 16);
example_composite(GPIO_NUM_8, 16);
examples_run_all(GPIO_NUM_8, 16);
```

### Available animations:

* 🌈 Gradient / Rainbow
* 💓 Pulse effects
* 🌀 Spinner effects
* 🔴 Simple blink
* 🎨 Static gradients
* 🔥 Composite animations (with transitions)

---

## 🧠 Architecture Overview

```text
FX Engine → Callback → Encoder (RMT) → LED Strip
```

* **FX Engine** → generates animation frames
* **Alarm** → drives updates (FPS-based)
* **Encoder** → converts frames to RMT signals
* **RMT Peripheral** → handles precise transmission

---

## 📌 Notes

* Make sure the GPIO matches your hardware wiring
* WS2812 LEDs use **GRB color order** (handled internally)
* RMT handles all timing automatically

---

## 📄 License

MIT License
