# Privilege Escalation Detection (sudo)

## Description
This detection identifies when a user gains root privileges using the `sudo` command. Privilege escalation is a common step attackers take after gaining initial access to a system.

Monitoring `sudo` activity helps detect unauthorized administrative actions and potential system compromise.

---

## Data Source

Elastic Agent — `system.auth` logs from Linux authentication events.

---

## Detection Query (KQL)

```kql
process.name : "sudo" AND message : "session opened for user root"
```
---

## Example Event

pam_unix(sudo:session): session opened for user root(uid=0) by oye(uid=1000)

## Investigation Steps
1. Identify the user account executing the sudo command
2. Review the timestamp of the privilege escalation event
3. Examine commands executed after root access was obtained
4. Confirm whether the activity was legitimate administrative behavior

## Severity

Medium → High depending on context

Because:
- Root privileges were granted to a user account
- Privileged access could be abused if credentials are compromised
- Unauthorized escalation may indicate attacker activity
---

## MITRE ATT&CK Mapping

Technique: T1548 — Abuse Elevation Control Mechanism
Technique: T1068 — Exploitation for Privilege Escalation
