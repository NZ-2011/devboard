# 🔌 DevBoard — RP2040 Development Board

![License: MIT](https://img.shields.io/badge/Firmware%20License-MIT-blue)
![Hardware License](https://img.shields.io/badge/Hardware%20License-CERN%20OHL%20v2-green)
![GitHub Stars](https://img.shields.io/github/stars/NZ-2011/devboard?style=social)
![GitHub Issues](https://img.shields.io/github/issues/NZ-2011/devboard)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)

> A compact, open-source development board powered by the **Raspberry Pi RP2040** — featuring a 12 MHz crystal oscillator, onboard 3.3V regulation, QSPI Flash, SWD debug header, and 40 broken-out GPIO pins. Built for makers, students, and engineers who want full control.

---
## DEVBOARD
<!-- 📸 BOARD PHOTO: Replace the line below with your actual board photo -->
<img width="3264" height="2448" alt="image" src="https://github.com/user-attachments/assets/b735687c-b51d-4a65-a09a-cb8ba18ef295" />


> 📷 *3D render and PCB layout available in `/assets/images/`*

# Purpose:
it is like an small computer that can fit in ur hand.you plug it in your computer or Laptop to test the prototype or product ypur makimg.it is used to conmect lights,sensors,mototrs according to the code you write.

# How to use it:
1- install the software.and open it.

2-plug the devboard in ur computer or laptop with a good USB cable (a normal cable will work too)

3-upload ur first program

4-connect real stuff. like LEDs,button etc
(always unplug USB before toiching wires)


# Why did i make it:
we all have to start somehwere to i thought to start my PCB,electronics journey from here.i could have selected something easy but where is the fun in that so i decided to make a devboard.and also during this i learned how to use kicad and how to make a PCB,and some ways to fix errors.



---

##  Features

- 🧠 **Microcontroller:** Raspberry Pi RP2040 (Dual-core ARM Cortex-M0+ @ up to 133MHz)
- 💾 **Flash Memory:** 2MB QSPI Flash (W25Q16)
- ⚡ **Power:** USB-C (USB 2.0, 14P) with onboard MCP1700-3300 LDO (3.3V output)
- 📌 **GPIO:** 40 pins broken out via dual 1×20 pin headers (GPIO0–GPIO29 + power/GND)
- 🔮 **Crystal:** 12 MHz external oscillator for accurate USB & timing
- 🔘 **Button:** 1× tactile push button (SW1 — Boot/User)
- 🛠️ **Debug:** 3-pin SWD header (J4) for hardware debugging
- 📐 **Form Factor:** Compact stick ~55mm × 21mm, Pico-compatible footprint
- 🎨 **PCB:** 2-layer green PCB with black pin headers
- 🔧 **Compatible with:** MicroPython, CircuitPython, Arduino IDE, C/C++ SDK

---

## 📐 SCHEMATIC
<img width="3264" height="2448" alt="image" src="https://github.com/user-attachments/assets/674bc5b9-9407-428d-ac6a-6a3dfed07c89" />

## PCB Design
<img width="3264" height="2448" alt="image" src="https://github.com/user-attachments/assets/37fe3ac6-4f6f-4480-bb00-610c6023fa22" />

## 3D imagine
<img width="3264" height="2448" alt="image" src="https://github.com/user-attachments/assets/18105e5d-9ab5-43cd-9df3-a0cf09a0d0e3" />



| Left Header (J2) | Pin | Pin | Right Header (J3) |
|---|---|---|---|
| GPIO0 | 1 | 1 | GPIO16 |
| GPIO1 | 2 | 2 | GPIO17 |
| GPIO2 | 3 | 3 | GPIO18 |
| GPIO3 | 4 | 4 | GPIO19 |
| GPIO4 | 5 | 5 | GPIO20 |
| GPIO5 | 6 | 6 | GPIO21 |
| GPIO6 | 7 | 7 | GPIO22 |
| GPIO7 | 8 | 8 | GPIO23 |
| GPIO8 | 9 | 9 | GPIO24 |
| GPIO9 | 10 | 10 | GPIO25 |
| GPIO10 | 11 | 11 | GPIO26_ADC0 |
| GPIO11 | 12 | 12 | GPIO27_ADC1 |
| GPIO12 | 13 | 13 | GPIO28_ADC2 |
| GPIO13 | 14 | 14 | GPIO29_ADC3 |
| GPIO14 | 15 | 15 | VBUS (5V) |
| GPIO15 | 16 | 16 | 3V3 |
| RUN | 17 | 17 | GND |
| SWCLK | 18 | 18 | GND |
| SWDIO | 19 | 19 | GND |
| GND | 20 | 20 | GND |

> ⚠️ *GPIO26–29 are also ADC-capable. VBUS is 5V direct from USB — use with caution.*

---

##  Getting Started

### Prerequisites

- [Arduino IDE](https://www.arduino.cc/en/software) **or** [Thonny (MicroPython)](https://thonny.org/) **or** [VS Code + Pico SDK](https://www.raspberrypi.com/documentation/microcontrollers/c_sdk.html)
- USB-C cable
- [RP2040 Arduino Core by Earle Philhower](https://github.com/earlephilhower/arduino-pico) (if using Arduino IDE)

### Flash MicroPython

1. Hold the **BOOT button (SW1)** and plug in USB — the board mounts as a USB drive.
2. Download the latest [MicroPython UF2 for RP2040](https://micropython.org/download/rp2-pico/).
3. Drag and drop the `.uf2` file onto the drive — it reboots automatically.
4. Open **Thonny**, select `MicroPython (Raspberry Pi Pico)` as interpreter.
5. Run your first program:

```python
from machine import Pin
from time import sleep

led = Pin(25, Pin.OUT)  # Adjust to your onboard LED pin if present

while True:
    led.toggle()
    sleep(0.5)
```

### Flash with Arduino IDE

1. In Arduino IDE go to **File > Preferences** and add this URL to Board Manager:
   `https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json`
2. Go to **Tools > Board > Board Manager**, search `RP2040` and install.
3. Select **Raspberry Pi Pico** (or Generic RP2040) under Tools > Board.
4. Hold BOOT, plug in USB, then upload your sketch.

### SWD Debugging (Advanced)

Connect a **Picoprobe** or **J-Link** to the 3-pin SWD header (J4):

| J4 Pin | Signal |
|---|---|
| 1 | SWCLK |
| 2 | GND |
| 3 | SWDIO |

---

## 📁 Repository Structure

```
devboard/
├── hardware/
│   ├── schematic.pdf        # Full KiCad schematic export
│   ├── gerbers/             # Gerber files for PCB manufacturing
│   ├── bom.csv              # Bill of Materials
│   └── kicad/               # KiCad 6 source files (.kicad_sch, .kicad_pcb)
├── firmware/
│   └── examples/            # MicroPython & Arduino example sketches
├── assets/
│   └── images/              # Board photos, 3D renders, pinout diagrams
├── docs/
│   └── getting-started.md   # Detailed setup guide
├── LICENSE-HARDWARE         # CERN OHL v2-S
├── LICENSE-FIRMWARE         # MIT
└── README.md
```

---

## 🔧 Hardware Files

| File | Description |
|---|---|
| `hardware/schematic.pdf` | Full circuit schematic (KiCad 6.0) |
| `hardware/gerbers/` | Gerber + drill files — tested with JLCPCB & PCBWay |
| `hardware/bom.csv` | Full BOM: W25Q16, MCP1700-3300, 12MHz crystal, passives |
| `hardware/kicad/` | Editable KiCad source files |

**Key ICs used:**
- `U1` — RP2040 (Raspberry Pi)
- `U2` — MCP1700-3300TT (3.3V LDO, 250mA)
- `U4` — W25Q16 (2MB QSPI Flash)
- `Y1` — 12 MHz Crystal Oscillator

---

## Roadmap

- [ ] Add onboard RGB LED
- [ ] Add USB-to-UART chip option (CH340 / CP2102)
- [ ] Publish CircuitPython examples
- [ ] Add battery/LiPo charging circuit
- [ ] Create detailed Wiki with project examples
- [ ] Design a sensor breakout shield

> 💡 Have an idea? [Open a feature request](https://github.com/NZ-2011/devboard/issues/new?template=feature_request.md)

##Createdwith help of hackclub tutorial.
---

## Contributing

Contributions are what make open source amazing! Here's how you can help:

### Reporting Bugs
1. Check if the issue exists in [Issues](https://github.com/NZ-2011/devboard/issues)
2. Open a new issue with your OS, toolchain version, steps to reproduce, and expected vs actual behavior.

### Submitting Hardware Changes
1. Fork the repo
2. Edit in **KiCad** (same version used for this project)
3. Export updated Gerbers + schematic PDF
4. Submit a Pull Request with a clear description

### Submitting Firmware / Code
1. Fork the repo
2. Create a branch: `git checkout -b feature/your-feature-name`
3. Commit: `git commit -m "Add: description of change"`
4. Push and open a Pull Request

Look for [`good first issue`](https://github.com/NZ-2011/devboard/labels/good%20first%20issue) tags for beginner-friendly tasks!

---

## 📜 License

This project uses two licenses:

- **Firmware & Software** → [MIT License](LICENSE-FIRMWARE) — free to use, modify, and distribute with credit.
- **Hardware (PCB, Schematics)** → [CERN Open Hardware Licence v2 - Strongly Reciprocal](LICENSE-HARDWARE) — open hardware; modifications must also stay open.

---

## 🙌 Acknowledgements

- [Raspberry Pi Foundation](https://www.raspberrypi.com/) for the RP2040 chip and documentation
- [KiCad EDA](https://www.kicad.org/) for open-source PCB design tools
---

<p align="center">⭐ If you find this useful, please star the repo — it helps others discover it!</p>
