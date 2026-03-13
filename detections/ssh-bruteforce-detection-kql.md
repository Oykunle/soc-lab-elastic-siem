# SSH Brute Force Authentication Detection

## Description
This detection identifies repeated SSH authentication failures in Linux authentication logs. Multiple failed login attempts in a short time window may indicate a brute-force attack targeting a user account.

---

## Detection Query (KQL)

```kql
message : "authentication failure"
```
---

## Data Source

Elastic Agent — system.auth logs collected from Linux authentication events.

Example log location: /var/log/auth.log

---

## Detection Logic

Generate an alert when:

- Multiple SSH authentication failures occur
- Within a short time window
- Targeting the same user account

This behavior may indicate password guessing or brute-force login attempts.

---

## Investigation Steps

1. Identify the targeted user account
2. Review the source host or IP address
3. Check if a successful login occurred after the failures
4. Review authentication activity from the same source

---

## Severity

Medium

Because:

- Repeated authentication failures occurred
- A user account was targeted
- Continued attempts may eventually result in account compromise

---

## MITRE ATT&CK Mapping

Technique: T1110 — Brute Force
Tactic: Credential Access








