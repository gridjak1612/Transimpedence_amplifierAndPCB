# Analog CMOS Transimpedance Amplifier (TIA) & PCB Design

## 📜 Overview
This project involves the design, simulation, and hardware validation of a **Transimpedance Amplifier (TIA)** using **SCL 180nm CMOS technology**. The TIA is designed to convert input photocurrent into a proportional output voltage with high linearity and stability, specifically tailored for optical front-end applications.

In addition to the chip design, this repository contains the **PCB design files (Altium)** for a custom test board. The PCB features a photodiode emulator and an IC socket to facilitate practical characterization and modular testing of the fabricated chip.

## ⚡ Key Specifications
| Parameter | Value | Condition |
| :--- | :--- | :--- |
| **Technology Node** | SCL 180nm CMOS | |
| **Transimpedance Gain** | **66.26 dBΩ** (~2.06 kΩ) | @ 27°C, TT Corner |
| **Bandwidth (-3dB)** | **2.26 MHz** | $C_{pd} = 100 \text{pF}$ |
| **Output Swing** | ~0.90 V | Linear Region |
| **Photodiode Load** | 100 pF | Modeled Capacitance |
| **Feedback Resistor ($R_f$)** | 2.05 kΩ | On-chip PDK Poly Resistor |
| **Supply Voltage** | 1.8 V | |

## 🏗️ Circuit Design
### Core Architecture
The TIA is built upon a **Differential Amplifier with a Current Mirror Active Load**. This topology was selected to achieve:
* High open-loop gain for precise feedback control.
* Controlled input common-mode range (ICMR).
* Robustness against Process, Voltage, and Temperature (PVT) variations.

### Design Methodology
* **$g_m/I_D$ Methodology**: Used for transistor sizing to optimize power efficiency and ensure strong inversion operation.
* **Feedback Network**: A resistive feedback loop ($R_f$) sets the gain, while the amplifier's compensation ensures stability even with a large 100pF input capacitive load.

*(Place your schematic screenshots here, e.g., `docs/schematic.png`)*

## 🖥️ PCB Design (Hardware Validation)
A custom 2-layer Printed Circuit Board (PCB) was designed in **Altium Designer** to bridge simulation with real-world testing.

### Board Features:
* **IC Socket**: Allows for quick swapping of TIA chips without soldering.
* **Photodiode Emulator**: On-board circuitry (variable capacitive loading) to replicate photodiode behavior.
* **Test Points**: Dedicated points for probing Input Current ($I_{in}$), Output Voltage ($V_{out}$), and Bias levels.
* **Noise Reduction**: Uses polygon pours for solid Ground (GND) and Power (VDD) planes.

*(Place your PCB 3D view or layout screenshots here, e.g., `docs/pcb_3d.png`)*

## 📂 Repository Structure
```text
├── design/
│   ├── schematics/       # Cadence Virtuoso Schematics
│   ├── layout/           # CMOS Layout views
│   └── simulation/       # DC, AC, and Transient logs
├── pcb/
│   ├── altium_project/   # .PrjPcb, .SchDoc, .PcbDoc files
│   ├── gerbers/          # Manufacturing files
│   └── bom/              # Bill of Materials
├── docs/                 # Datasheets and Report
└── README.md
