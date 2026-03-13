# Incident 02 — Privilege Escalation Detection

## Summary
A privileged command execution was detected in Elastic SIEM logs where the user `oye` initiated a `sudo` session, resulting in a root shell.

This activity represents a **privilege escalation event**, where a standard user temporarily obtained elevated privileges to perform administrative actions on the system.

---

## Detection Query

The following KQL query was used to identify `sudo` activity in Elastic SIEM:

```kql
process.name: "sudo"
```
---
## Evidence
Elastic SIEM logs captured the following events:
	1.	Root session opened using sudo
	2.	Root session closed
	3.	sudo activity visible in the SIEM timeline

---
### Root Session Opened

The following log shows a privileged root session being opened through `sudo`.

![Root Session Opened](../../screenshots/incident-02-root-session-open.png)

---

### Root Session Closed

This log confirms the root session was later terminated.

![Root Session Closed](../../screenshots/incident-02-root-session-closed.png)

---

### Sudo Activity Timeline

The timeline below shows `sudo` activity recorded in Elastic SIEM.

![Sudo Activity Timeline](../../screenshots/incident-02-sudo-activity.png)
---

## Analysis

The logs confirm that the user oye executed a sudo command which opened a root session on the system.

While this activity may be legitimate for system administration tasks, monitoring sudo usage is important because it represents privileged access to the system. If an attacker gains access to a user account with sudo privileges, they could potentially escalate privileges and gain full control of the host.

Detecting and investigating sudo activity helps security analysts identify potential privilege escalation attempts and unauthorized administrative actions.

---

## Severity

Medium

Because:
	•	Root privileges were granted through sudo
	•	Privileged commands could be abused if credentials are compromised
	•	Administrative activity requires monitoring in security operations

---

## Lessons Learned

Centralized logging in Elastic SIEM allows security analysts to detect and investigate privileged activity across systems.

Monitoring sudo usage and privileged sessions provides visibility into administrative actions and helps identify potential privilege escalation attempts during incident investigations.

---


























  
