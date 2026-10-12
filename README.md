# Patricio Pérez - Cybersecurity Portfolio

> Junior SOC Analyst portfolio containing security incident reports, log analysis, and network hardening documentation.

## 🎯 About Me
Dedicated professional transitioning into defensive cybersecurity with a strong analytical foundation. Currently advancing through the Google Cybersecurity Professional Certificate with a targeted roadmap toward the Blue Team Level 1 (BTL1) certification. Focused on network traffic analysis, incident response, and applying enterprise security frameworks to protect critical infrastructure.

## 🛠️ Core Competencies & Tools
* **Security Frameworks:** NIST Cybersecurity Framework (CSF), NIST SP 800-53, CIA Triad.
* **Network Security:** Traffic Analysis (Wireshark, `tcpdump`), Firewall Rule Configuration, Protocol Analysis (TCP/IP, ICMP, DNS).
* **Defensive Operations:** Intrusion Detection/Prevention Systems (IDS/IPS), Threat Containment, Root Cause Analysis.
* **Infrastructure Hardening:** Multi-Factor Authentication (MFA) enforcement, Cryptographic baselines, Identity & Access Management (IAM).

---

## 📁 Project 1: Security Risk Assessment & Network Hardening
**Project ID:** SRA-2026-001 | **Target Environment:** Enterprise Infrastructure

### 1. Executive Summary
Following a major data breach that compromised customer Personally Identifiable Information (PII), a comprehensive security risk assessment was conducted on the organization's network infrastructure. This report details four critical vulnerabilities discovered during the security audit and outlines an enterprise-grade hardening strategy designed to eliminate single points of failure, secure administrative perimeters, and prevent future breach vectors.

### 2. Identified Vulnerabilities
An inspection of the organization's access controls, network layout, and asset configurations revealed four major systemic weaknesses:
1. **Password Sharing:** Internal employees routinely share credentials among peers, destroying individual accountability and audit trails.
2. **Default Administrative Credentials:** The core database administration portal was left configured with default factory credentials.
3. **Unfiltered Perimeters:** Network firewalls lack strict ingress and egress filtering rules to govern authorized traffic flow.
4. **Absence of Multifactor Authentication (MFA):** Critical systems rely exclusively on single-factor password authentication.

### 3. Hardening Recommendations & Remediation Plan
To address these vulnerabilities and fortify the network against future intrusions, a three-pillar hardening framework is proposed:

* **Pillar 1: Multifactor Authentication (MFA) Implementation**
  * **Mechanism:** Enforces dual- or multi-layer verification (combining something you know—a password—with something you have—a hardware token, authenticator app, or biometrics).
  * **Security Impact:** Neutralizes automated brute-force attacks and credential stuffing. Furthermore, MFA effectively discourages password sharing.
* **Pillar 2: Strict Password Policies & Baseline Configurations**
  * **Mechanism:** Establishes rigorous cryptographic standards (minimum length, forced complexity, prohibition of password reuse) and integrates automated account lockout policies.
  * **Security Impact:** Eradicates default administrative vulnerabilities and prevents weak or predictable credential creation across the organization.
* **Pillar 3: Proactive Firewall Maintenance & Traffic Filtering**
  * **Mechanism:** Mandates routine audits of firewall rulesets to align with up-to-date security baselines. Implements strict ingress and egress packet filtering.
  * **Security Impact:** Prevents unauthorized external reconnaissance, mitigates DoS/DDoS vectors, and stops malicious payloads from traversing internal network segments.

### 4. Conclusion
Implementing this hardening framework shifts the organization's security posture from reactive incident response to proactive defense. By eliminating default credentials, locking down perimeters through firewall maintenance, and enforcing MFA, the organization drastically reduces its attack surface.

---

## 📁 Project 2: Incident Response Analysis - DDoS ICMP Flood
**Project ID:** IR-2026-002 | **Framework Focus:** NIST CSF

### 1. Incident Summary
A multimedia enterprise experienced a two-hour Denial of Service (DDoS) attack caused by an incoming flood of ICMP packets through an unconfigured firewall, which disrupted normal internal network operations. The incident was contained by blocking ICMP traffic, pausing non-critical network services, and restoring critical functions. Long-term mitigations were established by implementing firewall rate-limiting, source IP address verification, network monitoring software, and an IDS/IPS filtering system.

### 2. NIST CSF Application Lifecycle

#### Identify
* **Perimeter Audit:** Conducted regular audits of network configurations, firewall rulesets, and perimeter access points to identify unconfigured or overly permissive rules.
* **Asset Mapping:** Cataloged critical network resources and services vulnerable to volumetric or flood-based attacks.

#### Protect
* **Firewall Hardening:** Implemented strict firewall rules, including rate-limiting for incoming ICMP packets to prevent traffic surges.
* **Source Verification:** Enabled source IP address verification on firewalls to detect and drop spoofed IP packets.
* **Attack Surface Reduction:** Isolated non-critical network services during high-risk events to protect core business assets.

#### Detect
* **Traffic Monitoring:** Deployed proactive network monitoring software to establish traffic baselines and detect abnormal volumetric patterns or spikes in real time.
* **IDS/IPS Deployment:** Integrated an Intrusion Detection and Prevention System (IDS/IPS) to automatically identify and filter out ICMP traffic exhibiting suspicious characteristics.

