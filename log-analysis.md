# Log Analysis Notes

## Overview

This document contains investigation notes, SPL queries, observations, and lessons learned while analyzing logs in Splunk using the BOTSv3 dataset.

The purpose of this analysis is to develop foundational SIEM and SOC analyst skills by exploring Windows event logs, investigating authentication activity, and learning how security events are represented within Splunk.

---

# Investigation 1: Initial EventCode 4625 Analysis

## Objective

The goal of this investigation was to identify failed Windows authentication events associated with EventCode 4625 and better understand how security logs are structured within Splunk.

---

## Initial Search

```spl
index=botsv3 "4625"
