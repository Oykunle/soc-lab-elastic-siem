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
- Authentication monitoring
- Privilege escalation detection
- Brute force attack detection
- Incident documentation
- Detection rule creation using KQL
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

Location:

 /incidents/

---

# Detection Rules

Detection rules written using **Kibana Query Language (KQL)** to identify suspicious activity within the Elastic SIEM environment.

| Detection | Description |
|----------|-------------|
| Brute Force Detection | Detects multiple failed authentication attempts in Linux authentication logs |
| Privilege Escalation Detection | Detects `sudo` usage and root session activity |
| Unauthorized User Creation Detection | Detects execution of the `useradd` command which may indicate persistence |

Location:

/detections/

---

# Evidence Screenshots

Security investigations include supporting evidence from Elastic SIEM dashboards.

Location:

/screenshots/

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

Oyekunle Alabi  
Cybersecurity Student — Ball State University  

Focused on building practical blue team and SOC analyst skills through hands-on lab environments.
