+++
title = "Ubuntu Static IP Address"
date = 2014-06-22T00:34:51+05:30
tags = ["ubuntu"]
+++


## Static IP Configuration Debian & Ubuntu

### Edit :/etc/network/interfaces
```
vi /etc/network/interfaces

# The loopback interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
      address 10.29.29.61
      netmask 255.255.255.0
      network 10.29.29.0
      broadcast 10.29.29.255
      gateway 10.29.29.1
# dns-* options are implemented by the resolvconf package, if installed
      dns-nameservers 10.29.29.10

# Configuration for eth0  aliases

# This line ensures that the interface will be brought up during boot.
auto eth0:0
# eth0:0

# This is a second IP address.
iface eth0:0 inet static
    address 10.30.1.2
    netmask 255.255.255.0
```

### Restart networking:
```
/etc/init.d/networking restart
```
