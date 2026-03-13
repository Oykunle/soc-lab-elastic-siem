# Incident 03 — SU Brute Force Authentication Attempt

## Summary
Multiple failed `su` authentication attempts were detected targeting the user **hacker** within a short period of time. The repeated authentication failures suggest a possible brute-force attack where an attacker attempts to guess a user's password through multiple login attempts.

---

## Detection Method

Elastic SIEM logs were queried using the following search:

```kql
message : "FAILED SU"
```
The results revealed repeated authentication failures occurring within seconds.
---

## Evidence

### Brute Force Timeline

The SIEM timeline below shows multiple `su` authentication failures occurring within a short timeframe.

![Brute Force Timeline](../../screenshots/incident-03-bruteforce-timeline.png)

---

### Failed Authentication Event

The log below shows a failed `su` authentication attempt targeting the **hacker** account.

![Failed Authentication Event](../../screenshots/incident-03-bruteforce-event.png)
---

## Analysis

The logs show multiple failed attempts to switch to the hacker account using the su command. These attempts occurred within a very short time interval, which is not typical for normal user behavior.

This pattern strongly suggests automated or repeated password guessing activity commonly associated with brute-force attacks.

Although no successful authentication was recorded during this investigation, repeated login attempts increase the risk of eventual account compromise.
---

## Severity

Medium

Because:
	•	Multiple authentication failures occurred in a short timeframe
	•	The login attempts targeted a local user account
	•	Continued attempts could eventually result in account compromise
---

## Recommended Response

•	Investigate activity related to the targeted user account
•	Monitor the system for additional authentication attempts
•	Implement account lockout policies after repeated login failures
•	Review authentication logs for other suspicious behavior






















