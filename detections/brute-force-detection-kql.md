# Brute Force Authentication Detection (Elastic SIEM)

## Description
This detection identifies repeated failed authentication attempts using the `su` command. A high number of failures in a short period of time may indicate a brute-force password attack targeting a local user account.

## Data Source
Elastic Agent — `system.auth` logs collected from Linux authentication events.

## Detection Query (KQL)

```kql
process.name : "su" AND message : "FAILED"
```
---

## Detection Logic

Generate an alert when:
	•	More than 5 failed authentication attempts
	•	Occur within 1 minute
	•	Target the same user account

This behavior may indicate automated password guessing or repeated login attempts against a privileged account.

## MITRE ATT&CK Mapping

Technique: T1110 — Brute Force
Tactic: Credential Access

## Investigation Steps:

1. Review authentication logs in Kibana Discover
2. Identify the targeted user account
3. Check whether a successful login occurred after the failures
4. Investigate the host or session generating the authentication attempts

## Response Actions
	
- Temporarily lock or disable the targeted account
- Investigate the source host or IP address
- Continue monitoring the system for additional authentication attempts or persistence activity
