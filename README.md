# Unmanned Rocket

An embedded systems and aerospace project focused on designing, building, and launching an unmanned model rocket with onboard atmospheric data logging, pre-flight sensor validation, and post-flight trajectory reconstruction.

## Overview

**Unmanned Rocket** combines embedded software, sensor integration, mechanical design, and post-flight data analysis into a single flight-ready system. The rocket carried a custom **ESP32-S2-based payload module** designed to capture atmospheric and motion data during flight, store it locally, and support post-flight reconstruction of the rocket’s flight path.

A custom **3D-printed payload protection system** was designed and installed inside the rocket to secure the electronics, protect the microcontroller during launch and landing forces, and maintain reliable sensor operation throughout flight.

## Key Features

- Custom embedded payload module built around an **ESP32-S2 microcontroller**
- Firmware written in **C++**
- Onboard **SD card data logging** for post-flight analysis
- Atmospheric and motion data tracking, including:
  - Temperature
  - Humidity
  - Gyroscope data
  - Additional sensor telemetry
- Onboard screen for **pre-flight component checks**
- Custom **3D-printed internal protection structure** for the electronics payload
- Post-flight software analysis used to recreate the rocket’s flight path

## System Architecture

```text
Rocket Airframe
│
├── 3D-Printed Payload Protection Housing
│   │
│   ├── ESP32-S2 Microcontroller
│   │
│   ├── Sensor Suite
│   │   ├── Temperature Sensor
│   │   ├── Humidity Sensor
│   │   ├── Gyroscope / IMU
│   │   └── Additional Flight Telemetry Sensors
│   │
│   ├── SD Card Module
│   │   └── Stores flight telemetry data
│   │
│   └── Display Module
│       └── Runs pre-flight component checks
│
└── Post-Flight Analysis Software
    └── Reconstructs flight path from recorded telemetry
```

## Embedded Software

The microcontroller firmware was written in **C++** and designed to run reliably in a constrained embedded environment. The software handled sensor initialization, pre-flight diagnostics, real-time data collection, local file storage, and telemetry formatting for later analysis.

Core firmware responsibilities included:

- Initializing and validating all connected sensors
- Running pre-flight component checks through the onboard display
- Sampling atmospheric and motion data during flight
- Writing structured telemetry data to an SD card
- Preserving flight data for post-launch analysis
- Supporting reconstruction of the rocket’s trajectory after recovery

## Pre-Flight Sensor Validation

Before launch, the onboard display was used to run component checks and confirm that each sensor was connected and responding correctly.

This helped reduce the risk of launching with a disconnected, misconfigured, or nonresponsive sensor. The pre-flight check system made the payload easier to debug in the field and improved confidence that the data collected during launch would be valid.

Example validation flow:

```text
Power On
│
├── Initialize ESP32-S2
├── Mount SD Card
├── Check Temperature Sensor
├── Check Humidity Sensor
├── Check Gyroscope / IMU
├── Display Sensor Status
│
└── Ready for Launch
```

## Data Logging

Flight telemetry was written to an onboard SD card so the rocket could operate independently without relying on a live wireless connection during launch.

The logged data was used after recovery to analyze flight behavior and recreate the rocket’s flight path in software.

Example telemetry fields:

```csv
timestamp_ms,temperature_c,humidity_percent,gyro_x,gyro_y,gyro_z
0,23.4,41.2,0.01,-0.02,0.04
50,23.4,41.3,0.03,-0.01,0.08
100,23.5,41.1,0.05,0.00,0.12
```

## Mechanical Design

A custom **3D-printed payload protection system** was designed to fit inside the rocket body and shield the electronics during flight.

The design goals were:

- Secure the ESP32-S2 and sensor modules inside the rocket
- Protect the payload from vibration, acceleration, and landing impact
- Maintain access to wiring, SD card storage, and display connections
- Fit within the rocket’s internal space constraints
- Keep the payload organized and serviceable for testing and iteration

This mechanical design was critical because the embedded system had to survive a real launch environment, not just function on a bench.

## Post-Flight Analysis

After launch and recovery, the telemetry stored on the SD card was imported into analysis software. The recorded atmospheric and gyroscope data was used to reconstruct the rocket’s flight path and evaluate system performance.

Post-flight analysis enabled:

- Visualization of the rocket’s flight behavior
- Review of sensor readings over time
- Validation of payload performance during launch
- Debugging of hardware or firmware issues
- Iteration on future rocket and payload designs

## Technical Skills Demonstrated

This project demonstrates practical experience across embedded systems, hardware integration, and applied engineering.

### Embedded Systems

- ESP32-S2 firmware development
- C++ programming for microcontrollers
- Sensor initialization and polling
- SD card file I/O
- Display-driven diagnostics
- Real-time telemetry collection

### Hardware Integration

- Microcontroller-based payload design
- Sensor suite integration
- Field-ready electronics packaging
- Pre-flight hardware validation
- Embedded debugging and testing

### Mechanical Design

- Custom 3D-printed payload protection
- Electronics enclosure design
- Rocket payload mounting
- Design for vibration and impact protection
- Space-constrained hardware packaging

### Data Analysis

- Flight telemetry collection
- Sensor data formatting
- Post-flight data processing
- Trajectory reconstruction
- Performance review from real-world launch data

## Project Motivation

The goal of this project was to build more than a basic rocket launch system. The focus was on creating a complete embedded payload pipeline: design the physical module, write the firmware, validate the sensors, collect real launch data, and use that data after recovery to understand the rocket’s flight.

This project required the system to work outside of a controlled lab environment, where reliability, packaging, diagnostics, and data integrity mattered.

## Why This Project Matters

**Unmanned Rocket** highlights the kind of end-to-end engineering required in embedded systems roles:

- Building firmware that interfaces with real hardware
- Designing for reliability before deployment
- Debugging across software, electronics, and mechanical constraints
- Collecting and preserving field data
- Turning raw sensor readings into useful analysis

The project reflects practical embedded software engineering experience, especially in sensor-driven systems where hardware, firmware, and data analysis must work together successfully.

## Technologies Used

- **C++**
- **ESP32-S2**
- **SD card module**
- **Temperature and humidity sensors**
- **Gyroscope / IMU**
- **Onboard display**
- **3D printing**
- **Post-flight data analysis software**

## Future Improvements

Potential future improvements include:

- Adding barometric pressure sensing for altitude estimation
- Improving trajectory reconstruction with accelerometer fusion
- Adding wireless telemetry for live ground-station monitoring
- Implementing timestamp synchronization across all sensor readings
- Designing a more modular payload bay for faster testing
- Adding automated anomaly detection to post-flight analysis software

## Repository Structure

```text
unmanned-rocket/
│
├── firmware/
│   ├── src/
│   ├── include/
│   └── README.md
│
├── hardware/
│   ├── wiring-diagrams/
│   └── components.md
│
├── mechanical/
│   ├── 3d-models/
│   └── payload-housing/
│
├── data/
│   └── sample-flight-logs/
│
├── analysis/
│   └── flight-path-reconstruction/
│
└── README.md
```

## Status

Project completed as a working unmanned rocket payload system with embedded data collection, onboard diagnostics, custom 3D-printed protection, and post-flight analysis.
