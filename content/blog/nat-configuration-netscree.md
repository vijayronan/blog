
+++
title = "NAT Configuration  Netscreen"
date = 2018-06-23T13:32:42+05:30
tags = ["natscreen","nat"]
+++

```
set interface "<INTERFACE_NAME>" mip <PUBLIC_IP> host <PRIVATE_IP> netmask 255.255.255.255 vr "trust-vr"
set policy id 200 from "Untrust" to "Trust" "Any-IPv4" "MIP(<PUBLIC_IP>)" "ANY" permit log
```
