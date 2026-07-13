# Phishing Email Triage & Incident Response Report

## 📌 Project Overview
This project simulates the real-world workflow of a Security Operations Center (SOC) Analyst responding to a suspicious email report. Operating within a secure macOS environment, I performed static analysis on a suspected phishing email, extracted key Indicators of Compromise (IoCs), investigated malicious infrastructure using command-line utilities, and authored a formal Incident Report with actionable containment recommendations.

### 🛠️ Skills & Tools Demonstrated
* **Analysis Environment:** macOS (Terminal, native text processing)
* **OSINT & Network Tools:** Native `whois` domain lookup, MX Toolbox (simulated)
* **Core Competencies:** Email header analysis, look-alike domain identification (typosquatting), IoC defanging, and tactical incident reporting.
* **Framework:** Standard NIST SP 800-61 Rev. 2 Incident Handling guidelines (Containment, Eradication, and Recovery).

### 📧 Phishing Email Artifact
Key indicators like look-alike domains and urgent messaging were identified in the raw email text:

![Phishing Email Screenshot](email.png)
# Cyber Security Incident Report: Phishing Triage
**Date:** July 13, 2026  
**Analyst:** Vivek Patel  
**Severity:** Medium  

## 1. Executive Summary
On July 13, 2026, a suspicious email masquerading as a PayPal security alert was identified. The email attempts to induce panic by claiming the user's account is restricted and directs them to a credential-harvesting landing page. 

## 2. Indicator Extraction (IoCs)
| Indicator Type | Value |
| :--- | :--- |
| **Sender Address** | `secure-update@paypal-security-alert.com` |
| **Sender Domain** | `paypal-security-alert.com` |
| **Subject Line** | URGENT: Your account has been restricted! |
| **Defanged URL** | `hxxp://update-paypal-login-security[.]com/login/auth` |

## 3. Artifact Analysis
* **Email Spoofing:** The sender address uses look-alike domain tactics (typosquatting) to mimic legitimate PayPal communications.
* **Urgency:** The email utilizes social engineering by threatening permanent account closure within 24 hours.
* **Infrastructure:** A `whois` lookup reveals the domain was registered recently, which is highly characteristic of disposable phishing infrastructure.

## 4. Containment & Remediation Recommendations
To mitigate further risk, the following actions are recommended:
1. **Network Block:** Block inbound/outbound traffic to `paypal-security-alert[.]com` and `update-paypal-login-security[.]com` at the perimeter firewall and web proxy.
2. **Email Gateway Rule:** Purge all emails from `secure-update@paypal-security-alert.com` from all user inboxes globally.
3. **Credential Reset:** Force a password reset and revoke active sessions for any user who interacted with the link.
4. **User Awareness:** Deploy a targeted phish-training simulation for departments targeted by this campaign.
