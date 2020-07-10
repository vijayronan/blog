
+++
title = "SSH Configuration ASA"
date = 2014-06-23T14:05:09+05:30
tags = ["asa","ssh"]
+++
## Set hostname
```
asa(config)# hostname asa1
```
## Set domain name
``asa1(config)# domain-name blog.smsid.in``
## Create RSA Key
```
asa1(config)# crypto key generate rsa modulus 1024
```
## Allow ssh from inside/ Outside 
```
asa1(config)# ssh 0.0.0.0 0.0.0.0 outside
asa1(config)# ssh 0.0.0.0 0.0.0.0 inside
```
## Create Local user account
```
asa1(config)# username admin password ******* privilege 15
```
## Local user account database to SSH AAA group
```
asa1(config)# aaa authentication ssh console LOCAL
```