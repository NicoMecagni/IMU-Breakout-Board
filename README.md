# IMU-Breakout-Board
IMU breakout board for the MPU-6050 6-axis accelerometer/gyroscope, designed in Altium Designer with LTspice power supply simulation reference.

# IMU Breakout Board — MPU-6050

A custom PCB breakout board for the MPU-6050 6-axis Inertial Measurement Unit (IMU), 
designed from scratch in Altium Designer.

## Overview
The MPU-6050 combines a 3-axis accelerometer and 3-axis gyroscope in a compact QFN-24 
package, used in aerospace, robotics, and motion-sensing applications. This board breaks 
out the I2C interface for easy integration with a microcontroller.

## Features
- 5V input regulated to 3.3V via AMS1117-3.3 linear voltage regulator
- Decoupling capacitors on all power pins per MPU-6050 datasheet recommendations
- I2C pull-up resistors (4.7kΩ) on SCL and SDA lines
- JST GH series connectors for power input and I2C output
- Ground plane on both top and bottom copper layers

## Tools Used
- Altium Designer — schematic capture and PCB layout
- LTspice — power supply circuit reference and simulation
- MPU-6050 and AMS1117-3.3 datasheets for design specifications

## Design Files
- `IMU_Breakout_Schematic.SchDoc` — full schematic
- `IMU_Breakout_Board.PcbDoc` — PCB layout
- `Project Outputs/` — Gerber and NC drill files (fabrication-ready)

## Known Issues (Rev 1)
- One GND pad (C4-2) shows a DRC unrouted net flag due to routing constraints — 
electrically connected through ground plane but flagged by Altium's DRC. 
To be resolved in Rev 2 by rerouting adjacent +3.3V traces.
