# Incident 04 — Unauthorized User Creation

## Summary
A new user account named `attacker` was created on the system using the `useradd` command. Unauthorized user creation can indicate persistence activity following a system compromise.

Attackers often create new user accounts in order to maintain long-term access to a system after gaining initial access.

---

## Detection Query

The following KQL query was used to detect execution of the `useradd` command in Elastic SIEM:

```kql
process.name : "useradd"
```

---

## Evidence

Elastic SIEM logs captured execution of the useradd command which resulted in the creation of a new user account on the SOC-Lab system.

### User Creation Event

The following event shows the execution of the `useradd` command responsible for creating the new user account.

![User Creation Event](../../screenshots/incident-04-user-created-event.png)

---

### Log Details

The log details confirm that the new user account was successfully created on the host.

![Log Details](../../screenshots/incident-04-user-created-log.png)

---

## Analysis

Elastic SIEM detected execution of the useradd command on the SOC-Lab system. This command is used in Linux systems to create new user accounts.

Creation of unauthorized user accounts is a common persistence technique used by attackers after gaining access to a system. By creating their own account, attackers can maintain access to the system even if the originally compromised credentials are changed or revoked.

Monitoring account creation activity is therefore critical for identifying potential persistence mechanisms used during a compromise.

---

## Severity

Medium

Because:
- A new user account was created on the system
- Unauthorized accounts can allow attackers to maintain persistent access
- Account creation events require investigation to confirm whether they are legitimate

---

## Recommended Response
- Investigate the origin of the useradd command execution
- Review recent account creation activity on the system
- Remove any unauthorized user accounts if identified
- Monitor authentication logs for activity related to newly created users
  
---















