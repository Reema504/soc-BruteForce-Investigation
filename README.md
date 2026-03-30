# 🚨 SOC Investigation: Brute Force Attack & PowerShell Execution



## 📌 Overview

This project simulates a real SOC investigation using log analysis in Elasticsearch.

Logs are provided in CSV format and analyzed using Elasticseach.

## 🎯 Objective

Detect and analyze a potential attack involving:

- Brute-force login attempts

- Successful authentication

- Suspicious process execution



---



## 🧪 Scenario

An external IP (203.0.113.5) attempted multiple logins on an admin account.



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

The attacker performed brute-force attempts, gained access, and executed PowerShell commands.



---



## 📊 MITRE ATT&CK Mapping

- T1110 – Brute Force  

- T1059 – Command Execution  



---

### Brute Force Attempt


Multiple failed login attempts detected from external IP (203.0.113.5), indicating a brute-force attack.

---
## ✅ Conclusion

🚨 Confirmed Security Breach (True Positive)



---



## 👩‍💻 Author

Reema