#### Respond
* **Immediate Containment:** Swiftly executed incident response playbooks by blocking malicious incoming traffic (ICMP floods) and taking non-critical services offline.
* **Root Cause Analysis:** Investigated the security event to identify the core weakness (the unconfigured firewall) and implemented targeted administrative controls.
* **Reporting:** Escalated the incident to upper management and appropriate legal authorities as required by corporate governance.


#### Recover
* **Service Restoration:** Safely brought critical network services back online once threat vectors were neutralized and perimeters were secured.
* **Post-Incident Verification:** Monitored network telemetry to ensure traffic flows returned to normal operating baselines and verified system stability before bringing non-critical systems back online.

---

## 📁 Project 3: Linux Access Control & File Permissions Hardening
**Project ID:** LNX-2026-003 | **Target Environment:** Enterprise Linux Server
**Framework / Concept:** Principle of Least Privilege (PoLP) & Discretionary Access Control (DAC)

#### 1. Project Description
As a security professional supporting an internal research team, my responsibility was to audit the Linux file system permissions within the `projects` directory to ensure alignment with corporate authorization standards. The audit involved verifying that existing permissions adhere to the principle of least privilege by identifying over-permissive files and directories. Using Linux command-line utilities, I modified access rights to eliminate unauthorized read and write access, ensuring that sensitive research assets remain protected against unauthorized modification and exposure.

#### 2. Check File and Directory Details
To perform a complete permission audit across the directory, I used the `ls -la` command. The `-l` flag lists the directory contents in a detailed, long format (including permissions, owner, group, and size), while the `-a` flag reveals hidden files (dotfiles) that are excluded by standard directory listings. 

The initial audit revealed the following permission structure:

```bash
researcher2@f0754b230eca:~/projects$ ls -la
total 32
drwxr-xr-x 3 researcher2 research_team 4096 Oct 12 21:49 .
drwxr-xr-x 3 researcher2 research_team 4096 Oct 12 22:27 ..
-rw--w---- 1 researcher2 research_team   46 Oct 12 21:49 .project_x.txt
drwx--x--- 2 researcher2 research_team 4096 Oct 12 21:49 drafts
-rw-rw-rw- 1 researcher2 research_team   46 Oct 12 21:49 project_k.txt
-rw-r----- 1 researcher2 research_team   46 Oct 12 21:49 project_m.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 12 21:49 project_r.txt
-rw-rw-r-- 1 researcher2 research_team   46 Oct 12 21:49 project_t.txt
```

#### 3. Describe the Permissions String
Taking `project_k.txt` as a reference (`-rw-rw-rw-`), the 10-character string indicates the file type and the discretionary access control (DAC) bits assigned to three distinct user categories:
*   **1st character (`-`):** Represents the file type. A hyphen (`-`) indicates a regular file, whereas a `d` represents a directory.
*   **2nd-4th characters (`rw-`):** Represent the **User/Owner** permissions (`researcher2`). The user has read (`r`) and write (`w`) permissions, but no execute (`-`) permission.
*   **5th-7th characters (`rw-`):** Represent the **Group** permissions (`research_team`). Group members have both read (`r`) and write (`w`) permissions.
*   **8th-10th characters (`rw-`):** Represent the **Others** permissions (all other system users). In this initial state, any user on the system possessed read (`r`) and write (`w`) access, representing a critical security violation.

#### 4. Change File Permissions
Organizational security policy prohibits "others" from having write access to any file. The baseline audit identified that `project_k.txt` violated this policy with permissions set to `-rw-rw-rw-`. To remediate this vulnerability, I executed `chmod o-w project_k.txt` to remove write permissions for the "others" group:

```bash
researcher2@f0754b230eca:~/projects$ chmod o-w project_k.txt
researcher2@f0754b230eca:~/projects$ ls -la project_k.txt
-rw-rw-r-- 1 researcher2 research_team 46 Oct 12 21:49 project_k.txt
```

#### 5. Change File Permissions on a Hidden File
The research team archived `.project_x.txt`, turning it into a hidden file indicated by the leading dot (`.`). To satisfy the team's security requirement, this file needed to have write permissions revoked for all users while maintaining read access exclusively for the file owner (`researcher2`) and the `research_team` group. I used the command `chmod u-w,g-w,g+r .project_x.txt` to enforce read-only authorization:

```bash
researcher2@f0754b230eca:~/projects$ chmod u-w,g-w,g+r .project_x.txt
researcher2@f0754b230eca:~/projects$ ls -la .project_x.txt
-r--r----- 1 researcher2 research_team 46 Oct 12 21:49 .project_x.txt
```

#### 6. Change Directory Permissions
Corporate access policy mandates that only the `researcher2` user should have access to the `drafts` subdirectory and its internal contents. The initial directory permissions (`drwx--x---`) granted execute (`x`) permission to the `research_team` group, allowing group members to traverse into the directory. To revoke unauthorized traversal and access, I executed `chmod g-x drafts`:

```bash
researcher2@f0754b230eca:~/projects$ chmod g-x drafts
researcher2@f0754b230eca:~/projects$ ls -la | grep drafts
drwx------ 2 researcher2 research_team 4096 Oct 12 21:49 drafts
```

#### 7. Summary
During this security engagement, I inspected the authorization model across the organization's research directory using `ls -la` to detect misconfigured file and directory permissions. Utilizing the `chmod` utility, I revoked public write permissions on `project_k.txt`, locked down archived data on `.project_x.txt` to read-only for authorized members, and restricted traversal into the `drafts` directory exclusively to the owner. These remediations successfully enforced the principle of least privilege, reducing the organizational attack surface and safeguarding data integrity and confidentiality.
