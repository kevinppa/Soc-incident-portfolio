Incident Report – Suspicious Network Activity (PCAP Analysis)

Incident Type: Network Reconnaissance & Brute-Force Activity
Detection Source: Network traffic (PCAP analysis)
Analyst Role: SOC Analyst (Investigation & Triage)

1. Alert / Detection
Unusual network activity was identified during routine traffic review. A single, previously unknown internal IP generated a high volume of SSH and HTTP requests within a short timeframe, triggering suspicion of malicious behaviour.

2. Investigation
PCAP analysis revealed repeated TCP SYN packets across multiple ports, failed SSH authentication attempts, and automated HTTP requests targeting various URLs. The traffic pattern was consistent with reconnaissance and service enumeration rather than normal user behaviour.
Further inspection showed the use of common scanning techniques and tools typically associated with attackers attempting to identify vulnerable services.

4. Evidence
Source IP: Suspicious internal host
Destination IP: Internal server
Protocols Observed: TCP, HTTP, ICMP
Ports Targeted:
22 (SSH) – repeated connection attempts
80 (HTTP) – automated requests to multiple URLs
Indicators of Compromise:
      SYN scanning behaviour
      Brute-force style SSH attempts
      Web scanning patterns consistent with tools such as Nikto and DirBuster
PCAP Size: ~112,000 packets

4. Impact Assessment
The observed activity indicates an attempt to discover exposed services and potential vulnerabilities. If successful, this could have led to unauthorised access, service disruption, or data compromise. While no confirmed breach was observed, the activity posed a medium to high security risk.

5. Response & Recommendations
Block or isolate the source IP immediately
Review SSH authentication logs for successful logins
Enforce stronger authentication controls (e.g., account lockout, MFA)
Monitor for continued scanning or lateral movement
Alert security team and document incident for future detection tuning

Outcome:
Incident identified and assessed as malicious reconnaissance activity. Preventive controls and monitoring improvements recommended to reduce future risk.
