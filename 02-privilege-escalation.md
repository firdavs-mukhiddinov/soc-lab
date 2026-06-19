# Privilege Escalation Attempt Detection

**Date:** 2026-06-19  
**Severity:** High  
**Status:** True Positive

## Description

A user attempted to access sensitive system files and elevate privileges using sudo commands. Activity involving access to `/etc/shadow` was detected and investigated.

## Timeline

| Time | Event |
|------|-------|
| 16:00 | First `sudo cat /etc/shadow` command detected |
| 16:24 | Second attempt to access `/etc/shadow` observed |
| 16:25 | Splunk alert triggered |
| 16:27 | Investigation initiated |
| 16:30 | Privilege escalation activity confirmed |

## Investigation Findings

- User: testuser
- Command Executed: `sudo cat /etc/shadow`
- Attempts: 2
- Sensitive File Targeted: `/etc/shadow`
- Data Source: Linux Authentication and Command Logs ingested into Splunk

## Detection Query

```spl
index=linux ("sudo" AND "/etc/shadow")
| stats count by user command
```




Analysis

The user attempted to access the /etc/shadow file, which contains password hash information and requires elevated privileges. Such behavior is commonly associated with privilege escalation attempts, credential access, or unauthorized system reconnaissance.

The activity was successfully detected through Splunk monitoring and validated during investigation.

Verdict

True Positive

Recommendations
Review user privileges and sudo permissions
Apply the principle of least privilege
Monitor privileged command execution
Enable detailed audit logging
Investigate any additional suspicious user activity
Evidence
Splunk Search Results

Event Details

Lab Note

This activity was generated in a controlled lab environment for security monitoring and detection engineering practice. The commands were intentionally executed to validate Splunk detection capabilities.
