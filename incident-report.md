# Incident Report - SSH Brute Force Attack

## Summary
- **Date:** 2026-06-19
- **Severity:** Medium
- **Status:** True Positive

## Description
195 failed SSH login attempts detected targeting invalid user "wronguser" from IP 127.0.0.1.

## Timeline
- 02:25 - First failed login detected
- 02:57 - Brute force activity continued (20+ attempts)
- 03:00 - Alert triggered in Splunk

## Investigation
- **Source IP:** 127.0.0.1
- **Target user:** wronguser (invalid user)
- **Total attempts:** 195
- **Successful login:** No

## Verdict
**True Positive** - Brute force attack pattern confirmed.

## Recommendation
- Block source IP via firewall
- Enable fail2ban to auto-block repeated failures
- Monitor for further activity
