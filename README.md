# InkTime-SmartWatch

## Project Overview

InkTime-SmartWatch is a compact wearable embedded system built around the Nordic nRF52840 microcontroller, designed for ultra-low-power smartwatch applications using an e-paper display, motion sensing, haptic feedback, battery monitoring and USB-C charging.

The project integrates power management, sensing, display driving and wireless communication into a compact PCB optimized for enclosure integration.

---

# Block Diagram

```text
USB-C Input
   ↓
LiPo Charger
   ↓
LiPo Battery
   ↓
DC/DC Converter
   ↓
nRF52840 MCU
 ├── E-Paper Display (SPI)
 ├── IMU Sensor (I2C)
 ├── Fuel Gauge (I2C)
 ├── Haptic Driver (I2C / GPIO)
 ├── Buttons (GPIO Interrupts)
 ├── SWD Debug Interface
 └── BLE Antenna
```

---

# Bill of Materials (BOM)

| Component         | Part             | Function                       |
| ----------------- | ---------------- | ------------------------------ |
| MCU               | nRF52840-QFAA    | Main microcontroller           |
| Battery Charger   | BQ25180          | LiPo charging                  |
| DC/DC Converter   | RT6150           | Voltage regulation             |
| IMU               | Motion sensor    | Accelerometer / motion sensing |
| Fuel Gauge        | MAX17048         | Battery level measurement      |
| Haptic Driver     | DRV2605          | Vibration motor control        |
| Display Connector | 24-pin FPC       | E-paper connection             |
| USB-C Connector   | Type-C           | Charging and power             |
| ESD Protection    | USBLC6           | USB protection                 |
| Buttons           | Tactile switches | User input                     |
| SWD Header        | TC2030           | Programming/debug              |

---

# Hardware Functional Description

## Microcontroller Core

The central processing unit of the smartwatch is the Nordic nRF52840, a BLE-enabled ARM Cortex-M4 microcontroller selected for:

* low power consumption
* integrated Bluetooth Low Energy
* SPI / I2C / GPIO flexibility
* wearable device suitability

The MCU handles:

* display updates
* sensor acquisition
* battery monitoring
* haptic events
* user input

---

## Power Management

The power subsystem contains:

### LiPo Charger

BQ25180 charger manages battery charging through USB-C input.

Functions:

* battery charging
* input protection
* charging regulation

### DC/DC Converter

RT6150 converts battery voltage to regulated supply rails for MCU and peripherals.

Main outputs:

* 3.3V logic supply
* regulated peripheral rail

---

## Display Subsystem

The smartwatch uses an e-paper display interface.

Advantages:

* ultra low power
* persistent image retention
* sunlight readability

Dedicated E-Paper Driver section generates required voltages.

---

## IMU Sensor

The inertial measurement unit provides motion data:

* acceleration
* movement detection
* orientation sensing

Used for:

* wake-up events
* motion-based interface control

---

## Fuel Gauge

MAX17048 continuously measures battery charge state.

Functions:

* battery voltage monitoring
* charge estimation
* low battery alert

---

## Haptic Feedback

DRV2605 driver controls the vibration motor.

Allows:

* notifications
* tactile feedback
* programmable vibration patterns

---

## USB-C Interface

USB-C connector provides:

* charging input
* power delivery
* ESD protected connection

Protection implemented using USBLC6 device.

---

## Buttons

Three hardware buttons are implemented:

* SW_UP
* SW_INT
* SW_DN

Used for:

* navigation
* selection
* wake-up interrupt

---

# nRF52840 Pin Assignment

| nRF52840 Pin | Connected Module | Interface | Purpose       |
| ------------ | ---------------- | --------- | ------------- |
| P0.13        | Display Clock    | SPI       | Display clock |
| P0.15        | Display Data     | SPI       | Display data  |
| P0.24        | Haptic control   | GPIO      | Motor trigger |
| P0.26        | IMU SDA          | I2C       | Sensor data   |
| P0.27        | IMU SCL          | I2C       | Sensor clock  |
| P1.xx        | Buttons          | GPIO      | User input    |
| SWDIO        | Debug            | SWD       | Programming   |
| SWDCLK       | Debug            | SWD       | Programming   |

---

# Power Consumption Considerations

Estimated current consumption:

* MCU active: ~5 mA
* E-paper refresh: ~20 mA
* IMU active: ~1 mA
* Haptic pulse: ~80 mA

Battery sizing selected for wearable operation with optimized duty cycle.

---

# Mechanical Integration

The mechanical assembly contains:

* PCB
* LiPo battery
* e-paper display
* vibration motor
* enclosure

Placement order:

top to bottom:

Display → Battery → PCB → Case

---

# Design Decisions

Main design goals:

* compact PCB layout
* low power architecture
* short SPI lines to display
* antenna edge placement
* battery direct pad connection

---

# Rendered Images

Project folder contains:

* PCB 3D top render
* PCB 3D side render
* complete assembly top render
* complete assembly side render
* exploded mechanical view

---

# Files Included

## Hardware

* schematic (.sch)
* board (.brd)
* schematic PDF

## Manufacturing

* gerbers.zip
* BOM
* CPL

## Mechanical

* STEP exploded assembly
* STEP PCB 3D
* Fusion360 project

## Images

* PCB renders
* assembly renders

---
