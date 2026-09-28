# Portfolio Project: Security Risk Assessment & Network Hardening

**Project ID:** SRA-2026-001  
**Target Environment:** Social Media Enterprise Infrastructure  
**Author / Analyst:** Junior SOC Analyst Portfolio  
**Framework Focus:** NIST SP 800-53 / Infrastructure Hardening  

---

## 1. Executive Summary
Following a major data breach that compromised customer Personally Identifiable Information (PII), a comprehensive security risk assessment was conducted on the organization's network infrastructure. This report details four critical vulnerabilities discovered during the security audit and outlines an enterprise-grade hardening strategy designed to eliminate single points of failure, secure administrative perimeters, and prevent future breach vectors.

---

## 2. Identified Vulnerabilities
An inspection of the organization's access controls, network layout, and asset configurations revealed four major systemic weaknesses:
1. **Password Sharing:** Internal employees routinely share credentials among peers, destroying individual accountability and audit trails.
2. **Default Administrative Credentials:** The core database administration portal was left configured with default factory credentials.
3. **Unfiltered Perimeters:** Network firewalls lack strict ingress and egress filtering rules to govern authorized traffic flow.
4. **Absence of Multifactor Authentication (MFA):** Critical systems rely exclusively on single-factor password authentication.

---

## 3. Hardening Recommendations & Remediation Plan

To address these vulnerabilities and fortify the network against future intrusions, a three-pillar hardening framework is proposed:

### Pillar 1: Multifactor Authentication (MFA) Implementation
* **Mechanism:** Enforces dual- or multi-layer verification (combining something you know—a password—with something you have—a hardware token, authenticator app, or biometrics).
* **Security Impact:** Neutralizes automated brute-force attacks and credential stuffing. Furthermore, MFA effectively discourages password sharing: even if an employee shares their password with a colleague, the unauthorized user cannot complete the login sequence without the owner's physical second-factor device.

### Pillar 2: Strict Password Policies & Baseline Configurations
* **Mechanism:** Establishes rigorous cryptographic standards (minimum length, forced complexity, character variety, and prohibition of password reuse). Integrates automated account lockout policies (e.g., locking access after 5 consecutive failed login attempts) and mandatory default password changes upon initial setup.
* **Security Impact:** Eradicates default administrative vulnerabilities and prevents weak or predictable credential creation across the organization.

### Pillar 3: Proactive Firewall Maintenance & Traffic Filtering
* **Mechanism:** Mandates routine audits of firewall rulesets to align with up-to-date security baselines. Implements strict ingress and egress packet filtering, alongside dynamic blacklisting of anomalous source IPs.
* **Security Impact:** Prevents unauthorized external reconnaissance, mitigates DoS/DDoS vectors, and stops malicious payloads from traversing internal network segments.
