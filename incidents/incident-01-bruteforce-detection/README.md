# Incident 01 — Brute Force Detection

## Summary
Multiple failed authentication attempts were detected targeting the user **hacker** within a short period of time. The repeated login failures suggest a possible brute-force attack where an attacker attempts to guess a user's password by trying multiple combinations.

## Evidence

Elastic SIEM logs showed repeated authentication failures with the following characteristics:

- `event.dataset: system.auth`
- `process.name: su`
- `event.outcome: failure`

More than **10 authentication failures occurred within approximately 30 seconds**, which is unusual for normal user behavior.

---

## Analysis

The pattern of repeated login failures within a short time window is not consistent with normal human activity. This behavior is commonly associated with brute-force password guessing attempts.

The activity targeted the **hacker** account using the `su` command, which indicates an attempt to switch user privileges on the system.

Eventually, a successful authentication event was recorded, indicating that the attacker was able to obtain valid credentials and open a session for the targeted account.

---

## Severity

**High**

Because:

- Multiple authentication failures occurred in a short time window
- The attack targeted a local user account
- A successful authentication event followed the failed attempts

---

## Containment Action

To reduce the risk of further compromise, the following response actions are recommended:

- Lock or temporarily disable the targeted account
- Investigate the source of the login attempts
- Monitor the system for additional suspicious activity or persistence attempts

---

## Lessons Learned

Centralized log collection in Elastic SIEM enables security analysts to quickly detect abnormal authentication behavior such as brute-force attacks.

By monitoring authentication logs and investigating suspicious login patterns, analysts can identify potential compromises and respond before attackers gain long-term access to the system.

---

## Investigation Evidence

### Authentication Attempt Timeline

The SIEM timeline below shows repeated `su` authentication attempts targeting the **hacker** account.

![Authentication Timeline](../../screenshots/incident-01-su-activity-timeline.png)

---

### Successful Authentication Event

The log below confirms that a successful `su` session was eventually opened for the **hacker** account.

![Successful SU Event](../../screenshots/incident-01-su-success.png)
