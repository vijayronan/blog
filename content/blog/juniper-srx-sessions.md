+++
title = "Juniper SRX Sessions"
date = 2018-06-22T01:09:10+05:30
tags = ['srx','juniper']
+++

## Display Sessions Summary
```
show security flow session summary
```
## Display All Sessions
```
show security flow session
```
## Terminate All Sessions
```
clear security flow session all
```
## Display a Specific Source IP / Subnet Session
```
show security flow session source-prefix 10.29.29.93
show security flow session source-prefix 10.29.28.0/24
```
## Display a Specific Destination IP / Subnet / Port Session
```
show security flow session destination-prefix 4.2.2.2
show security flow session destination-prefix 8.8.8.0/8
show security flow session destination-port 80
```
## Terminate the session whose session ID you specify
```
clear security flow session session-identifier 40000381
```
