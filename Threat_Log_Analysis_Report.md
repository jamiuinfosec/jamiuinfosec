# 🔍 Threat Log Analysis Report
**Author:** Jamiu Ibrahim (JamiuInfosec)  
**Date:** October 2025  

---

## 🧩 Overview
This project simulates a log analysis task where system logs were reviewed for suspicious login activities.  
The goal is to identify brute-force or unauthorized access attempts and recommend mitigation steps.

---

## 🧾 Sample Log Data
Oct 29 21:45:12 server sshd[1123]: Failed password for invalid user admin from 45.67.89.101 port 50432 ssh2
Oct 29 21:45:13 server sshd[1125]: Failed password for root from 45.67.89.101 port 50435 ssh2
Oct 29 21:45:14 server sshd[1127]: Failed password for root from 45.67.89.101 port 50436 ssh2
Oct 29 21:45:20 server sshd[1130]: Accepted password for root from 45.67.89.101 port 50440 ssh2
---

## 🧠 Analysis

- Multiple **failed SSH login attempts** occurred within seconds from the same IP: `45.67.89.101`.
- Login attempts targeted **privileged accounts** (`admin`, `root`).
- The attacker succeeded after several failures → Indicates a **brute-force attack**.

---

## 🚨 Threat Identified
**Type:** Brute-Force SSH Attack  
**Source IP:** 45.67.89.101  
**Target:** Root user  
**Risk Level:** High

---

## 🛡️ Recommended Mitigation

- Block IP address `45.67.89.101` in firewall or intrusion prevention system.  
- Enable **two-factor authentication (2FA)** for SSH logins.  
- Limit SSH access to specific trusted IPs only.  
- Configure **Fail2Ban** to automatically block repeated failed attempts.  
- Review system for signs of further compromise.

---

## ⚙️ Tools Used

- **Linux system logs (/var/log/auth.log)**  
- **Command-line tools:** grep, awk  
- **SIEM platforms:** Splunk / Wazuh (for real-time detection)  

---

✅ **Conclusion:**  
A brute-force SSH attack was successfully detected through log analysis.  
Timely response and account hardening were recommended to prevent further unauthorized access.
