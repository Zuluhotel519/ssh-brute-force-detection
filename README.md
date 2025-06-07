
# 🛡️ SSH Brute Force Detection using Fail2Ban (SOC Project)

## 📌 Overview
This project simulates a brute-force SSH attack from an external attacker (Kali) against a Linux server. It showcases detection and response using Fail2Ban and log analysis — simulating the work of an entry-level SOC analyst.

---

## 🎯 Objective
- Simulate an SSH brute-force attack using Hydra
- Monitor `/var/log/auth.log` for failed login attempts
- Detect and block attacker using Fail2Ban
- Document attacker behavior and mitigation timeline

---

## 🛠️ Lab Setup
| Component     | Role                              |
|---------------|-----------------------------------|
| Kali Linux    | Attacker (Hydra, SSH brute force) |
| Ubuntu Server | Target (SSH, Fail2Ban, logging)   |

**Attacker IP:** `192.168.56.1`  
**Target IP:** `192.168.56.102`

---

## 🔥 Attack Simulation
Hydra command used:
```bash
hydra -l testuser -P /usr/share/wordlists/rockyou.txt ssh://192.168.56.102

Log Example:Failed password for testuser from 192.168.56.1 port 60593 ssh2

Detection & Response (Fail2Ban)
Fail2Ban configured to monitor SSH logins

After 3 failed attempts, the attacker's IP was banned

Fail2Ban Output: Banned IP list: 192.168.56.1

Screenshots
- Hydra brute-force attempt

- /var/log/auth.log with failed logins

- fail2ban-client status sshd with banned IP


MITRE ATT&CK Mapping 

| Tactic            | Technique                                                         |
| ----------------- | ----------------------------------------------------------------- |
| Credential Access | [T1110 – Brute Force](https://attack.mitre.org/techniques/T1110/) |


Lessons Learned
How brute-force attacks are detected through log analysis

How to configure automated blocking with Fail2Ban

The importance of understanding attacker behavior from both red and blue team perspectives



Author Notes
This project was built as part of a cybersecurity portfolio for SOC Analyst readiness. It combines attacker simulation with defensive response, modeled after real-world incidents.


