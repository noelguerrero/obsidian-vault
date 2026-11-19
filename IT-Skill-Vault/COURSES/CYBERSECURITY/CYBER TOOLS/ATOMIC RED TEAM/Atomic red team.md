**Atomic Red Team** is an open-source security testing framework that helps organizations safely emulate attacker techniques in a controlled way. It is maintained by [Red Canary](https://redcanary.com?utm_source=chatgpt.com) and maps tests to the MITRE ATT&CK framework.

### What it does

Atomic Red Team provides small, focused tests called **"atomics"**. Each atomic test simulates a specific adversary behavior, such as:
- Creating a suspicious scheduled task
- Dumping process memory
- Modifying registry keys
- Executing PowerShell commands
- Using credential access techniques

These tests allow defenders to verify whether:
- Security tools detect the activity
- Logging is working correctly
- Alerting rules trigger as expected
- Incident response procedures are effective

### Example

Suppose you want to test whether your EDR detects PowerShell abuse. Atomic Red Team includes a test that runs a PowerShell command associated with a specific ATT&CK technique.

Example ATT&CK technique:
- T1059.001 PowerShell

The corresponding atomic test executes a benign PowerShell command that mimics how attackers often use PowerShell, allowing defenders to validate detections without deploying real malware.