<div align="center">

<img src="assets/icon.png" alt="Gantry" width="150">

# Gantry

**Three-Axis Gantry Control System**

[![release](https://img.shields.io/github/v/release/bluerobotics/gantry?style=flat-square)](https://github.com/bluerobotics/gantry/releases/latest)
[![build](https://img.shields.io/github/actions/workflow/status/bluerobotics/gantry/release.yml?style=flat-square)](https://github.com/bluerobotics/gantry/actions)
[![downloads](https://img.shields.io/github/downloads/bluerobotics/gantry/total?style=flat-square)](https://github.com/bluerobotics/gantry/releases)
[![license: MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)

[View Changelog](CHANGELOG.md) • [Download Latest Release](https://github.com/bluerobotics/gantry/releases/latest)

</div>

---

## Overview

Firmware for the Gantry three-axis motion control system, built on the Teknic ClearCore platform. This firmware provides precision control for X, Y, and Z axis movements with synchronized dual-motor Y-axis control, homing routines, and network/USB communication.

**Designed to work with:** [BR Equipment Control App](https://github.com/bluerobotics/br-equipment-control-app) - A Python/Tkinter GUI for controlling and monitoring the Gantry and other Blue Robotics manufacturing equipment.

## Features

- **Three-axis control** - Independent X, Y, Z axis control with synchronized Y-axis dual motors
- **UDP/Ethernet communication** - Network-based control with device discovery
- **USB Serial fallback** - Direct USB communication support
- **Command-based control** - Simple text-based command protocol
- **Real-time telemetry** - Position, velocity, torque, and status reporting for all axes
- **Automatic homing** - Configurable homing routines for all axes
- **Software limits** - Configurable travel limits for safety
- **Error handling** - Comprehensive error reporting and recovery

---

## Building

### Requirements

- **Atmel Studio 7** (Windows) or compatible ARM GCC toolchain
- **Teknic ClearCore libraries** (included in `lib/` folder)
  - `libClearCore`
  - `LwIP` (Lightweight IP stack)

### Build Instructions

1. Open `gantry.atsln` in Atmel Studio
2. Ensure libraries are properly referenced:
   - `lib/libClearCore/ClearCore.cppproj`
   - `lib/LwIP/LwIP.cppproj`
3. Select build configuration (Debug or Release)
4. Build the solution (F7)

### Output Files

- `Debug/gantry.bin` - Binary firmware image
- `Debug/gantry.uf2` - UF2 format for bootloader flashing

## Flashing

### Via BR Equipment Control App (Recommended for Updates)

The easiest way to update firmware on an already-running device is through the [BR Equipment Control App](https://github.com/bluerobotics/br-equipment-control-app):

1. Open the Firmware Manager in the app
2. Select your device
3. Choose the firmware file or download the latest release
4. Click "Update Firmware" - the app handles the entire flashing process automatically

**Note:** Firmware flashing is only supported over USB connections. For initial flashing of a new device, use the bootloader method below.

### Via Bootloader (For Initial Flashing)

For initial flashing of a new device or when the app is not available:

1. Put the ClearCore into bootloader mode (hold button during power-on)
2. Copy `gantry.uf2` to the mounted bootloader drive
3. The device will automatically reboot with new firmware

### Via Atmel Studio

1. Connect ClearCore via USB
2. Select "Custom Programming Tool" in project settings
3. Build and program (F5)

---

## Communication Protocol

The firmware uses a simple text-based command protocol over UDP or USB serial:

- Commands: `move_x <position> mm`, `move_y <position> mm`, `move_z <position> mm`
- Status: `DONE: <command>`, `ERROR: <message>`, `INFO: <message>`
- Telemetry: Periodic status updates with position, velocity, torque

See the [BR Equipment Control App](https://github.com/bluerobotics/br-equipment-control-app) for full protocol documentation and command reference.

---

## Hardware Configuration

### Axes
- **X-axis**: Single motor (M0), 1219mm travel range
- **Y-axis**: Dual synchronized motors (M1, M2), 410mm travel range
- **Z-axis**: Single motor (M3) with brake control, -160mm to 0mm travel range

### Sensors
- Homing sensors: Digital inputs for each axis (IO0, IO1, IO3, IO4)
- Limit switches: Y-axis back limit (IO2)
- Z-axis brake: Digital output control (IO5)

## Configuration

Key parameters can be configured in `inc/config.h`:

- **Steps per mm**: Conversion factors for each axis
- **Travel limits**: Software limits for X, Y, Z axes
- **Homing parameters**: Velocities, accelerations, and torque limits
- **Network settings**: UDP port, packet sizes, telemetry interval

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Copyright (c) 2025 Blue Robotics

## Contributing

For issues, feature requests, or contributions, please open an issue or pull request on GitHub.

---

<div align="center">

⭐ **Star us on GitHub if you found this useful!**

Made with 💙 by the Blue Robotics team and contributors worldwide

---

<img src="assets/logo.png" alt="Blue Robotics" width="300">

**[bluerobotics.com](https://bluerobotics.com)** | Manufacturing Equipment Control

</div>
