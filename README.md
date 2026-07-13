# Phishing-Triage-Report
A professional incident response report and triage workflow analyzing a simulated PayPal phishing campaign. Includes IoC extraction and containment strategies.

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
