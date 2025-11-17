# Changelog

All notable changes to the Gantry firmware will be documented in this file.

## [1.0.0] - 2025-11-17

### Added
- **Initial release**: Three-axis gantry control system firmware
- **X, Y, Z axis control**: Independent control of three linear axes with synchronized Y-axis dual motors
- **UDP/Ethernet communication**: Network-based control with device discovery
- **USB Serial support**: Direct USB communication fallback
- **Command-based control**: Simple text-based command protocol for axis movements
- **Real-time telemetry**: Position, velocity, torque, and status reporting for all axes
- **Homing routines**: Automatic homing with configurable velocities and torque limits
- **Software travel limits**: Configurable min/max position limits for all axes
- **Error handling**: Comprehensive error reporting and recovery mechanisms
- **Motor configuration**: Support for ClearPath motors with configurable steps/mm, velocity, and acceleration

### Features
- X-axis: Single motor control with 1219mm travel range
- Y-axis: Dual motor synchronized control with 410mm travel range
- Z-axis: Single motor control with brake control, -160mm to 0mm travel range
- Homing sensors: Digital input sensors for each axis
- Limit switches: Y-axis back limit switch protection
- Z-axis brake: Digital output control for Z-axis brake engagement

### Hardware Support
- Built on Teknic ClearCore platform
- ClearPath motor drivers (M0-M3 connectors)
- Digital I/O for sensors and limit switches
- Ethernet connectivity for network communication
- USB serial for direct communication

