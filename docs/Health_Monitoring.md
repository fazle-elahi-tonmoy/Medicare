# Health Monitoring System

## Introduction

In addition to medication management, Medicare continuously monitors vital health parameters to help caregivers track patient wellbeing and respond quickly to emergencies.

The system uses a dedicated pulse oximeter sensor to measure:

- Heart Rate (BPM)
- Blood Oxygen Saturation (SpO₂)

Measurements can be performed manually or automatically according to predefined schedules.

The collected information is displayed locally, uploaded to ESP RainMaker, and used to generate emergency alerts when necessary.

---

# System Overview

The health monitoring subsystem consists of:

- Pulse Oximeter Sensor
- OLED User Interface
- Reminder Scheduler
- ESP RainMaker Cloud Platform
- GSM Alert System
- Emergency Calling System

Workflow:

```text
Scheduled Checkup
        ↓
Patient Prompted
        ↓
Finger Detection
        ↓
Health Measurement
        ↓
Data Analysis
        ↓
Store / Alert
```

---

# Measured Parameters

## Heart Rate

Heart rate is measured in:

```text
BPM
(Beats Per Minute)
```

Example:

```text
72 BPM
```

---

## Blood Oxygen Saturation

Blood oxygen level is measured in:

```text
SpO₂ %
```

Example:

```text
98%
```

---

# Scheduled Health Monitoring

The system supports automated checkups.

Possible schedules include:

## Fixed Time Monitoring

Example:

```text
Every Day
08:00 AM
```

---

## Multiple Daily Checkups

Example:

```text
08:00 AM
02:00 PM
08:00 PM
```

---

## Weekly Monitoring

Example:

```text
Monday
Wednesday
Friday
```

---

## Interval Based Monitoring

Example:

```text
Every 6 Hours
Every 12 Hours
Every 24 Hours
```

---

# Health Checkup Workflow

When the scheduled time arrives:

```text
Checkup Time Reached
         ↓
Alarm Activated
         ↓
Display Message
         ↓
Wait For Finger
```

The patient is instructed to place a finger on the sensor.

---

# Patient Guidance System

The OLED display provides instructions.

Example:

```text
PLACE
FINGER
ON SENSOR
```

The buzzer assists by generating an audible alert.

This is particularly useful for elderly patients who may not constantly watch the display.

---

# Finger Detection

The sensor continuously checks for finger placement.

Possible states:

```text
Finger Detected
Finger Not Detected
```

---

# Successful Measurement

If a finger is detected:

```text
Finger Detected
        ↓
Measurement Starts
        ↓
Heart Rate Calculated
        ↓
SpO₂ Calculated
        ↓
Results Stored
```

The measurement is uploaded to ESP RainMaker.

---

# Patient Not Responding Event

If no finger is placed on the sensor:

```text
Checkup Requested
         ↓
No Finger Detected
         ↓
Timeout Reached
         ↓
Patient Not Responding
```

Alert escalation begins.

---

# Patient Not Responding Alerts

## Local Alert

```text
OLED Warning
Buzzer Alarm
```

---

## Cloud Notification

ESP RainMaker sends:

```text
Patient Not Responding
```

notification.

---

## SMS Alert

Example:

```text
Patient did not respond to scheduled health checkup.
```

---

# Heart Rate Monitoring

After successful finger placement:

```text
Finger Detected
        ↓
Pulse Signal Acquired
        ↓
Heart Rate Calculated
```

The measured value is displayed on the OLED screen.

Example:

```text
Heart Rate
72 BPM
```

---

# Blood Oxygen Monitoring

The pulse oximeter also calculates:

```text
SpO₂
```

which indicates oxygen saturation level.

Example:

```text
SpO₂
98%
```

---

# Health Status Evaluation

The system evaluates measurements against predefined safety thresholds.

Workflow:

```text
Measurement Complete
         ↓
Compare With Limits
         ↓
Normal / Critical
```

---

# Normal Health Event

If values remain within safe limits:

```text
Measurement Complete
         ↓
Data Stored
         ↓
Cloud Updated
```

No alerts are generated.

---

# Critical Health Event

If measurements fall below safe thresholds:

```text
Measurement Complete
         ↓
Critical Value Detected
         ↓
Emergency Alert
```

Examples:

- Low Heart Rate
- Low Blood Oxygen Level

---

# Emergency Alert Workflow

```text
Critical Reading
        ↓
Local Alarm
        ↓
RainMaker Notification
        ↓
SMS Alert
        ↓
Phone Call
```

This ensures caregivers receive immediate warning.

---

# ESP RainMaker Integration

Health data is synchronized with:

```text
ESP RainMaker
```

Available information:

- Heart Rate
- Blood Oxygen Level
- Measurement Status
- Last Checkup Time
- Patient Response Status

---

# Historical Monitoring

Repeated measurements allow caregivers to observe:

- Long-Term Trends
- Recovery Progress
- Health Deterioration
- Monitoring Compliance

---

# Benefits

## Early Detection

Abnormal conditions can be identified before they become severe.

---

## Remote Monitoring

Family members can track patient status remotely.

---

## Improved Compliance

Scheduled checkups encourage routine health monitoring.

---

## Emergency Response

Critical conditions generate immediate alerts.

---

# Future Improvements

Potential upgrades include:

- Blood Pressure Monitoring
- ECG Monitoring
- Body Temperature Monitoring
- Sleep Tracking
- Fall Detection
- Health Trend Analytics
- Doctor Dashboard Integration

---

# Educational Value

This subsystem demonstrates:

- Biomedical Sensors
- Pulse Oximetry
- IoT Healthcare
- Cloud Monitoring
- Alert Escalation Systems
- Human Interaction Verification
- Embedded Medical Devices

It transforms Medicare from a simple medicine reminder into a comprehensive patient health monitoring platform.