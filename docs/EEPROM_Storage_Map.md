# EEPROM Storage Map

## Introduction

One of the key features of Medicare is its ability to retain important settings even after power loss or system restart.

To achieve this, configuration data is stored inside the ESP32's EEPROM memory.

This allows the device to remember:

- Emergency Contact Numbers
- Notification Settings
- Medicine Schedules
- Health Monitoring Configuration
- User Preferences

without requiring the user to reconfigure the device after every restart.

---

# Why EEPROM?

EEPROM provides:

```text
Non-Volatile Storage
```

meaning data remains stored even when power is removed.

Unlike RAM:

```text
Power OFF
      ↓
Data Preserved
```

This makes EEPROM ideal for healthcare devices that must maintain critical settings.

---

# Stored Parameters

The Medicare system stores several categories of information.

## Caregiver Information

Used for:

- SMS Alerts
- Emergency Phone Calls
- Notification Delivery

Example:

```text
+8801XXXXXXXXX
```

---

## Device Configuration

Includes:

- Reminder Settings
- Monitoring Settings
- Notification Preferences

---

## User Preferences

Includes:

- Alarm Configuration
- Display Preferences
- Operating Modes

---

# Storage Architecture

The EEPROM is logically divided into sections.

```text
EEPROM
│
├── Phone Number
├── Medicine Settings
├── Monitoring Settings
├── Notification Settings
└── Reserved Space
```

This organization makes future upgrades easier.

---

# Emergency Contact Storage

The caregiver phone number is permanently stored.

Workflow:

```text
User Updates Number
         ↓
RainMaker App
         ↓
ESP32 Receives Data
         ↓
EEPROM Updated
```

After restart:

```text
Power Loss
      ↓
Restart
      ↓
Phone Number Restored
```

No reconfiguration is required.

---

# Medicine Reminder Configuration

The device stores:

```text
Reminder Enabled
Reminder Disabled
```

states.

Possible future expansion:

```text
Medicine Name
Dose Information
Reminder Frequency
```

---

# Health Monitoring Configuration

Stored information may include:

```text
Monitoring Enabled
Monitoring Disabled
```

and scheduling preferences.

Examples:

```text
Every 6 Hours
Every 12 Hours
Every Day
Every Week
```

---

# Notification Settings

Configuration options include:

```text
SMS Enabled
SMS Disabled
```

and

```text
Phone Call Enabled
Phone Call Disabled
```

allowing caregivers to customize alert behavior.

---

# Data Update Process

Whenever a setting changes:

```text
User Modifies Setting
         ↓
Validation
         ↓
EEPROM Write
         ↓
Confirmation
```

The new value immediately becomes persistent.

---

# Startup Recovery Process

When the device powers on:

```text
System Startup
       ↓
Read EEPROM
       ↓
Load Settings
       ↓
Initialize Services
```

This ensures all previous settings are restored automatically.

---

# Benefits of EEPROM Storage

## Persistent Configuration

No need to re-enter settings after power loss.

---

## Improved Reliability

Critical contact information is always available.

---

## User Convenience

Configuration only needs to be performed once.

---

## Offline Capability

Settings remain available even without internet access.

---

# Data Integrity Considerations

Healthcare devices rely on accurate configuration.

Therefore:

```text
Write Only When Necessary
```

helps reduce EEPROM wear.

---

# EEPROM Lifetime

Typical EEPROM endurance:

```text
100,000+
Write Cycles
```

which is more than sufficient for occasional configuration updates.

---

# Example Usage Scenario

## First-Time Setup

```text
Install Device
      ↓
Connect WiFi
      ↓
Enter Caregiver Number
      ↓
Save Configuration
```

---

## After Power Failure

```text
Power Restored
      ↓
Read EEPROM
      ↓
Restore Settings
      ↓
Resume Operation
```

The system continues operating normally without user intervention.

---

# Future Improvements

Potential future EEPROM usage:

- Multiple Caregiver Contacts
- Medicine Database
- Health History Cache
- Emergency Threshold Storage
- Personalized Alarm Settings
- Device Usage Statistics

---

# Security Considerations

Future versions may include:

- Configuration Encryption
- Access Authentication
- Cloud Backup
- Secure Restoration

to protect patient information.

---

# Educational Value

This subsystem demonstrates:

- Non-Volatile Memory
- Embedded Data Storage
- Configuration Management
- IoT Device Persistence
- Healthcare Device Reliability
- EEPROM Read/Write Operations

Understanding EEPROM storage is an important aspect of designing reliable connected healthcare devices where configuration data must survive power interruptions and system restarts.