# Drawer Verification System

## Introduction

One of the most unique features of Medicare is its ability to verify whether the patient actually accessed the medicine drawer.

Most medicine reminder devices simply generate an alarm and assume the patient has taken the medicine. Medicare actively monitors drawer activity and escalates alerts when medication is missed.

This feature significantly improves medication compliance monitoring and caregiver awareness.

---

# System Overview

The drawer verification system consists of:

- Servo Controlled Drawer Lock
- Drawer Position Sensor
- Reminder Scheduler
- GSM Alert System
- ESP RainMaker Notification System

The workflow is:

Patient Reminder
        ↓
Drawer Unlocked
        ↓
Wait For Access
        ↓
Drawer Opened ?
      /      \
    Yes      No
     ↓        ↓
 Success   Alert

---

# Hardware Components

## Servo Motor

Each medicine drawer is secured using a servo motor.

Functions:

- Lock drawer
- Unlock drawer
- Prevent accidental access
- Restrict medicine access outside schedule

---

## Drawer Sensor

Each drawer contains a position detection sensor.

The sensor reports:

```text
OPEN
CLOSED
```

states to the ESP32.

---

# Reminder Trigger

When medication time arrives:

1. Alarm activates
2. OLED notification appears
3. Drawer unlocks
4. Verification timer starts

Workflow:

```text
Scheduled Time
      ↓
Alarm Starts
      ↓
Servo Unlocks Drawer
      ↓
Verification Timer Starts
```

---

# Verification Timer

The patient is given:

```text
60 Seconds
```

to access the drawer.

During this period the system continuously checks:

```text
Drawer Opened?
```

---

# Successful Medication Event

If the drawer is opened within the allowed time:

```text
Reminder Triggered
        ↓
Drawer Opened
        ↓
Medicine Access Confirmed
        ↓
Reminder Cleared
```

The system records a successful medication event.

No notifications are sent.

---

# Missed Medication Event

If the drawer remains closed:

```text
Reminder Triggered
        ↓
60 Seconds Expired
        ↓
Drawer Not Opened
        ↓
Medication Missed
```

Alert escalation begins.

---

# Alert Escalation

## Level 1

Local Device Alert

- OLED Warning
- Buzzer Alarm

---

## Level 2

ESP RainMaker Notification

Example:

```text
Patient did not take scheduled medication.
```

---

## Level 3

SMS Notification

Example:

```text
Patient did not open medicine drawer after reminder.
```

The caregiver receives immediate notification.

---

# Why This Matters

Medication reminders alone cannot verify compliance.

Example:

```text
Alarm Rings
      ↓
Patient Ignores Alarm
      ↓
Medicine Not Taken
```

Traditional systems cannot detect this.

Medicare solves this problem by monitoring actual drawer interaction.

---

# Caregiver Benefits

Caregivers can quickly determine:

- Medicine Taken
- Medicine Missed
- Patient Response Status

without physically being present.

---

# Integration With Cloud Platform

Drawer status is synchronized with:

```text
ESP RainMaker
```

allowing remote monitoring through the mobile application.

Possible states:

```text
Drawer Locked
Drawer Unlocked
Drawer Opened
Drawer Missed
```

---

# Future Improvements

Potential upgrades include:

- RFID Medicine Verification
- Weight-Based Pill Detection
- Camera Verification
- Voice Confirmation
- Automatic Compliance Reports

---

# Educational Value

This subsystem demonstrates:

- Servo Motor Control
- Sensor Integration
- Human Interaction Verification
- IoT Notifications
- Healthcare Automation
- Embedded State Machines

It represents one of the key innovations of the Medicare platform by transforming a simple reminder into a verifiable medication compliance system.