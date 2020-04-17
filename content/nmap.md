+++
title = "Nmap"
date = 2019-05-04T00:12:12+05:30
tags = ["nmap", "pentest"]
+++

Nmap is an open-source network scanner. It is used to discover hosts and services on a computer network by sending packets and analyzing the responses.
## Features
* **Host discovery** Identifying hosts on a network. For example, listing the hosts that respond to TCP and/or ICMP requests or have a particular port open.
* **Port scanning** Enumerating the open ports on target hosts.
* **Version detection** – Interrogating network services on remote devices to determine application name and version number
* **OS detection** – Determining the operating system and hardware characteristics of network devices.
* **Scriptable interaction with the target** – using Nmap Scripting Engine(NSE) and Lua programming language.


### Host Discovery

* **Ping Scan -sn**
* **TCP SYN Scan -sn -PS**
* **TCP ACK Scan -sn -PA**



### Scan all TCP ports
```
nmap -n -p- 192.168.1.1
```
