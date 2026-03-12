# SOC Lab — Elastic SIEM Detection & Incident Response

This project documents a personal Security Operations Center (SOC) home lab built using the Elastic Stack to simulate, detect, and investigate security incidents.

The purpose of this lab is to develop practical blue team skills including log analysis, threat detection, and incident investigation.

---

# Lab Environment

Tools used in this lab:

- Elastic Stack (Elasticsearch, Kibana)
- Elastic Agent
- Ubuntu Linux endpoint
- Filebeat system authentication logs
- KQL (Kibana Query Language)

Logs monitored:

- /var/log/auth.log
- /var/log/syslog

---

# SOC Skills Demonstrated

This lab demonstrates:

- SIEM log analysis
- Linux log analysis
- Authentication monitoring
- Threat detection & basic threat hunting
- Privilege escalation detection
- Brute force attack detection
- Detection rule creation using KQL
- Incident documentation
- Security investigation workflows

---

# Incident Investigations

| Incident | Description |
|--------|-------------|
| Incident 01 | Brute force authentication attempts detected against local user account |
| Incident 02 | Privilege escalation activity using sudo detected |
| Incident 03 | Repeated `su` authentication failures indicating brute-force behavior |
| Incident 04 | Unauthorized user account creation detected using `useradd` command |

All investigations include:

- Evidence screenshots
- SIEM queries
- Security analysis
- Recommended response actions

Location: `/incidents/`

---

# MITRE ATT&CK Mapping

The simulated incidents in this lab align with known adversary techniques documented in the MITRE ATT&CK framework.

| Incident | MITRE Technique | Description |
|--------|----------------|-------------|
| Incident 01 | T1110 – Brute Force | Multiple authentication failures detected against a user account |
| Incident 02 | T1548 – Abuse Elevation Control Mechanism | Privilege escalation using sudo |
| Incident 03 | T1110 – Brute Force | Repeated `su` authentication failures indicating brute force attempts |
| Incident 04 | T1136 – Create Account | Unauthorized user account creation detected through execution of the `useradd` command |

---

# Incident Severity Classification

Each simulated incident is categorized based on potential impact to system security.

| Incident | Severity | Reason |
|--------|---------|--------|
| Incident 01 | Medium | Multiple authentication failures indicating possible brute force |
| Incident 02 | High | Privilege escalation using sudo grants root access |
| Incident 03 | Medium | Repeated `su` authentication failures suggest credential guessing |
| Incident 04 | High | Unauthorized user account creation indicates persistence attempt |

---

# Detection Rules

Detection rules written using **Kibana Query Language (KQL)** to identify suspicious activity within the Elastic SIEM environment.

| Detection | KQL Query | Description |
|----------|-----------|-------------|
| Brute Force Detection | `event.dataset : "system.auth" AND message : ("FAILED SU" OR "authentication failure")` | Detects multiple failed authentication attempts in Linux logs |
| Privilege Escalation Detection | `event.dataset : "system.auth" AND message : "sudo"` | Detects sudo usage and potential privilege escalation |
| Unauthorized User Creation Detection | `process.name : "useradd"` | Detects creation of new user accounts |

Location: `/detections/`

---

# Evidence Screenshots

Security investigations include supporting evidence from Elastic SIEM dashboards.

Location: `/screenshots/`

Examples include:

- Authentication timelines
- Failed login events
- Root session activity
- Privilege escalation logs

---

# Future Improvements

Planned enhancements for this SOC lab include:

- SSH brute force detection
- Suspicious user account creation alerts
- Persistence detection techniques
- Network reconnaissance detection (Nmap scanning)
- Alert rule automation within Elastic SIEM
- MITRE ATT&CK technique mapping for incidents

---

# Author

GitHub: https://github.com/Oykunle/soc-lab-elastic-siem

Oyekunle Alabi  
Cybersecurity Student — Ball State University  

Focused on building practical blue team and SOC analyst skills through hands-on lab environments.
