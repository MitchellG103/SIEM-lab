# SIEM Log Analysis Lab

## Project Overview

This project documents my hands-on learning experience with Security Information and Event Management (SIEM) concepts using Splunk Enterprise and the Splunk BOTSv3 dataset.

The goal of this lab is to learn how security analysts use SIEM platforms to ingest, search, filter, and analyze security logs in order to investigate authentication activity and identify potentially suspicious behavior.

This repository focuses on building foundational SIEM and SOC analyst skills through practical log analysis and SPL (Search Processing Language) queries.

---

## Lab Environment

The lab environment consists of a locally deployed Splunk Enterprise instance configured with the BOTSv3 dataset and supporting Splunk add-ons.

The dataset contains realistic Windows and network log data used to simulate activity that a security analyst may encounter in a real environment.

Logs Used:
- Windows Security Event Logs
- Windows Application Logs
- Additional BOTSv3 log sources

BOTSv3 Dataset:
https://github.com/splunk/botsv3

---

## Tools Used

- Splunk Enterprise
- Splunk Search & Reporting App
- SPL (Search Processing Language)
- Windows Event Logs
- BOTSv3 Dataset

---

## Current Learning Objectives

The primary objectives of this lab include:

- Learning how Splunk ingests and indexes log data
- Understanding how different log sources are structured
- Practicing SPL searches and filtering techniques
- Investigating Windows authentication events
- Identifying failed and successful login activity
- Learning how analysts validate log sources and event context
- Documenting findings and investigation workflows

---

## Topics Explored

Current topics explored within this lab include:

- Windows Security Event IDs
- Failed login analysis (EventCode 4625)
- Successful login analysis (EventCode 4624)
- Log source validation
- Sourcetype and field analysis
- SPL query troubleshooting
- Event filtering and data exploration

---

## Repository Contents

### splunk-setup.md
Documents the installation and configuration of Splunk Enterprise, BOTSv3 setup, add-ons, and log ingestion.

### log-analysis.md
Contains investigation notes, observations, event analysis, and lessons learned during log analysis.

### spl-queries.md
Documents useful SPL queries, their purpose, and how they were used during investigations.

### screenshots/
Contains screenshots of Splunk searches, statistics views, and investigation results.

---

## Skills Practiced

This lab demonstrates foundational cybersecurity and SOC analyst skills including:

- SIEM log analysis
- SPL query development
- Security event investigation
- Windows Event Log analysis
- Log source validation
- Data filtering and correlation
- Security documentation

---

## Future Goals

As I continue learning Splunk and SIEM workflows, future improvements may include:

- Building dashboards and visualizations
- Creating basic detection searches
- Correlating authentication events
- Investigating simulated attack activity
- Expanding into additional log sources and security telemetry

---

## Author

Mitchell G  
Cybersecurity Student | Blue Team Focus
