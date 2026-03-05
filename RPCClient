---
description: >-
  How to enumerate port 135 (RPC) using RPC Client.
---

# RPC Client

## RPC Client Introduction:

* RPC Client is used to enumerate the RPC protocol. RPC stands for Remote Procedure Call protocol.&#x20;
* RPC allows a computer to execute code remotely over a network on another computer. It can be exploited by hackers to enumerate users, dump credentials and execute code.&#x20;
* RPC Client is used to interact with Windows devices using RPC to extract this information.



Usage:

1. Gain an RPC Client CLI first:

```shellscript
root@kali:~# rpcclient -U "" -N [Target IP] 
## Null authentication attempt 

root@kali:~# rpcclient -U "[Domain]\[User]%[Password]" [Target IP]
## Authenticated RPC Client connection establishment in a Windows domain environment

root@kali:~# rpcclient -U "[Username]%[Password]" [Target IP]
## Authenticated RPC Client connection establishment to a standalone machine..
```

-> "-U": specifies the user to authenticate with.



2. Once in an RPC Client CLI:

```
rpcclient $> enumusers
## Enumerate users 

rpcclient $> enumgroups 
## Enumerate user groups

rpcclient $> tusername
## Get currently logged-in user information
```
