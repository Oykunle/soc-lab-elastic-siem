# Incident 05 — SSH Brute Force Authentication Attempt

## Summary
Multiple failed SSH authentication attempts were detected in Elastic SIEM logs targeting the user account `hacker`.

These events indicate a **possible brute-force attack**, where repeated login attempts are made in an effort to guess valid credentials.

The authentication failures were recorded in the Linux authentication logs and ingested into Elastic SIEM via Filebeat.

---

## Detection Query

The following KQL query was used to identify authentication failures in Elastic SIEM:

```kql
message : "authentication failure"

--

Evidence

Elastic SIEM logs captured authentication failures during SSH login attempts.
	1.	Authentication failure event recorded by the SSH daemon
	2.	Failed login attempt targeting the hacker account
	3.	Authentication failure visible in the SIEM timeline

--

Authentication Failure Event

The following log shows an SSH authentication failure detected by Elastic SIEM.
--

Authentication Failure Timeline

The timeline below shows authentication failures detected during the investigation period.
--

Analysis

The logs show repeated authentication failures during SSH login attempts for the user hacker.

The source host recorded in the logs was 127.0.0.1, indicating that the login attempts originated locally during the simulation.

Repeated authentication failures are consistent with brute-force login attempts where an attacker tries multiple passwords to gain access.

No successful login was observed during this investigation.
--

Severity

Medium

Because:
	•	Multiple authentication failures were detected
	•	The login attempts targeted a user account
	•	No successful authentication occurred
--

Lessons Learned

Monitoring Linux authentication logs in Elastic SIEM enables security analysts to quickly detect and investigate brute-force login attempts.

Centralized logging and SIEM detection rules allow analysts to identify suspicious authentication activity before an attacker successfully compromises an account.
--

Recommended Response
	•	Monitor SSH authentication logs for repeated login failures
	•	Implement account lockout policies after multiple failed login attempts
	•	Enable SSH key-based authentication
	•	Disable password authentication for SSH where possible
--

# Screenshot
incident-05-ssh-bruteforce-timeline.png
incident-05-ssh-bruteforce-event.png

Location: /screenshot/

