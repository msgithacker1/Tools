---
description: >-
  Insight into showmount - a tool used to enumerate NFS (Network File System on
  port 2049) shares on a victim. It's like smbclient for SMB shares.
---

# Showmount (NFS Enum)

## Introduction:

* NFS is a file system protocol that lets a computer access files over a network as if it were local storage.&#x20;
* A server would export a directory (share it) and clients would mount the export so it appears as a local directory.&#x20;
* If you find port 111 for rpcbind open on a machine, investigate NFS because rpcbind is a supporting service for NFS.&#x20;
* If port 111 is open, confirm NFS is running and on what port using:

```
root@kali:~# rpcinfo -p [Target]
```

-> This would list all RPC services and their ports.



***

## Usage:

* Show all exported/shared directories:

```
root@kali:~# showmount -e [Target]
```

-> For a directory, if it's marked with a \* sign, it means anyone can mount it. If it has a specified subnet, it means any machine with an IP in that subnet can mount it (including the attacker if the attacker has an included IP).&#x20;



* Mount a share and view its contents:

```
root@kali:~#  mkdir /folder
root@kali:~# mount -t nfs [Target]:/[Directory to Mount as Listed Above] /folder 
root@kali:~# cd folder
root@kali:~# ls
```

-> "-t" flag specifies the type of directory to mount.&#x20;
