# Incident Report - Privilege Escalation Attempt

## Summary
- **Date:** 2026-06-19
- **Severity:** High
- **Status:** True Positive

## Description
User attempted to escalate privileges by reading /etc/shadow and switching to root user via sudo.

## Timeline
- 16:00 - First sudo cat /etc/shadow detected
- 16:24 - Second attempt: sudo cat /etc/shadow
