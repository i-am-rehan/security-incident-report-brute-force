# 🛡️ Security Incident Scenario – Brute Force Attack and Malicious Redirect

## 📌 Overview

This case study documents a real-world style security incident affecting **yummyrecipesforme.com**, a public-facing recipe website. The incident involved a **brute force attack** on the admin panel, allowing an attacker to inject malicious code into the website's source. As a result, users who visited the site were prompted to download an executable file and were later redirected to a fake, malware-infected domain: **greatrecipesforme.com**.

This scenario demonstrates key skills in:
- **TCP/IP network analysis**
- **Protocol identification via `tcpdump`**
- **Incident documentation**
- **Security remediation planning**

---

## 📂 Background

An attacker (a former employee) exploited weak administrative controls to gain unauthorized access via brute force. Once inside the admin panel, they:

- Embedded **JavaScript code** to prompt users to download a malicious file
- Modified the admin credentials
- Redirected user traffic to a spoofed domain

Shortly after, customers reported being prompted to download suspicious files and experiencing performance issues after doing so.

---

## 🧪 Investigation Process

The cybersecurity team performed the following steps:

1. **Captured network traffic using `tcpdump`** in a sandbox environment by visiting the compromised URL.
2. **Reviewed the DNS and HTTP traffic logs** to trace the redirection and file download process.
3. **Mapped each packet log entry to TCP/IP model layers** and identified the relevant protocols involved in the attack.

---

## 🧠 Protocols Identified

| Layer | Protocols Observed |
|-------|---------------------|
| Application | HTTP, DNS |
| Transport | TCP |
| Internet | IP |
| Network Access | (implied: Ethernet/MAC – not logged in `tcpdump`) |

---

## 📝 Incident Summary

- **Source**: yummyrecipesforme.com (production website)
- **Attack Vector**: Brute force on admin login
- **Payload**: JavaScript code prompting a file download and redirect
- **Redirection**: yummyrecipesforme.com → greatrecipesforme.com
- **Tools Used**: `tcpdump` for log capture and investigation

---

## 🛡️ Remediation Recommendation

To prevent future brute force attacks, the following control is recommended:

### 🔐 Enforce Two-Factor Authentication (2FA)

Adding a second layer of verification significantly reduces the risk of unauthorized access — even if credentials are compromised through brute force or credential stuffing. 2FA increases overall system security by requiring both something the user knows (password) and something they have (authenticator app/token).

---

## 📎 Related Files

- `tcpdump-traffic-log.txt`: Raw log file of packet captures
- `Security_Incident_Report.md`: Detailed report covering protocol analysis, timeline, and remediation

---

## 📘 Learning Outcome

This project demonstrates how to:

- Analyze a network traffic capture
- Apply the TCP/IP model to real-world security incidents
- Document findings in a security incident report
- Recommend meaningful preventative measures

---

✅ Feel free to fork, clone, or reuse this case study to demonstrate your hands-on experience in threat analysis and incident response.
