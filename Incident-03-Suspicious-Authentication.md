\## Incident Report – Suspicious Authentication Activity (Windows Event ID 4625)



\*\*Incident Type:\*\* Failed Logon Spike / Password Guessing  

\*\*Detection Source:\*\* Windows Security Logs (Event Viewer)  

\*\*Date Observed:\*\* <08/02/2026>  

\*\*Analyst:\*\* Kevin Mathew Philip



---



\### 1. Alert / Detection

Multiple failed logon events (Event ID 4625) were observed within a short time window, indicating abnormal authentication activity.



---



\### 2. Investigation

Windows Security logs were reviewed to determine the target account, logon method, and whether the pattern matched normal user behaviour. The activity showed repeated failures within minutes, consistent with password guessing attempts.



---



\### 3. Evidence

\- \*\*Event ID:\*\* 4625 (An account failed to log on)

\- \*\*Target Account:\*\* Kevin Philip

\- \*\*Logon Type:\*\* 2 (Local) 

\- \*\*Time Window:\*\* 20:40–20:45

\- \*\*Count:\*\* 12 failed logons

\- \*\*Failure Reason:\*\* Unknown user name or bad password

\- \*\*Source IP / Workstation:\*\* Local



---



\### 4. Impact Assessment

Repeated failed logons increase the risk of account compromise through brute-force or password guessing. If successful, an attacker could gain unauthorised access and potentially move laterally.



---



\### 5. Response \& Recommendations

\- Enforce account lockout policy and strong password requirements

\- Reset or secure the targeted account if needed

\- Enable MFA where possible

\- Monitor for continued attempts or new targeted accounts

\- If remote attempts are confirmed (Logon Type 10), block the source IP and review RDP exposure



---



\*\*Outcome:\*\* Suspicious authentication behaviour detected and documented. Further monitoring recommended.



