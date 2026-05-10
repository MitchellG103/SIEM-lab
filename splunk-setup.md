# Splunk SIEM Setup

## Overview

This document describes how the SIEM lab environment was configured using Splunk.  
The purpose of this setup is to ingest and analyze security logs in order to practice log analysis and event investigation.

---

## System Information

**SIEM Platform:** Splunk  
**Deployment Type:** Local installation  
**Operating System:** Windows 11 

**Log Sources:** Boss of the SOC (BOTS) Dataset Version 3 (https://github.com/splunk/botsv3)

---

## Installation Steps

1. Downloaded Splunk from the official website.
2. Installed the platform on a local system.
3. Started the Splunk service.
4. Install all necessary addons (https://github.com/splunk/botsv3). How to install addons: https://docs.splunk.com/Documentation/AddOns/released/Overview/Singleserverinstall
5. Accessed the Splunk web interface through the local web console or via the shortcut created with the installer.

Likely interface access:

```
http://localhost:8000
```

---

## Data Ingestion

Log data was imported into Splunk to simulate security monitoring.

Steps:

1. Locate $SPLUNK_HOME/etc/apps (commonly found in >Program Files on windows).
2. unzip downloaded dataset into previously identified file.
3. Open the Search & Reporting app on Splunk (located under the apps dropdown).
4. Index the logs for searching (index=botsv3)

---

## Verification

After ingestion, log data was verified by performing a basic search.

Example query:

```
index=botsv3
```

This confirmed that log data was successfully indexed and searchable.

---

## Notes

This lab environment is intended for educational purposes and focuses on learning how SIEM platforms ingest and analyze security logs.

The logs used can be found [here](https://github.com/splunk/botsv3)
