+++
title = "Nmap"
date = 2019-05-04T00:12:12+05:30
tags = ["nmap"]
+++

## Port Scan

**Scan using TCP connect**	
```
nmap -sT 192.168.1.1
```
**Scan using TCP SYN scan (default)**	
```
nmap -sS 192.168.1.1
```
**Scan UDP ports**	
```
nmap -sU -p 123,161,162 192.168.1.1
```

**check host live or not**
```
nmap -sP 192.168.1.1
```