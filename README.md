# Threat models

Attacker-centred threat models built with [OWASP Threat Dragon](https://owasp.org/www-project-threat-dragon/). Each model starts from what an attacker wants, breaks it down into the steps they would take, and attaches STRIDE threats and mitigations to each step.

## HelixPay: steal customer payment data

**File:** [`ThreatDragonModels/HelixPay/HelixPay.json`](ThreatDragonModels/HelixPay/HelixPay.json) · **Method:** PASTA attack tree + STRIDE

HelixPay is a payment-company case study. The attack tree has the goal *steal customer payment data* at the root, with AND/OR branches covering three routes:

| Route | Example attack steps |
|---|---|
| **Gain database access** | Take over one of 16 admin accounts (phishing + weak MFA + MITM session hijack), privilege escalation, lateral movement across microservices |
| **Compromise the payment server** | Exploit Log4j (Log4Shell), compromise the Jenkins server, abuse an exposed staging API, AWS misconfiguration |
| **Steal from customers directly** | Phishing customers, XSS / skimming script in the app, API gateway abuse (BOLA, credential stuffing) |

**18 threats** mapped across the tree:

| STRIDE category | Count |
|---|---|
| Information disclosure | 6 |
| Spoofing | 5 |
| Elevation of privilege | 5 |
| Repudiation | 1 |
| Tampering | 1 |

Severity: 5 Critical · 8 High · 5 Medium. Each threat carries a proposed mitigation.

### Open the model
1. Go to [Threat Dragon](https://www.threatdragon.com/) (or run it locally).
2. Choose **Open an existing threat model** and load `HelixPay.json`.
