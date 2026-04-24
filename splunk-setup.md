# Splunk SIEM Setup

## Overview

This document describes how the SIEM lab environment was configured using Splunk.  
The purpose of this setup is to ingest and analyze security logs in order to practice log analysis and event investigation.

---

## System Information

**SIEM Platform:** Splunk  
**Deployment Type:** Local installation  
**Operating System:** Windows 11

**Log Sources:** (Example: Windows Event Logs, sample datasets)

---

## Installation Steps

1. Downloaded Splunk from the official website.
2. Installed the platform on a local system.
3. Started the Splunk service.
4. Accessed the Splunk web interface through the local web console.

Example interface access:

```
http://localhost:8000
```

---

## Data Ingestion

Log data was imported into Splunk to simulate security monitoring.

Steps:

1. Navigate to **Settings → Add Data**
2. Upload or monitor log files
3. Assign the correct **source type**
4. Index the logs for searching

---

## Verification

After ingestion, log data was verified by performing a basic search.

Example query:

```
index=*
```

This confirmed that log data was successfully indexed and searchable.

---

## Notes

This lab environment is intended for educational purposes and focuses on learning how SIEM platforms ingest and analyze security logs.
