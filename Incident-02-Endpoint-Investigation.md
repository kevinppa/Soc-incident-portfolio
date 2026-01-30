## Incident Report – Endpoint Compromise Investigation

**Incident Type:** Suspicious Endpoint Activity  
**Detection Source:** Endpoint artefact review  
**Analyst Role:** SOC Analyst (Investigation & Scoping)

---

### 1. Alert / Detection
Suspicious activity was reported on a Windows endpoint following concerns of unauthorised access and abnormal user behaviour. The system was isolated for investigation to determine whether a security incident had occurred.

---

### 2. Investigation
Endpoint artefacts were analysed to identify signs of compromise and establish an activity timeline. System logs, user profiles, disk partitions, installed applications, and connected external devices were reviewed to validate the alert and scope potential impact.

Analysis focused on:
- User account activity
- Installed and executed software
- External storage usage
- System configuration anomalies

---

### 3. Evidence
- **Operating System:** Windows 10 (64-bit)
- **Primary User Account:** Single active local user
- **Key Artefacts Reviewed:**
  - Event logs and system configuration
  - Disk partitions including unallocated space
  - Installed applications and cloud sync tools
  - USB device connection history
- **Indicators Observed:**
  - Unusual system configuration settings
  - Evidence of extensive external storage usage
  - Activity patterns requiring further monitoring

---

### 4. Impact Assessment
No immediate destructive activity was confirmed; however, artefacts indicated potential misuse and elevated risk of data exposure. The incident was assessed as **medium risk**, requiring continued monitoring and control improvements.

---

### 5. Response & Recommendations
- Preserve endpoint evidence and maintain system isolation if required
- Reset user credentials and review access privileges
- Review external device usage policies
- Enable enhanced endpoint monitoring and alerting
- Escalate to full forensic investigation if additional indicators emerge

---

**Outcome:**  
Incident validated and scoped. Preventive controls and monitoring improvements recommended to reduce future endpoint risk.
