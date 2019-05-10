+++
title = "Pat Configuration Vyatta"
date = 2018-06-22T00:43:24+05:30
tags = ["vyatta","pat"]
+++

## PAT Configuration in Vyatta
```
set nat source rule 10 outbound-interface eth0
set nat source rule 10 source address 10.29.29.0/24
set nat source rule 10 translation address masquerade
```