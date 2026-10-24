# IMU Breakout Board — MPU-6050

A custom PCB breakout board for the MPU-6050 6-axis Inertial Measurement Unit (IMU), designed from scratch in Altium Designer.

## Overview
The MPU-6050 combines a 3-axis accelerometer and 3-axis gyroscope in a compact QFN-24 package, used in aerospace, robotics, and motion-sensing applications. This board breaks out the I2C interface for easy integration with a microcontroller.

## Features
- 5V input regulated to 3.3V via AMS1117-3.3 linear voltage regulator
- Decoupling capacitors on all power pins per MPU-6050 datasheet recommendations
- I2C pull-up resistors (4.7kΩ) on SCL and SDA lines
- JST GH series connectors for power input and I2C output
- GND pours on top and bottom copper layers, tied together with vias

## Rev 2 Changes
- **Custom MPU-6050 symbol and footprint** (`MPU6050.SchLib`, `MPU6050.PcbLib`): IPC-7351 QFN-24 land pattern generated from the datasheet package dimensions (Sec. 11.2) and cross-checked against the manufacturer's recommended PCB land pattern (Sec. 11.3).
- **Followed datasheet assembly guidance (Sec. 11.4):**
  - Exposed die pad removed from the footprint; the datasheet specifies it should not be soldered and has no electrical connection.
  - No traces or vias routed under the sensor.
- **Reserved pins (19, 21, 22) left unconnected** per the pin description table (Sec. 7.1); Rev 1 had tied them to GND.
- **Fixed floating bottom ground plane** by adding GND stitching vias.
- **DRC:** zero electrical violations (clearance, short-circuit, un-routed, net antennae). Solder mask and silkscreen rules set to JLCPCB capabilities; remaining items are minor library-footprint silkscreen offsets (0.125–0.145 mm vs. 0.15 mm rule).

## Tools Used
- Altium Designer — schematic capture, PCB layout, footprint/symbol creation
- LTspice — power supply circuit reference and simulation
- MPU-6050 and AMS1117-3.3 datasheets for design specifications

## Design Files
- `IMU_Breakout_Schematic.SchDoc` — full schematic
- `IMU_Breakout_Board.PcbDoc` — PCB layout
- `MPU6050.SchLib` / `MPU6050.PcbLib` — custom symbol and footprint
- `Project Outputs for IMU_Breakout_Board/` — Gerber and NC drill files
