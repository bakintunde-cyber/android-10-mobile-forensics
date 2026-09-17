# android-10-mobile-forensics
Android 10 mobile device forensic analysis of a Google Pixel 3, including application, messaging, location, account, and network artifacts.
# Android 10 Mobile Device Forensic Analysis – Google Pixel 3

## Project Overview

This project documents a mobile device forensic examination of a **Google Pixel 3 running Android 10**. The investigation focused on identifying and analyzing artifacts recovered from a forensic image of the device.

The examination included device identification, user accounts, installed applications, messaging artifacts, payment activity, location information, Wi-Fi configuration, connected Google devices, and other application-level evidence.

> **Project Type:** Academic Cyber Forensics Project
> **Focus:** Mobile Device Forensics / Digital Forensics
> **Platform:** Android 10
> **Device:** Google Pixel 3

---

## Investigation Objectives

The objectives of this investigation were to:

* Identify the make, model, and serial number of the device.
* Identify user account artifacts associated with the device.
* Determine the telephone number associated with the device.
* Identify non-stock applications installed on the device.
* Examine Facebook Messenger artifacts.
* Identify payment-related application activity.
* Analyze Google Maps location artifacts.
* Identify connected/casted Google devices.
* Examine Wi-Fi configuration artifacts.
* Document forensic evidence and the locations of relevant artifacts.

---

## Device Identification

The examined device was identified as:

| Attribute        | Finding        |
| ---------------- | -------------- |
| Make             | Google         |
| Model            | Pixel 3        |
| Serial Number    | `30f934cc5d14` |
| Operating System | Android 10     |

The device information was identified from the `softap.conf` artifact within the forensic image.

---

## User and Account Artifacts

The examination identified a Google account associated with the device as well as a second user profile.

For security and privacy purposes, account credentials and authentication data are **not published in this repository**.

The second user profile identified during the examination was associated with:

`thisisdfirtwo@gmail.com`

The artifact was located within the Android account database.

---

## Installed Applications

The investigation identified **20 non-stock applications** installed on the device.

The application information was examined using Android package-related artifacts, including:

```text
data/system/packages.list
```

The project specifically examined application artifacts associated with applications such as:

* Facebook Messenger
* Venmo
* Google Maps
* Google Chromecast
* Gmail

The installed-application count and package artifact were documented during the examination.

---

## Facebook Messenger Artifact Analysis

Facebook Messenger was examined to identify application and user-related artifacts.

### Identified Artifacts

| Artifact         | Finding                              |
| ---------------- | ------------------------------------ |
| Application      | Facebook Messenger                   |
| Version          | `195366473`                          |
| Install Date     | January 29, 2020                     |
| Username         | `thisis.dfir`                        |
| Message Evidence | Identified within Messenger database |
| Message Date     | February 1, 2020                     |

The application version was identified from the Android package database, while the installation date was identified through the application-state database.

The Messenger username was identified from:

```text
com.facebook.orca/databases/threads_db2
```

The investigation also identified authentication-related data within the Messenger application directory. Sensitive authentication information has been intentionally excluded from this public portfolio.

A Messenger message artifact dated **February 1, 2020** was also identified in the Messenger database.

---

## Payment Application Analysis

A payment-related artifact was examined to identify the application responsible for a **$5 payment**.

### Finding

**Application identified:** Venmo

The relevant artifact was associated with the application's Gmail-related database path documented during the investigation.

---

## Google Maps / Location Artifact Analysis

Google Maps artifacts were examined to identify location search activity stored on the device.

The investigation identified the following location search:

**121 E Tryon Rd, Raleigh, NC 27603**

**Date:** April 4, 2019
**Time:** 7:49:03.604 PM

The evidence was identified within:

```text
com.google.android.apps.maps/databases/gmm_myplaces.db
```

This demonstrates how application databases can preserve historical location-related activity that may contribute to a forensic timeline.

---

## Connected Google Device / Casting Analysis

The examination identified a **Google Nest Hub** as a Google device associated with casting/connection activity.

The investigation documented:

| Artifact                   | Finding             |
| -------------------------- | ------------------- |
| Connected Device           | Google Nest Hub     |
| MAC Address                | `ae:f6:c7:a8:a5:c2` |
| Wi-Fi / Hotspot Identifier | `CCookiesDcastleR5` |

The Google Chromecast application artifact was examined to identify the connected Google device.

The Wi-Fi configuration artifact was also examined for network-related information.

---

## Evidence Sources

