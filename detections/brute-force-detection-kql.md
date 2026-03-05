# Brute Force Authentication Detection (Elastic SIEM)

## Description
Detects repeated failed authentication attempts using the `su` command which may indicate a brute force attack.

## Data Source
Elastic Agent — system.auth logs

## Detection Query (KQL)

process.name: "su" AND message: "FAILED"

## Detection Logic

Trigger an alert when:

- More than 5 failed authentication attempts
- Within 1 minute
- Targeting the same user account

## MITRE ATT&CK Mapping

Technique: T1110  
Tactic: Credential Access

## Investigation Steps

1. Check authentication logs in Kibana Discover
2. Identify the targeted account
3. Determine if a successful login occurred afterward
4. Investigate the host performing the authentication attempts

## Response Actions

- Lock the targeted account
- Investigate source IP
- Monitor system for persistence attempts
