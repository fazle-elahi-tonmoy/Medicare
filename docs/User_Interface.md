# User Interface System

## Introduction

Medicare was designed to be usable by elderly patients without requiring constant access to a smartphone application.

To achieve this, the device includes a complete onboard graphical user interface (GUI) displayed on an OLED screen and controlled using physical buttons.

The interface provides:

- Device Setup
- WiFi Configuration
- Medicine Management
- Health Monitoring
- Status Information
- System Settings

This allows the device to operate independently while still supporting cloud connectivity through ESP RainMaker.

---

# Design Philosophy

The user interface was designed around three key goals:

## Simplicity

The interface should remain easy to understand for elderly users.

---

## Accessibility

Important functions should be available directly from the device.

---

## Independence

The device should remain usable even if:

- Internet is unavailable
- Smartphone is unavailable
- Cloud services are unavailable

---

# Hardware Components

The user interface consists of:

| Component | Purpose |
|------------|----------|
| OLED Display | Visual Feedback |
| Push Buttons | Navigation |
| Buzzer | Audio Feedback |
| ESP32 | Interface Controller |

---

# System Architecture

```text
User
  ↓
Buttons
  ↓
Menu System
  ↓
OLED Display
  ↓
System Functions
```

The interface acts as the central access point for all device features.

---

# Main Menu Structure

The interface is organized into multiple screens.

```text
Main Menu
│
├── Medicine System
├── Health Monitoring
├── WiFi Setup
├── Device Setup
├── Status Information
└── Settings
```

---

# Startup Screen

When the device powers on:

```text
MEDICARE
SMART HEALTHCARE
SYSTEM
```

is displayed.

The system then loads:

- EEPROM Configuration
- WiFi Settings
- User Preferences

before entering normal operation.

---

# WiFi Setup Interface

The device supports onboard WiFi provisioning.

Workflow:

```text
WiFi Setup
      ↓
Scan Networks
      ↓
Select Network
      ↓
Enter Password
      ↓
Connect
```

---

## Benefits

Allows users to configure:

```text
SSID
Password
```

without modifying firmware.

---

# Device Setup Interface

The setup menu provides access to:

```text
Device Configuration
```

including:

- Phone Number Setup
- Notification Settings
- Reminder Settings
- Monitoring Settings

---

# Medicine Management Screen

This screen displays:

```text
Drawer 1 Status
Drawer 2 Status
Drawer 3 Status
```

Possible states:

```text
Locked
Unlocked
Opened
Reminder Active
```

---

# Manual Drawer Control

The patient can manually open a drawer using the onboard button controls.

Workflow:

```text
Button Press
      ↓
Select Drawer
      ↓
Unlock Drawer
```

This feature is useful when medication needs to be accessed outside scheduled reminder times.

---

# Reminder Status Screen

Displays information about upcoming reminders.

Example:

```text
NEXT MEDICINE

08:00 PM

DRAWER 2
```

This helps patients anticipate upcoming medication schedules.

---

# Health Monitoring Screen

The health monitoring page displays:

```text
Heart Rate
SpO₂
Temperature
```

in real time.

Example:

```text
HR : 72 BPM

SpO₂ : 98%

TEMP : 29°C
```

---

# Health Checkup Interface

During scheduled checkups:

```text
PLACE FINGER
ON SENSOR
```

is displayed.

The system remains in monitoring mode until:

```text
Finger Detected
```

or

```text
Timeout Reached
```

---

# Patient Response Screen

Possible system states:

## Waiting

```text
WAITING FOR
PATIENT
```

---

## Measuring

```text
MEASURING
PLEASE WAIT
```

---

## Success

```text
MEASUREMENT
COMPLETE
```

---

## Failed

```text
PATIENT NOT
RESPONDING
```

---

# Notification Status Screen

Displays recent alerts.

Examples:

```text
Medicine Missed

Patient Not Responding

Low Oxygen Level

Low Heart Rate
```

This allows caregivers and patients to review recent events directly on the device.

---

# Emergency Alert Screen

When a critical condition occurs:

```text
EMERGENCY

CAREGIVER
NOTIFIED
```

is displayed.

The buzzer may also remain active depending on system settings.

---

# Cloud Status Screen

Displays ESP RainMaker connectivity.

Possible states:

## Connected

```text
RAINMAKER
CONNECTED
```

---

## Connecting

```text
CONNECTING
TO CLOUD
```

---

## Offline

```text
OFFLINE MODE
```

The device continues operating locally even if internet connectivity is unavailable.

---

# Button Navigation System

Navigation is performed using onboard buttons.

Possible actions:

| Action | Function |
|----------|----------|
| Short Press | Next Item |
| Long Press | Select |
| Double Press | Back |
| Hold | Exit Menu |

---

# Audio Feedback

The buzzer provides feedback during:

- Menu Navigation
- Reminder Activation
- Health Checkups
- Emergency Events

This improves accessibility for elderly users.

---

# Error Messages

The interface can display system warnings.

Examples:

## No WiFi

```text
WIFI
DISCONNECTED
```

---

## Sensor Error

```text
SENSOR
NOT FOUND
```

---

## GSM Failure

```text
GSM MODULE
ERROR
```

---

# Human-Centered Design

Special consideration was given to elderly users.

Features include:

- Large Text
- Simple Menus
- Audio Guidance
- Minimal Navigation Steps
- High Contrast Display

---

# Benefits

## Improved Accessibility

Patients can interact directly with the device.

---

## Reduced Dependence

The device remains usable without a smartphone.

---

## Better User Experience

Clear feedback improves confidence and usability.

---

## Easier Troubleshooting

System status can be viewed directly from the device.

---

# Future Improvements

Potential upgrades include:

- Touchscreen Interface
- Voice Guidance
- Multi-Language Support
- Animated Icons
- Large Font Accessibility Mode
- Voice Commands
- Caregiver Login System

---

# Educational Value

This subsystem demonstrates:

- Embedded GUI Design
- OLED Display Programming
- Human-Machine Interfaces
- Accessibility Design
- Healthcare Product Development
- User Experience Engineering

The Medicare user interface transforms a complex healthcare monitoring platform into a device that can be comfortably used by elderly patients with minimal technical knowledge.