The investigation relied on artifacts recovered from the Android forensic image.

Examples of examined artifacts included:

```text
data/misc/wifi/softap.conf

data/system/packages.list

data/system/packages.xml

data/system_de/11/accounts_de.db

data/system_ce/0/accounts_ce.db

data/data/com.facebook.orca/databases/threads_db2

data/data/com.facebook.orca/app_light_prefs/

data/data/com.google.android.apps.maps/databases/gmm_myplaces.db

data/misc/wifi/WifiConfigStore.xml

data/data/com.google.android.apps.chromecast.app/
```

These artifacts were used to correlate device, application, account, communication, location, and network-related information.

---

## Skills Demonstrated

### Digital & Mobile Forensics

* Android device forensic examination
* Mobile artifact identification
* Application artifact analysis
* Digital evidence documentation
* Evidence correlation
* Forensic timeline development

### Android Forensics

* Android file-system navigation
* Android application data analysis
* Package/application artifact analysis
* SQLite database artifact examination
* User/account artifact identification
* Wi-Fi configuration analysis

### Investigative Analysis

* Evidence identification
* Artifact correlation
* User activity reconstruction
* Location artifact analysis
* Communication artifact analysis
* Network/device relationship analysis

### Documentation

* Evidence-path documentation
* Forensic findings documentation
* Screenshot-based evidence preservation
* Technical reporting

---

## Key Findings Summary

| Investigation Area      | Result                               |
| ----------------------- | ------------------------------------ |
| Device                  | Google Pixel 3                       |
| OS                      | Android 10                           |
| Non-stock applications  | 20                                   |
| Facebook Messenger      | Identified and examined              |
| Messenger installation  | January 29, 2020                     |
| Messenger activity      | February 1, 2020 artifact identified |
| Payment application     | Venmo                                |
| Location artifact       | 121 E Tryon Rd, Raleigh, NC          |
| Location timestamp      | April 4, 2019 – 7:49:03.604 PM       |
| Connected Google device | Google Nest Hub                      |
| Wi-Fi identifier        | `CCookiesDcastleR5`                  |

---

## Evidence Screenshots

Screenshots demonstrating the forensic findings can be stored in the `/evidence/screenshots/` directory.

Suggested organization:

```text
evidence/
└── screenshots/
    ├── device-identification.png
    ├── installed-applications.png
    ├── messenger-artifact.png
    ├── payment-artifact.png
    ├── location-artifact.png
    ├── google-nest-hub-artifact.png
    ├── wifi-artifact.png
    └── home-screen.png
```

Each screenshot should be accompanied by a short description explaining:

1. What artifact is being displayed.
2. Where the artifact was located.
3. What forensic finding it supports.

---

## Forensic Artifact Documentation

A separate artifact reference can be maintained in:

```text
documentation/artifact-paths.md
```

This document can contain the artifact name, file path, forensic significance, and associated finding.

Example:

| Artifact              | Location                                  | Purpose                         |
| --------------------- | ----------------------------------------- | ------------------------------- |
| `packages.list`       | `data/system/`                            | Application/package information |
| `threads_db2`         | `com.facebook.orca/databases/`            | Messenger artifacts             |
| `gmm_myplaces.db`     | `com.google.android.apps.maps/databases/` | Google Maps/location artifacts  |
| `WifiConfigStore.xml` | `data/misc/wifi/`                         | Wi-Fi configuration information |

---

## Privacy & Redaction

This repository is intended for educational and professional portfolio purposes.

Sensitive information identified during the forensic examination has been intentionally **redacted or excluded**, including:

* Passwords
* Authentication tokens
* Credential hashes
* Private account information
* Personal telephone numbers
* Other information that is unnecessary for demonstrating the forensic methodology

The original forensic image is **not included** in this repository.

---

## Disclaimer

This project was completed in an academic cyber forensics environment using provided forensic evidence.

The findings documented in this repository represent the artifacts identified during the examination and are presented for **educational and portfolio purposes**. They should not be interpreted as findings from a real-world criminal investigation.

---

## Project Takeaways

This investigation provided practical experience analyzing Android mobile-device artifacts and connecting information across multiple applications and system databases.

The project demonstrated how forensic investigators can use artifacts from messaging applications, location databases, payment-related applications, account databases, and Wi-Fi configuration files to reconstruct portions of device and user activity.

It also reinforced the importance of documenting **where evidence was located, what the artifact represents, and how individual artifacts can be correlated to support a forensic finding**.
