---
description: Tool used to enumerate SMB on Windows & Samba systems.
---

# Enum4Linux

## Introduction:

* It can be used to enumerate user accounts, shares, password policy, OS information etc.
* Useful if SMB port 445/139 is open on the target machine.
* Particularly useful because it doesn't require credentials to mine information. However, without creds, information gained may be limited.
* If you use it with credentials, you authenticate as a real use so you may be able to enumerate more shares, domain info, password policy details etc.&#x20;
* If you authenticate as a domain admin, you would get access to everything, including admin shares like ADMIN$ and C$.
* This is particularly useful for post-compromise enumeration.

***

## Usage:

```
root@kali:~# enum4linux -a [Target]    
```

-> Runs enum4linux against the target and performs full enumeration.



```
root@kali:~# enum4linux -u [User] -p [Password] -a [Target]
```

-> Authenticates as a user and runs enum4linux post-compromise to extract more information.&#x20;
