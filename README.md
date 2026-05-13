<p align="center">
<img width="129" height="129" alt="icon" src="https://github.com/user-attachments/assets/936c77b3-44ef-4b81-8532-66ca58a50ba8" />

</p>

<h1 align="center">iThaDMA Tool</h1>

<p align="center">
  Windows desktop utility for flashing, DNA reading, and benchmarking DMA FPGA boards via JTAG.
</p>

<p align="center">
  <a href="../../releases/latest">
    <img src="https://img.shields.io/github/v/release/YOUR_USERNAME/iThaDMATool?style=for-the-badge&color=00cfff&label=Download" />
  </a>
  &nbsp;
  <img src="https://img.shields.io/badge/platform-Windows%2010%2F11-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=for-the-badge" />
</p>

---

## Download

Go to the [**Releases**](../../releases/latest) page and download **`iThaDMA Tool Setup x.x.x.exe`**.

Run the installer — choose your install directory, click Install, done.

---
<img width="2264" height="1478" alt="image" src="https://github.com/user-attachments/assets/659a5345-4963-4dcb-8ac3-67309acc51c7" />

## Features

| Tab | Description |
|-----|-------------|
| **Flash** | Write firmware (`.bin`) to SPI flash on Artix-7 boards via JTAG |
| **DNA** | Read the unique 57-bit Device DNA from any Xilinx 7-series FPGA |
| **Speed Test** | Benchmark PCIe read throughput with PCIleech |

- Auto-detects connected JTAG adapters (CH347 and FTDI RS232) on startup
- Supports **35T**, **75T**, and **100T** Artix-7 boards
- Live terminal output with colour-coded stdout/stderr

---

## Requirements

- Windows 10 or Windows 11 (64-bit)
- A Xilinx Artix-7 FPGA board (35T / 75T / 100T)
- A JTAG adapter: **CH347** or **FTDI RS232** (FT2232H / FT4232H / FT232H)

---

## Driver Setup

After installing, open the `drivers\` folder inside the install directory:

| Adapter | Driver to run |
|---------|--------------|
| CH347 | `CH341PAR.EXE` — install the CH347 driver |
| FTDI RS232 | `zadig-2.9.exe` in the `drivers\` folder → select your device → install **WinUSB** |

> Only needed once per machine.

---

## Usage

### Flash firmware

1. Open the **Flash** tab.
2. Select your **adapter** and **board**.
3. Click **Browse** and select your `.bin` firmware file.
4. Click **Flash Firmware** and monitor the progress bar and terminal.

> First flash on a new adapter may take 2–3 minutes. Do not disconnect the board.

### Read Device DNA

1. Open the **DNA** tab.
2. Select your adapter and board.
3. Click **Read DNA**. The 64-bit hex value appears in the result box.

### Speed test

1. Flash your firmware and **reboot the host PC** so the FPGA enumerates on the PCIe bus.
2. Open the **Speed Test** tab.
3. Click **Run Benchmark**. Results appear after ~10 seconds.

---

## Supported hardware

| Adapter | VID:PID |
|---------|---------|
| CH347 (JTAG) | `1A86:55DD` |
| FTDI FT2232H | `0403:6010` |
| FTDI FT4232H | `0403:6011` |
| FTDI FT232H  | `0403:6014` |

| Board | FPGA |
|-------|------|
| Squirrel / 35T boards | XC7A35T |
| 75T boards | XC7A75T |
| Enigma-X1 / 100T boards | XC7A100T |

---

## Credits

Built by **ithalove** — Discord: `ithalove`

Powered by [OpenOCD](https://openocd.org/) and [PCIleech](https://github.com/ufrisk/pcileech).
