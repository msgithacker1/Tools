---
description: Useful for enumerating SMB on Windows and Samba systems.
---

# SMB Client

## Introduction:

* Unlike enum4linux, smbclient directly works with shares, allowing someone to also browse/upload/download files whereas enum4linux is used for read-only information gathering.&#x20;
* Enum4linux reveals what is there, smbclient lets an attacker actually access it.
* You can access sensitive shares like C$ and ADMIN$ if you have admin creds.&#x20;
* You can upload payloads/malicious files onto writable shares.&#x20;

***

## Use Cases:

* Listing available shares without creds:

```
root@kali:~# smbclient -L //[Target]
```

* Listing available shares with creds:

```
root@kali:~# smbclient -L //[Target] -U [Username]
```

-> You will be prompted for a password.

* Connecting to a specific share:

```
root@kali:~# smbclient -L //[Target]/[Share Name] -U [Username]
```

* Connecting with domain creds:

```
root@kali:~# smbclient -L //[Target]/[Share Name] -U [Domain]\\[Username]
```
