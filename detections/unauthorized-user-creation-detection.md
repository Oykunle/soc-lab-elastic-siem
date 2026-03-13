# Unauthorized User Creation Detection

## Description
This detection rule identifies execution of the `useradd` command on a Linux system. Attackers often create new user accounts to maintain persistence after gaining access to a compromised host.

Monitoring account creation activity helps security teams detect unauthorized persistence mechanisms.

---

## Detection Query (KQL)

```kql
process.name : "useradd"
```
---

## Log Source
Linux authentication logs

Example log locations:

/var/log/auth.log
/var/log/syslog
---

## Investigation Steps

1. Identify the user account that executed the `useradd` command.
2. Determine the newly created username.
3. Check whether the account creation was authorized.
4. Review additional activity from the same user or host.

---

## Severity

Medium

Because:

- A new user account was created on the system
- Unauthorized accounts can provide attackers with persistent access
- Account creation events require investigation to confirm legitimacy

---

## MITRE ATT&CK Mapping

Technique: T1136 — Create Account
Tactic: Persistence


