# Medication Reminder System

## Introduction

One of the primary goals of Medicare is ensuring medication compliance among elderly patients.

Traditional reminder systems only generate an alarm and assume that the patient has taken the medicine. Medicare goes further by actively verifying patient interaction with the medicine drawer and escalating alerts if medication is missed.

This significantly improves caregiver awareness and patient safety.

---

# System Overview

The medicine reminder system consists of:

* Real Time Scheduling
* Servo Controlled Drawers
* Drawer Access Sensors
* OLED Notifications
* Audible Alarms
* GSM Alerts
* Cloud Notifications

The complete workflow is:

```text
Scheduled Medicine Time
          ↓
Alarm Activated
          ↓
Drawer Unlocked
          ↓
Patient Response Verification
          ↓
Success / Alert Escalation
```

---

# Medicine Drawers

The device contains:

```text
Drawer 1
Drawer 2
Drawer 3
```

Each drawer can be assigned to a different medication schedule.

Examples:

| Drawer   | Purpose              |
| -------- | -------------------- |
| Drawer 1 | Morning Medication   |
| Drawer 2 | Afternoon Medication |
| Drawer 3 | Night Medication     |

---

# Scheduled Reminder Process

When a medication schedule is reached:

```text
Current Time
       =
Scheduled Time
```

the device begins the reminder sequence.

---

## Reminder Sequence

### Step 1

Activate buzzer.

### Step 2

Display reminder message.

### Step 3

Unlock corresponding drawer.

### Step 4

Wait for drawer interaction.

---

# Drawer Unlocking

The assigned servo rotates and releases the drawer lock.

```text
Reminder Triggered
        ↓
Servo Unlock
        ↓
Drawer Accessible
```

The patient can now retrieve medication.

---

# Patient Verification

Unlike conventional pill dispensers, Medicare verifies whether the drawer was actually opened.

The drawer sensor continuously monitors:

```text
OPEN
CLOSED
```

states.

---

# One Minute Response Window

After the reminder begins:

```text
Timer Starts
      ↓
60 Seconds
```

The patient is expected to access the drawer.

---

# Successful Medication Event

If the drawer is opened:

```text
Drawer Opened
      ↓
Medication Confirmed
      ↓
Reminder Cleared
```

No further action is required.

---

# Missed Medication Event

If the drawer remains closed:

```text
Reminder Triggered
       ↓
60 Seconds
       ↓
No Drawer Activity
       ↓
Medication Missed
```

Alert escalation begins.

---

# Alert Escalation

The system automatically generates:

### Local Alert

```text
OLED Message
Buzzer Warning
```

---

### Cloud Alert

```text
ESP RainMaker Notification
```

---

### GSM Alert

```text
SMS Sent
```

Example:

```text
Patient did not take scheduled medication.
```

---

# Benefits

## Improved Compliance

Medication intake becomes verifiable.

---

## Caregiver Awareness

Family members receive immediate feedback.

---

## Reduced Risk

Missed medication events are detected early.

---

# Educational Value

This subsystem demonstrates:

* Scheduled Automation
* Servo Control
* Human Interaction Verification
* IoT Notifications
* Embedded State Machines
* Healthcare Technology

---
