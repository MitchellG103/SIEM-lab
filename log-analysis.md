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
```

---

## Observation

This broad search returned multiple results associated with the value 4625. The initial assumption was that these were Windows Failed login events. 
Most of these results were actually unrelated to failed login attempts. Upon further analysis many originated from Windows Application logs rather than Windows Security logs. 
This demonstrated the importance of validating log context instead of solely relying on event IDs. Many log types may share the same event ID that mean different things to different log types.
This mistake could have led to false reporting and further expenditure of resources unnecessarily. Luckily verification of the logs allowed this to all be avoided, if this were a real world scenario. 

---

# Investigation 2: Identifying Legitimate Security Authentication Events

##Objective

The next phase of analysis focused on finding legitimate Windows Security authentication logs. 

---

##Refined Search

```spl
index=botsv3 LogName=Security "4625"
```

---

