# Incident Report 02 — Endpoint Compromise Investigation

**Incident Type:** Suspicious Endpoint Activity  
**Detection Source:** Endpoint Artefact Review  
**Operating System:** Windows 10 (64-bit)  
**Analyst Role:** SOC Analyst (Investigation & Scoping)  

---

## 1. Executive Summary

Suspicious activity was reported on a Windows 10 endpoint following concerns of unauthorised access and abnormal behaviour.

A forensic image of the system was analysed to:

- Validate whether compromise occurred  
- Identify potential persistence mechanisms  
- Review user activity  
- Assess data exposure risk  

No immediate destructive activity was confirmed; however, artefacts indicated elevated risk and required monitoring and remediation.

---

## 2. Scope

- **Operating System:** Windows 10 Education (64-bit)  
- **Primary User Profile:** Single active local user  
- **Disk Image:** Forensic clone with verified hash integrity  
- **Analysis Tools Referenced:** Autopsy, EnCase, FTK Imager, Magnet AXIOM  

The investigation focused on artefact analysis, user activity, system configuration, and external device usage.

---

## 3. Evidence Integrity & Validation

Before analysis:

- Forensic image created using FTK Imager  
- Write-blocking techniques applied  
- SHA-256 hash generated and verified  
- Hash revalidated during analysis  

This ensured no evidence tampering occurred.

---

## 4. Investigation Approach (SOC Workflow)

---

### Step 1 — Operating System Configuration Review

The following system details were identified:

- Windows 10 Education (64-bit architecture)  
- System Root Directory: `%SystemRoot%\TEMP`  
- Product ID recorded  

The unusual system root directory configuration was noted for further review.

---

### Step 2 — Disk Partition Analysis

The disk contained multiple partitions including:

- Unallocated space (potential deleted artefacts)  
- Basic data partitions (user activity storage)  
- EFI system partition (boot files)  
- Microsoft reserved partition  

Unallocated space was reviewed for potential recoverable deleted files.

---

### Step 3 — Installed Applications Review

Analysis of installed software revealed:

- Cloud synchronisation tools (Box Sync, Google Backup & Sync)  
- S3 Browser (Amazon S3 interaction)  
- Multimedia drivers and system utilities  
- Communication and productivity applications  

The presence of cloud storage tools indicated possible external data synchronisation.

---

### Step 4 — USB Device Analysis

Multiple USB artefacts were identified:

- SanDisk flash drives  
- USB root hubs  
- Dell integrated webcam  
- Bluetooth module  

The use of removable storage introduced potential data exfiltration risk.

---

### Step 5 — User Profile Analysis

Single active local account observed.

Artefacts reviewed included:

- Login behaviour  
- System activity  
- File usage patterns  
- Cloud interaction  

No confirmed privilege escalation or malware execution was observed during artefact review.

---

## 5. Indicators Observed

- Unusual system configuration settings  
- Extensive external storage usage  
- Active cloud synchronisation applications  
- Multiple partitions including recoverable space  

While no confirmed malicious binary execution was identified, the combination of external storage usage and cloud synchronisation presented elevated data exposure risk.

---

## 6. Impact Assessment

Potential risks included:

- Data exfiltration via USB devices  
- Cloud-based data synchronisation outside monitored channels  
- Persistence through user-level configurations  
- Possible misuse of legitimate applications  

**Risk Level:** Medium  

---

## 7. Response & Recommendations

### Immediate Actions
- Reset user credentials  
- Review access privileges  
- Enable enhanced endpoint monitoring  

### Hardening Measures
- Restrict external USB storage usage  
- Implement stricter endpoint logging  
- Monitor cloud synchronisation activity  

### Monitoring Improvements
- Enable advanced logging  
- Review unallocated space for future cases  
- Implement continuous EDR monitoring  

---

## 8. Final Assessment

The endpoint did not show confirmed destructive compromise; however:

- Artefacts indicated elevated risk  
- Data exposure pathways existed  
- Monitoring controls required strengthening  

Preventive controls and enhanced monitoring were recommended to reduce future endpoint risk.

---

**End of Report**
