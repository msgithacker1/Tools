---
description: Used to send HTTP requests and test web servers.
---

# Curl

## Introduction:

* No special privileges are required.
* Used to send HTTP requests for basic authentication, cookies, test for SQLi etc.
* When testing for SQLi, using Curl is good but SQL Map automatically exploits SQLi so you can go straight to using it instead of Curl.&#x20;

***

## Usage:



* Basic GET request to return the HTML source code:

```
root@kali:~# curl "http://[Target IP]"
```

* Test for SQLi example:

```
root@kali:~# curl "http://[Target IP]/?id=1"
```

-> Assumes this webpage exists and belongs to a signed-in user.&#x20;

-> As a reference, the server would run a query like:

```sql
SELECT *
FROM Users
WHERE id = 1
```

-> For this to be SQLi, run this for example:

```
root@kali:~# curl "http://[Target IP]/?id=1 OR 1=1"
```

-> This is always true so would output all information (basically neutralises the WHERE clause in the SQL query as it becomes WHERE TRUE since 1=1 is always true).&#x20;

-> If the output is significantly larger than without the attempted SQLi, SQLi works and you just received a lot more information.&#x20;



* Basic authentication attempts:

```
root@kali:~# curl -u [Username]:[Password] http://[Target IP]
```



* Test for error-based SQLi example:

```
root@kali:~# curl "http://[Target IP]/?id=1 '"
```

-> This would be a SQL syntax error so if it results in an SQL Syntax Error, you know you could try SQLi.&#x20;
