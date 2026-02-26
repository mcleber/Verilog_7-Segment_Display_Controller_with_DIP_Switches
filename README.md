# 💡 7-Segment Display Controller with DIP Switches
### BCD Decoder and Display Driver using Verilog on FPGA

![Platform](https://img.shields.io/badge/Platform-FPGA-blue)
![Language](https://img.shields.io/badge/Language-Verilog-orange)
![Board](https://img.shields.io/badge/Board-Tang%20Primer%2020K-green)
![IDE](https://img.shields.io/badge/IDE-Gowin%20IDE-blue)
![License](https://img.shields.io/badge/License-GPL--3.0-blue)

<p align="center"> <img src="assets/gif_display.gif" width="300" alt="Circuit in action"> </p>

---

## 📖 Overview

This project implements a BCD (Binary-Coded Decimal) decoder using Verilog for FPGA. It reads DIP switch input and drives a common-cathode 7-segment display, showing digits 0–8 or ‘E’ for invalid input combinations.

Key learning objectives:

- Basic Verilog development
- Input decoding from DIP switches
- Driving a 7-segment display
- FPGA pin mapping using Gowin IDE

---

## 🧰 Hardware Required

### Electronics
- 1 × Tang Primer 20K FPGA (GW2A-LV18PG256C8/I7) with Dock
- 1 × Common-cathode 7-segment display
- 1 × 8-position DIP switch
- 7 × Current-limiting resistors (~150Ω)
- 8 × Pull-down resistors (10 kΩ)

### Miscellaneous
- Jumper wires
- Breadboard
- USB-C cable

---

## 📷 Hardware Setup

### Circuit Diagram
<p align="center">
  <img src="assets/encoder_decoder_bcd_esquematico.png" width="800" alt="Circuit Diagram">
</p>

---

## 📊 Truth Tables

The developed system operates based on two fundamental truth tables that define the entire behavior of the circuit.  

The first table establishes the relationship between the DIP switch key combinations and the corresponding decimal values, while the second table determines how these values should be displayed on the 7-segment display.

<p align="center">
  <img src="assets/Table1.png" width="800" alt="Input to Decimal Table">
</p>

**Outputs from Table 1:**

D3 = HGFEDCBA

D2 = H’GFEDCBA + H’G’FEDCBA + H’G’F’EDCBA + H’G’F’E’DCBA

D1 = H’GFEDCBA + H’G’FEDCBA + H’G’F’E’D’CBA + H’G’F’E’D’C’BA

D0 = H’GFEDCBA + H’G’F’EDCBA + H’G’F’E’D’CBA + H’G’F’E’D’C’B’A


<p align="center">
  <img src="assets/Table2.png" width="800" alt="Decimal to 7-Segment Table">
</p>

These tables serve as essential references both for the Verilog code implementation and for the practical verification of the circuit.

---

## 🔌 Verilog Code and Constraints

Available in the `src` and `constraints` directories.

---

## 🧠 How It Works

1. Read DIP switch input
2. Convert the binary input to decimal (BCD)
3. Map decimal to 7-segment encoding
4. Display the output on the 7-segment display
5. Show ‘E’ when invalid combinations are detected

---

## 📂 Project Structure

```text
Verilog_7-Segment_Display_with_DIP_Switches/
│
├── assets/
│   ├── Table1.png
|   ├── Table2.png
|   ├── encoder_decoder_bcd_esquematico.png
│   └── gif_display.gif
|
├── constraints/
│   └── encoder_bcd.cst
|
├── src/
│   └── encoder_bcd.v
|
├── License
|
└── README.md
```

---

## 🎮 Features

- Modular Verilog code structure
- Full BCD decoding (0–8)
- Error detection for invalid inputs
- Clear FPGA pin mapping
- Hands-on learning for beginners in FPGA development

---

## 🚀 Future Improvements

- Support for multiple 7-segment displays
- Dynamic brightness control using PWM
- Support for 4-bit binary input (0–15)
- Add testbench for simulation

---

## ⚠️ Common Errors and Solutions

During development, I encountered some practical issues that may occur with any beginner:

**Incorrect use of reserved pins:**  
During signal mapping, an SPI-dedicated pin was incorrectly assigned to the display LEDs, triggering a ‘cannot be placed according to constraint’ synthesis error. The issue was resolved by reassigning the connection to an available GPIO pin, following the Dock’s pinout documentation.

**Reversed wiring on the display:**  
One of the segment wires was connected incorrectly, causing incorrect numbers to be displayed. After reviewing the segment order (a–g), I corrected the connections, and the display started working correctly.

---

## 📜 License

This project is open-source and available under the GPL-3.0 License.

---

## 👨‍💻 Author

Developed as an FPGA learning project. Strongly inspired by the "cistern" example from the book Eletrônica Digital, Verilog e FPGA.
