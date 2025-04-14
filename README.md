# Detecting-and-Mitigating-Brute-Force-Attacks-using-Splunk-SIEM

# Brute-Force Attack Detection and Mitigation Using Splunk

## 👨‍💻 Analyst: Harikrishna Raval

## 📅 Date: April 2025

---

## 📌 Overview
This project simulates a brute-force attack detection and response using Splunk as the SIEM platform. It mirrors the workflow of a Security Operations Center (SOC) analyst — from monitoring to investigation to applying immediate and long-term mitigations.

---

## ⚙️ Tools & Technologies
- Splunk Enterprise (Trial)
- Windows 10 VM (Target)
- Kali Linux (Attacker)
- VirtualBox
- PowerShell & Bash

---

## 🚨 Attack Simulation
- **Attack Type:** Brute-force login attempts
- **Tools Used:** Hydra on Kali Linux
- **Target:** Windows RDP
- **Goal:** Trigger multiple failed logins followed by one success to simulate credential compromise

---

## 🔍 Detection in Splunk
**SPL Query Example:**
```spl
index=wineventlog EventCode=4625 OR EventCode=4624 
| stats count by Account_Name, host, EventCode, _time, src_ip 
| where count > 5
```

**Indicators of Compromise:**
- >5 failed login attempts from the same IP
- A successful login following failed attempts

---

## 🛡️ Incident Response
### Short-Term Actions:
- Account lockout and forced password reset
- IP block via Windows Firewall
- Admin notification

### Long-Term Hardening:
- Enforced account lockout policy
- Stronger password requirements
- Patch updates
- Disabled unused services
- Restricted RDP access via GPO

---

## 📁 Files Included
- `brute_force_report.pdf` – Full case report (4–5 pages)
- `splunk_query.txt` – Detection logic
- `screenshots/` – (Optional) Visuals of Splunk dashboards and alerts

---

## 🧠 Lessons Learned
- Real-time log analysis is key to early detection
- Even basic SIEM rules can detect brute-force behavior
- Hardening systems is essential to reduce future risk

---

## 📚 References
- MITRE ATT&CK T1110 – Brute Force
- Microsoft Security Event Codes
- Splunk Security Essentials

--
