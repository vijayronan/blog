
+++
title = "NAT Configuration ASA"
date = 2018-06-23T13:38:12+05:30
tags = ["asa","nat"]
+++

## Static NAT
```
object network host-10.29.29.33 
host 10.29.29.33 
nat (dmz,outside) static 103.252.X.X 
access-list outside-inside extended permit ip any object host-10.29.29.33 
```
## Source NAT
```
object network net-10.29.0.0 
nat (any,outside) dynamic interface 
object network host-10.29.20.62 
```
