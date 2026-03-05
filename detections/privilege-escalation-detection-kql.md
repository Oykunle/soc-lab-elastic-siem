# Privilege Escalation Detection (sudo)

## Detection Goal

Detect when a user gains root privileges using `sudo`.

Privilege escalation is a common step attackers take after gaining initial access.

## KQL Detection Rule

process.name: "sudo" AND message: "session opened for user root"

## Log Source

Elastic SIEM  
Dataset: system.auth

## Example Event

pam_unix(sudo:session): session opened for user root(uid=0) by oye(uid=1000)

## Investigation Steps

1. Identify the user executing sudo
2. Check timestamp of escalation
3. Review commands executed after privilege escalation
4. Confirm if activity is authorized

## Severity

Medium → High depending on context.

Unauthorized privilege escalation may indicate account compromise or attacker lateral movement.

## MITRE ATT&CK Mapping

T1068 – Exploitation for Privilege Escalation  
T1548 – Abuse Elevation Control Mechanism
