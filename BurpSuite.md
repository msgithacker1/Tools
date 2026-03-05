---
description: >-
  A web-app pentesting platform. Useful for HTTP analysis and brute-forcing
  webpage logons.
---

# BurpSuite

## Introduction:

* Burp is a proxy that lies between the attacker's browser and the target web app.
* This helps it intercept, view, manipulate and replay HTTP/HTTPS traffic.
* You would use Burp for attacks like IDOR, SQLi, XSS etc.

***

## Set-Up:

* On Kali, start Burp and create a new project.
* On the browser, use a proxy like FoxyProxy and change the proxy connection settings to use HTTP Proxy 127.0.0.1 (or alternatively, 127.0.0.1:8080) with port 8080.
* Go to https://burp and download the CA certificate. Import the certificate and install it.
* Try searching something with the proxy enabled and Burp will intercept the information of the captured traffic.

***

## Important Tabs in Burp:

* Intruder tab: you can send a request to the intruder to fuzz parts of it using § markers. You may do this, for example, with a wordlist. Example:

```
username=admin&password=§password123§
```

-> Fuzzes the password section to attempt brute force.&#x20;



* Reponse tab: you can click on any row to see the Request tab which shows the exact HTPT request that was sent to the payload, which is useful to confirm what payoad was sent. It will also have the Response tab to show the full HTTP response from the server. This is where you can spot the difference between a fail or success of break-in. Look for status codes, response length (a successful login would usually have a different length) and response content (words like "welcome", "invalid", "logged in" etc.).

