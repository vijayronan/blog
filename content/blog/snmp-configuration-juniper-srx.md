+++
title =  "SNMP Configuration Juniper SRX"
date =  2018-06-26T23:50:47+05:30
tags  =  ["srx","snmp"]
+++

## Allow SNMP service from Security Zone
```
set security zones security-zone trust host-inbound-traffic system-services snmp
```

## Set snap community and Allowed clients
```
set snmp community ZIodZHut3jTjHRiYBzpg authorization read-only
set snmp community ZIodZHut3jTjHRiYBzpg clients 10.11.50.137/32
```
