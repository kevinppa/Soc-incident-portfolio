# Incident Report 03 — Suspicious Authentication Activity (Windows Event ID 4625)

**Incident Type:** Failed Logon Spike / Suspected Password Guessing  
**Detection Source:** Windows Security Logs  
**Event ID:** 4625  
**Analyst Role:** SOC Analyst (Authentication Triage)  

---

## 1. Executive Summary

Multiple failed logon events were detected within a short time window on a Windows system.

Analysis of Windows Security Logs identified:

- 12 failed authentication attempts  
- Occurring between 20:40–20:45  
- Targeting account: Kevin Philip  
- Logon Type: 2 (Local Logon)  
- Failure Reason: Unknown user name or bad password  

The pattern was consistent with password guessing or brute-force behaviour.

---

## 2. Scope

- **Event ID:** 4625  
- **Target Account:** Kevin Philip  
- **Logon Type:** 2 (Local)  
- **Time Window:** 20:40–20:45  
- **Total Failed Attempts:** 12  
- **Source:** Local machine  

The investigation focused on authentication anomalies within the defined time window.

---

## 3. Investigation Approach (SOC Workflow)

---

### Step 1 — Identify Failed Logon Events

Windows Event Viewer was used to filter:

Security Log → Event ID 4625

This identified multiple failed logon entries within a short timeframe.

---

### Step 2 — Analyse Logon Type

Logon Type 2 indicates:

- Interactive logon  
- Local system access attempt  

This suggests that the attempts originated directly on the system rather than via RDP (Logon Type 10).

---

### Step 3 — Review Failure Reason

Failure Reason recorded:

> Unknown user name or bad password

This indicates:

- Incorrect credentials supplied  
- No evidence of successful authentication  

---

### Step 4 — Pattern Analysis

Key characteristics observed:

- 12 failed attempts within 5 minutes  
- Targeting a single account  
- Consistent failure reason  
- No corresponding successful logon event  

This pattern is consistent with password guessing behaviour.

---

## 4. Technical Review

To isolate authentication failures, the following filter was applied in Event Viewer:

```text
Event ID: 4625
