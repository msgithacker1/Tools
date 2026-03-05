---
description: A background of Wireshark as a cybersecurity tool.
---

# Wireshark Intro

## Overview:

Wireshark is a network analysing tool over CLI and GUI. It can be used to intercept live network packets over media, such as WiFi and Ethernet, and analyse them to provide an insight into the contents of traffic over a network.&#x20;

Wireshark provides advanced tools and features allowing users to perform much deeper analysis into intercepted data packets.



## Benefits:

* **Free**: it is a widely-used, free platform for network analysis and remains one of the best out there for this purpose.
* **Cross-platform support**: available for use on a variety of operating systems, like Linux and Windows.
* **Color-coding & accessibility**: display filters are provided by Wireshark for easy identification of certain network traffic for users, without which the process would be tedious and prone to errors.
* **Multi-protocol support**: Wireshark is able to detect and decode traffic over TCP, UDP, HTTPS, DNS and other commonly-used protocols. This is key for a more holistic network analysis and deeper packet inspection.
* **Statistics**: Wireshark provides statistics for network traffic. This is particularly useful for identifying points of interest.



## Wireshark for Red Teaming & Blue Teaming:

For red-teamers, Wireshark can be used to identify network traffic affected by their own attacks to visualise impact (or lack of). It can also be used to identify attack vectors by analysing network traffic and identifying vulnerabilities.&#x20;

VS

For blue-teamers, Wireshark can be used to detect attacks, monitor network performance and security of the network.&#x20;

***

# Wireshark Network Traffic

## Packet Capturing:

Intercepting network packets that are in transit across a network.



Start A Capture In Wireshark:



1. Select the interface you want to capture traffic from.&#x20;
2. Start the capture to begin capturing packets. Wireshark will capture all traffic it detects by default.



Using Capture Filters (to specify what packets to capture based on certain criteria):



1. In the Capture options, you'll have an option to set a filter. Enter your filter expression to filter for specific packets. The input line will turn green if the filter expression is valid. You can find other filter expressions in the Wireshark User's Guide.

{% code title="Example of filter expression to capture HTTP traffic only." %}
```
tcp port 80 
```
{% endcode %}

2. Start capture with the filter.
3. If desired, save the capture in a file to analyse later. To do this, stop the capture. Go to "File" and then "Save As".



Using Display Filters (to highlight certain packets of interest):



1. In the "Display Filter" field, type a filter expression (similar to a capture filter expression).

{% code title="Example of a filter expression to highlight packets with a specific IP address." %}
```
ip.addr == 192.168.0.1
```
{% endcode %}

2. Apply the filter.



{% hint style="info" %}
You can apply certain colouring rules for display filters based on certain criteria for improved visual aid. To do this, go to "Preferences" then go to "User Interface" and then "Colouring Rules". Add a rule here and specify the filter and colour. This can be useful for certain situations where you may need to identify certain types of traffic.
{% endhint %}

{% hint style="info" %}
You can also apply certain grouping rules for easier organisation of data packets. To do this, go to "Column Header" and choose, for example, "Sort Ascending". This helps group data packets based on certain attributes and is incredibly useful for finding patterns (e.g., what host data packets came from, what type of packets were sent etc.).
{% endhint %}



## Decoding Protocols:

This is all about seeing the contents of data packets captured by Wireshark in a readable way.&#x20;

***

Transmission Control Protocol (TCP):

Wireshark shows you TCP flags (e.g., SYN, ACK, RST, FIN). Very useful for identifying connection initiation and termination.



Hyper Text Transfer Protocol (HTTP):

Wireshark shows you URLs, headers and potential exploitable vulnerabilities for HTTP. Very useful when dealing with web traffic.



Domain Name Service (DNS):

Wireshark shows DNS query types, responses etc. Useful for domain enumeration.



Simple Mail Transfer Protocol (SMTP):

Wireshark shows commands and information related to mail delivery. Useful for analysing phishing network traffic.



Secure Sockets Layer/Transport Layer Security (SSL/TLS):

This is used for encrypted communication. By providing session keys to Wireshark, the tool can decrypt the contents of SSL/TLS sessions to reveal data like API keys.



{% hint style="info" %}
Wireshark uses "protocol dissectors" to decode some protocols. These dissectors are small pieces of code that parses packets to help make analysis more accurate.
{% endhint %}

***

## Wireshark & TCP/UDP Analysis:

{% code title="Example TCP filter for SYN packets." overflow="wrap" %}
```
tcp.flags == 0x02 
```
{% endcode %}

{% code title="Example UDP filter for DNS traffic." %}
```
udp.port == 53
```
{% endcode %}

