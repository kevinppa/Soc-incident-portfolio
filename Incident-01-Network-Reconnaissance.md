# Incident Report 01 — Suspicious Network Activity (PCAP Analysis)

**Incident Type:** Network Reconnaissance, Brute-Force Attempts & Web Enumeration  
**Detection Source:** Network Traffic (PCAP – Wireshark)  
**Date Observed:** 6th November  
**Analyst Role:** SOC Analyst (Investigation & Triage)  
**Total Packets Analysed:** 112,563  

---

## 1. Executive Summary

Unusual network traffic was identified originating from **192.168.0.179** targeting internal server **192.168.0.160**.

The activity lasted approximately **39 minutes** and involved:

- TCP SYN scanning across multiple ports  
- Repeated SSH connection attempts (Port 22)  
- Automated HTTP requests across various URLs  
- ICMP traffic spikes  
- Multiple VNC connection attempts  

The traffic patterns were consistent with reconnaissance, service enumeration, and attempted brute-force behaviour.

No confirmed successful compromise was observed within the PCAP; however, the activity presented a **medium–high security risk**.

---

## 2. Scope

- **Source Host:** 192.168.0.179  
- **Target Server:** 192.168.0.160  
- **Duration:** ~39 minutes  
- **Total Packets Captured:** 112,563  

The investigation focused on abnormal communication between these two internal hosts.

---

## 3. Investigation Approach (SOC Workflow)

---

### Step 1 — IPv4 Conversation Analysis

Using:

`Statistics → Conversations → IPv4`

The majority of captured traffic occurred between:

- 192.168.0.179  
- 192.168.0.160  

The conversation lasted approximately 39 minutes and showed a significantly high packet exchange between the two hosts.

This sustained communication indicated abnormal behaviour requiring deeper inspection.

📸 **Screenshot 1 — IPv4 Conversations**

<img width="602" height="58" alt="image" src="https://github.com/user-attachments/assets/6442d191-1810-41c2-9db6-247c9b64190b" />


---

### Step 2 — Traffic Volume & Burst Analysis

Using:

`Statistics → I/O Graph`

The I/O graph revealed repeated traffic spikes within the investigation window.

Observations:

- High packet bursts over short time intervals  
- Source transmitted significantly more packets than received  
- Traffic behaviour consistent with automated scanning  

📸 **Screenshot 2 — I/O Graph**

<img width="601" height="399" alt="image" src="https://github.com/user-attachments/assets/f7e7994b-d673-4dcd-a901-f131e4ed5681" />


---

### Step 3 — Protocol Hierarchy Analysis

Using:

`Statistics → Protocol Hierarchy`

Findings:

- 89.0% of packets were HTTP  
- 45.2% of total bytes were HTTP traffic  
- Remaining traffic consisted of TCP, UDP, DNS, and ICMP  

The dominance of HTTP traffic aligned with automated web enumeration activity.

📸 **Screenshot 3 — Protocol Hierarchy**

<img width="470" height="242" alt="image" src="https://github.com/user-attachments/assets/d7440071-2e2e-4b4c-84a1-b6cc3d9d5dc4" />


---

### Step 4 — TCP SYN Scan Behaviour

Inspection of packet-level data revealed repeated TCP SYN packets targeting multiple ports.

Ports targeted included:

- 22 (SSH)  
- 80 (HTTP)  
- 143 (IMAP)  
- 53 (DNS)  

This behaviour indicated service discovery and reconnaissance activity.

#### Wireshark Filters Used

```text
# Identify SYN scan attempts
tcp.flags.syn == 1 && tcp.flags.ack == 0

# Filter traffic from suspicious source
ip.src == 192.168.0.179
