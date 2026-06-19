SSH Brute Force Detection

Date: 2026-06-19
Severity: Medium
Status: True Positive

Description

Multiple failed SSH authentication attempts were detected against an invalid account (wronguser). The activity matched a brute-force attack pattern.

Timeline
Time	Event
02:25	First failed SSH login detected
02:57	Multiple failed login attempts observed
03:00	Splunk alert triggered
03:01	Investigation initiated
03:05	Activity confirmed as brute-force attempt
Investigation Findings
Source IP: 127.0.0.1
Target Account: wronguser
Failed Attempts: 195
Successful Authentication: None
Data Source: Linux Authentication Logs ingested into Splunk
Detection Query
index=linux sourcetype=linux_secure "Failed password"
| stats count by src_ip user
| where count > 20
Analysis

The source generated a high volume of failed authentication attempts within a short period. No successful login was observed. The activity is consistent with credential brute-forcing.

Verdict

True Positive

Recommendations
Block malicious source IP
Enable fail2ban
Enforce strong password policies
Implement MFA where possible
Lab Note

This activity was generated in a controlled lab environment. Source IP 127.0.0.1 represents localhost and was used to simulate attack behavior for detection engineering practice.
