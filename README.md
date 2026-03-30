# 🚨 SOC Investigation: Brute Force Attack & PowerShell Execution

>  🚨 This project simulates a real-world SOC investigation, demonstrating practical skills in log analysis, event correlation, and multi-stage attack detection using Elasticsearch SIEM.

## 📌 Overview

This project simulates a real SOC investigation using log analysis in Elasticsearch.

Logs are provided in CSV format and analyzed using Elasticsearch.

## 🎯 Objective

Detect and analyze a potential attack involving:

- Brute-force login attempts

- Successful authentication

- Suspicious process execution



---



## 🔍 Findings



### 1. Failed Logins (4625)

Multiple failed login attempts detected → Possible brute-force attack



### 2. Successful Login (4624)

Same IP successfully authenticated → Potential compromise



### 3. Process Execution (4688)

Suspicious PowerShell activity detected



---


## 🧠 Analysis



The first attack originated from an internal IP (192.168.1.10), where multiple failed login attempts (Event ID 4625) were observed within a short time frame, indicating a brute-force attempt. This was followed by a successful login (4624), privilege escalation (4672), and PowerShell execution (4688), suggesting account compromise.



A second and more critical attack was detected from an external IP address (203.0.113.5). The attacker performed repeated failed login attempts, eventually gaining access to the admin account. This was followed by privilege escalation and suspicious PowerShell execution, indicating a high likelihood of malicious activity.



Additionally, another suspicious login was observed from IP (198.51.100.7), followed by command execution, which may indicate lateral movement or further compromise.



Normal user activity was also present (user1, user2, user3), confirming that the dataset includes both benign and malicious behavior, strengthening the reliability of the analysis.



This confirms a multi-stage attack lifecycle:

Brute Force → Initial Access → Privilege Escalation → Command Execution

indicating a successful account compromise and active malicious execution.


## ⏱️ Attack Timeline



- 10:00 → Multiple failed logins (192.168.1.10)

- 10:01 → Successful login + privilege escalation + PowerShell

- 10:05 → External brute-force attack (203.0.113.5)

- 10:05 → Account compromise + privilege escalation

- 10:05 → Suspicious PowerShell execution

- 10:07 → Additional suspicious login (198.51.100.7)
---

 ## 🔑 Key Insight

The detection was based on correlating multiple events rather than relying on a single alert, which is a critical SOC analyst skill.

---



## 📊 MITRE ATT&CK Mapping

- T1110 – Brute Force 

- T1059 – Command Execution 



---

## 🚨 Detection Logic

The following detection logic can be used in a SIEM to identify similar attacks:

- Multiple failed login attempts (Event ID 4625) from the same IP within a short time window
- Followed by a successful login (4624) from the same source
- Privilege escalation event (4672) assigned to the same account
- Suspicious process execution (4688), especially PowerShell

Detection Rule Concept:

IF:
    Failed logins > threshold
    AND successful login from same IP
    AND privilege escalation
    AND process execution

THEN:
    Trigger alert: Possible account compromise (Brute Force + Execution)
---

## 🔎 Indicators of Compromise (IOCs)



The following indicators were identified during the investigation:



- Suspicious IP Address: 203.0.113.5 (External brute-force source)

- Suspicious IP Address: 198.51.100.7 (Possible lateral movement)

- Targeted Account: admin

- Observed Activity:

  - Multiple failed login attempts (4625)

  - Successful authentication (4624)

  - Privilege escalation (4672)

  - Suspicious PowerShell execution (4688)



---



## 🛡️ Recommendations



Based on the findings, the following security measures are recommended:



- Implement account lockout policies to prevent brute-force attacks

- Continuously monitor failed login attempts (Event ID 4625)

- Restrict and log PowerShell usage to detect malicious activity

- Enable Multi-Factor Authentication (MFA) for privileged accounts

- Investigate and block suspicious external IP addresses
---
## ✅ Conclusion

🚨 Confirmed Security Breach (True Positive)



---



## 👩‍💻 Author

Reema
