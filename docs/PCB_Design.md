# PCB Design and Hardware Architecture

## Introduction

To ensure reliability, compactness, and ease of deployment, Medicare was designed around a custom PCB integrating all major system components.

The PCB serves as the central hub connecting:

- ESP32 Controller
- GSM Communication Module
- Health Monitoring Sensors
- OLED Display
- Servo Controlled Medicine Drawers
- User Input Buttons
- Alarm System
- Power Management Circuitry

This integrated approach reduces wiring complexity and improves system stability compared to breadboard-based prototypes.

---

# PCB Overview

![PCB Design](../images/PCB_view.jpg)

The PCB was designed to accommodate all major subsystems required for healthcare monitoring and medication management.

Primary objectives:

- Compact Design
- Reliable Operation
- Easy Assembly
- Reduced Wiring
- Simplified Maintenance
- Educational Demonstration

---

# Hardware Architecture

The complete system architecture can be represented as:

```text
                ESP32
                   │
 ┌─────────────────┼─────────────────┐
 │                 │                 │
 ▼                 ▼                 ▼

OLED          GSM Module      EEPROM Storage

 │                 │
 │                 ▼
 │          SMS & Phone Calls
 │
 ▼

User Interface

 ┌─────────────────┼─────────────────┐
 │                 │                 │

 ▼                 ▼                 ▼

MAX3010x      Servo Motors      Drawer Sensors

 │                 │                 │

 ▼                 ▼                 ▼

Health Data    Drawer Locking   Drawer Verification

                   │
                   ▼

             Medication System
```

---

# ESP32 Controller

The ESP32 serves as the primary controller.

Responsibilities:

- User Interface Management
- ESP RainMaker Connectivity
- Sensor Processing
- GSM Communication
- Servo Control
- Scheduling Engine
- EEPROM Management
- Alert Processing

The ESP32 was selected because it provides:

- WiFi Connectivity
- Bluetooth Capability
- Adequate Processing Power
- Large Memory Capacity
- Excellent IoT Support

---

# OLED Interface Section

The OLED display provides local interaction.

Functions:

- Device Setup
- WiFi Setup
- Health Monitoring
- Reminder Status
- Drawer Status
- Error Messages
- Alert Notifications

Benefits:

- Smartphone Independent Operation
- Simple Navigation
- Elderly Friendly Interface

---

# Health Monitoring Section

The PCB includes support for the pulse oximeter sensor.

Measured Parameters:

- Heart Rate
- Blood Oxygen Saturation (SpO₂)

Workflow:

```text
Finger Placement
        ↓
Pulse Detection
        ↓
Signal Processing
        ↓
Health Evaluation
```

The sensor communicates directly with the ESP32 using I²C.

---

# GSM Communication Section

The GSM module provides:

- SMS Notifications
- Emergency Phone Calls
- Remote Alert Delivery

Functions:

```text
Medication Missed
        ↓
SMS Sent

Patient Not Responding
        ↓
SMS Sent

Critical Health Event
        ↓
SMS Sent
        ↓
Phone Call
```

The GSM subsystem operates independently of cloud connectivity.

---

# Servo Driver Section

Three servo motors control the medicine drawers.

Each servo is responsible for:

```text
Drawer 1 Lock
Drawer 2 Lock
Drawer 3 Lock
```

Functions:

- Lock Drawer
- Unlock Drawer
- Controlled Access

The servos are controlled directly by the ESP32.

---

# Drawer Verification Section

Each drawer contains a position sensor.

Possible states:

```text
OPEN
CLOSED
```

The sensors allow Medicare to verify actual patient interaction.

Workflow:

```text
Reminder Triggered
       ↓
Drawer Unlocked
       ↓
Drawer Opened ?
       ↓
Success / Alert
```

This feature significantly improves medication compliance tracking.

---

# User Input Section

The PCB contains buttons used for:

- Menu Navigation
- Device Setup
- Manual Drawer Access
- System Configuration

Possible actions:

```text
Short Press
Long Press
Double Press
```

depending on the selected function.

---

# Alarm System

A buzzer is used for:

- Medicine Reminders
- Health Checkup Requests
- Error Notifications
- Emergency Alerts

Benefits:

- Audible Feedback
- Elderly Friendly Operation
- Immediate Attention

---

# EEPROM Storage

Configuration data is stored permanently.

Examples:

```text
Emergency Phone Number
Reminder Settings
Monitoring Settings
```

Benefits:

- Retains Settings After Restart
- Simplifies Setup
- Improves Reliability

---

# Power Distribution

The PCB distributes power to:

```text
ESP32
OLED Display
Pulse Oximeter
Servo Motors
GSM Module
Drawer Sensors
Buzzer
```

Special attention should be given to:

- Servo Current Requirements
- GSM Transmission Current Spikes
- Stable 5V Supply
- ESP32 Voltage Regulation

---

# Power Supply Considerations

The GSM module and servo motors can consume significant current.

Recommended power source:

```text
5V Regulated Supply

Minimum:
2A

Recommended:
3A+
```

This ensures stable operation during:

- SMS Transmission
- Phone Calls
- Servo Movement

---

# Communication Interfaces

## I²C Bus

Used for:

```text
OLED Display
MAX3010x Sensor
```

Benefits:

- Reduced Wiring
- Multiple Devices
- Simple Expansion

---

## UART Communication

Used for:

```text
ESP32 ↔ GSM Module
```

Functions:

- SMS Commands
- Phone Calls
- Network Status

---

# PCB Design Goals

The board was designed with several objectives:

## Reliability

Minimize wiring failures.

---

## Modularity

Allow easy subsystem upgrades.

---

## Compactness

Reduce enclosure size.

---

## Maintainability

Simplify troubleshooting.

---

## Educational Value

Clearly demonstrate:

- Healthcare Electronics
- IoT Integration
- Embedded Design

---

# Manufacturing Considerations

When producing the PCB:

Verify:

- Power Traces
- Servo Current Paths
- GSM Power Routing
- Ground Plane Integrity
- Decoupling Capacitors

before deployment.

---

# Future Hardware Improvements

Potential upgrades include:

- Battery Backup
- Charging Circuit
- Blood Pressure Sensor
- ECG Module
- Speaker System
- Touch Interface
- GPS Module
- Camera Integration

---

# Educational Value

This PCB demonstrates the integration of:

- Embedded Systems
- Healthcare Electronics
- IoT Devices
- GSM Communication
- Sensor Networks
- Human-Machine Interfaces

into a single practical healthcare platform.

The hardware architecture showcases how multiple subsystems can work together to create a reliable, connected, and patient-focused monitoring solution.