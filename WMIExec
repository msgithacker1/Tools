---
description: >-
  How to enumerate port 445 (SMB) using WMI Exec
---


## WMI Exec Introduction:

* WMI stands for Windows Management Instrumentation. This is a system that allows users to query and manage Windows systems remotely. It lets you configure Windows settings, query system information and execute commands remotely.&#x20;
* It uses port 135 (RPC) and port 445 (SMB) for communication.&#x20;
* WMI Exec lets attackers utilise WMI to execute commands remotely. They connect via WMI and execute commands.&#x20;

```shellscript
root@kali:~# wmiexec.py [Domain]/[User]:[Password]@[Target IP]
## Run WMI Exec with credentials on a domain-joined machine. 

root@kali:~# wmiexec.py -hashes [LMHASH]:[NTHASH][Domain]/[User]@[Target IP]
## Running WMI Exec with a pass-the-hash attack -> Using NTLM hashes for a user. 

root@kali:~# wmiexec.py [User]:[Password]@[Target IP]
## Running WMI Exec with credentials on a standalone machine.

root@kali:~# wmiexec.py -shell-type powershell [User]:[Password]@[Target IP]
## Use WMI Exec to start a PowerShell shell for the machine with credentials to authenticate.
```

-> Level of access/privs depends on what type of credentials you are using. Admin creds will give more privileged commands/access to files via WMI Exec compared to a regular user.&#x20;
