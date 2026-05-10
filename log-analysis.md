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

## Refined Search

```spl
index=botsv3 LogName=Security "4625"
```

---

## Findings

This search successfully identified Windows Security authentication logs associated with failed login activity. 
The returned events included:
1. LogName=Security
2. SourceName=Microsoft Windows security auditing
3. EventCode=4625

This confirmed the events were legitimate Windows Failed login attempts.

---

# Investigation 3: Successful Authentication Events

## Objective

After identifying failed authentication events associated with EventCode 4625, the next phase of analysis focused on successful Windows authentication events using EventCode 4624.

The purpose of this investigation was to compare successful and failed login activity and better understand authentication patterns within Windows Security logs.

---

## Search Performed

```spl
index=botsv3 LogName=Security EventCode=4624
```

---

## Findings

This search returned a significantly larger number of results compared to failed authentication events associated with EventCode 4625.
This observation is expected because successful login activity occurs much more frequently in normal system operations.

The returned events represented legitimate Windows Security authentication activity and included:
1. Successful user logins
2. System authentication activity
3. Service account logins
4. Additional authentication-related events

---

# Authentication Event Analysis

## Failed Login Events

Search used:

```spl
index=botsv3 LogName=Security EventCode=4625
| stats count by Account_Name
| sort -count
```

---

## Purpose

This query was used to identify accounts associated with failed authentication attempts

---

# SPL Troubleshooting Lessons Learned

During investigation, several searches returned unexpected or empty results due to assumptions about sourcetypes and field names.

## Example failed search:

```spl
index=botsv3 sourcetype=WinEventLog:Security EventCode=4625
```
## Observation

This search returned no results because the dataset used: 

```spl
sourcetype=WinEventLog:Security 
```

While the security log channel was identified through:

```spl
LogName=Security 
```

Instead of using the sourcetype itself

---

## Key Lesson

SIEM environments may structure and normalize logs differently depending on:
1. log sources
2. add-ons
3. parsing configurations
4. ingestion methods

Analysts must validate:
1. sourcetypes
2. field names
3. log channels
4. metadata

Rather than assuming standardized conventions.

---

# Lessons Learned

This investigation demonstrated several important SIEM concepts:
1. Successful authentication events are typically far more common than failed authentication events
2. Windows environments generate large amounts of normal authentication activity
3. Analysts must distinguish between expected system behavior and suspicious patterns
4. Authentication analysis often requires filtering and narrowing results to identify meaningful activity

---

## Skills Practiced
1. SPL query construction
2. Filtering Windows Security logs
3. Event validation
4. Basic statistical analysis
5. Authentication event investigation
