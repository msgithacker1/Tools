---
description: Very useful brute-forcing tool for network services.
---

# Hydra

## Introduction:

* No special privileges required.
* Useful for cracking passwords on a range of network services like SSH, FTP, HTTP, RDP, SQL etc.
* Usage depends on what ports are open.&#x20;
* Can adjust speed depending on parallel threads with the "-t" flag for all types of scan. Default is "-t 16". The higher the number of threads, the higher the speed but more load on the target.&#x20;
* Syntax is very similar across the different protocols being targeted.&#x20;
* Remember, lockout is a real possibility. Limit lockout risk through a lower number of threads, add delays between attempts and distribute the brute force across multiple users to avoid targeting one account and raising suspicion.&#x20;

***

## Usage:



* Brute forcing SSH logon:

```
root@kali:~# hydra -l admin -P wordlist.txt ssh://[Target IP] -w 10 -v -f -o results.txt
```

-> "-l" signifies only one user to test. Uppercase "-L" would mean a list of users in a .txt file to test.

-> "-P" signifies a list of passwords to test. Lowercase "-p" would mean test a single password.

-> You can use this to modify usage for password spraying also.&#x20;

-> "-w 10" means wait 10 seconds between attempts. Useful for making it seem less suspicious and avoid being locked out.

-> "-v" means verbose output. Replace with "-V" for even more verbose output.&#x20;

-> "-f" means stop after the first successful login found.&#x20;

-> "-o" saves the results to a file (optional).&#x20;



* Brute forcing FTP logon:

```
root@kali:~# hydra -l admin -P wordlist.txt ftp://[Target IP] -w 10
```



* Brute forcing RDP (Remote Desktop Protocol - Windows) logon:

```
root@kali:~# hydra -l admin -P wordlist.txt rdp://[Target IP]
```

