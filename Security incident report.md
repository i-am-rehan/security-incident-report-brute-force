# Security Incident Report – Brute Force Attack on yummyrecipesforme.com

---

## Section 1: Identify the Network Protocol Involved in the Incident

The network protocol involved in the incident is the **Hypertext Transfer Protocol (HTTP)**. This is identified in the `tcpdump` traffic log by connections initiated on **port 80**, the default port for HTTP. The client system established connections with both `yummyrecipesforme.com` and later `greatrecipesforme.com` using this protocol.

Since HTTP operates at the **Application Layer of the TCP/IP model**, it was used to transmit the malicious payload and redirect users to the spoofed website.

---

## Section 2: Document the Incident

On the day of the incident, multiple users contacted the helpdesk reporting that, while accessing the website `yummyrecipesforme.com`, they were prompted to download a file to access free recipes. Once the file was executed, the users were redirected to `greatrecipesforme.com`, and their computers started running unusually slow.

In response, the website owner attempted to log into the admin panel but failed. The cybersecurity team was engaged and used a **sandbox environment** to investigate. They used a **network protocol analyzer (tcpdump)** to observe the network behavior. 

The following events were identified in the logs:

- ✅ A **DNS request** was sent to resolve the IP for `yummyrecipesforme.com`.
- ✅ A **valid DNS response** was received.
- ✅ A **TCP 3-way handshake** (SYN, SYN-ACK, ACK) was completed.
- ✅ A **HTTP GET request** was sent by the client.
- ✅ A **download prompt** appeared and file execution followed.
- ✅ A **new DNS query** was triggered for `greatrecipesforme.com`.
- ✅ Another **HTTP request** confirmed the redirection.

Upon review, it was discovered that a **JavaScript function** was embedded into the site’s code to prompt this malicious download and redirection. A **brute force attack** had been used by a disgruntled former employee to guess the default admin password. The attacker:

- Accessed the admin panel
- Modified the source code
- Embedded malware
- Changed admin credentials

All of this was possible due to the **lack of brute force protections and weak password hygiene**.

---

## Section 3: Recommend One Remediation for Brute Force Attacks

To mitigate brute force attacks in the future, it is recommended to enforce **Two-Factor Authentication (2FA)** on all administrative accounts.

2FA adds an extra layer of protection by requiring a secondary code (from SMS, email, or an authenticator app) in addition to the password. Even if a password is compromised, attackers will not be able to log in without the second factor. This greatly reduces the risk of brute force attacks and enhances the organization's security posture.
