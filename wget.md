---
description: Wget is used to download files from the web.
---

# Wget

## Information:

* No special privileges are required.&#x20;
* Used to download files from the web.

***

## Usage:



* Downloading specific files from a website (to WD):

```shellscript
root@kali:~# wget http://[ip]/[file].[file ext]
```

-> You could also run this command from a Linux shell on the victim machine to download files from the attacker's IP (after opening a web server to make the attacker's files available to download).

-> Can be used to download files for payloads etc.

-> Add an optional "-q" flag for quiet output.&#x20;



