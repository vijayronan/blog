+++
title = "Kvm and Openvswitch Ubuntu 14"
date = 2014-03-22T00:56:41+05:30
draft = false
tags = ['kvm','openvswitch','ubuntu']
+++

## Update packages
```
apt-get update && apt-get upgrade
```

## Install Packages
```
apt-get install openvswitch-switch qemu-kvm libvirt-bin
```

## Ubuntu Box has 2 NIC

eth0 - only management traffic which is connected to Cisco 3560X port number g0/44
eth1 - Traffic for VM’s(all vlans) - connected to Cisco 3560X port number g0/46


## Cisco Configuration
```
interface GigabitEthernet0/44
 description *** Connected Monitoring02 eth0 ***
 switchport access vlan 20
 switchport mode access
 spanning-tree portfast

 interface GigabitEthernet0/46
 description *** Connected Monitoring02 eth1 ***
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 21-29
 switchport mode trunk
```
## Update network configuration in ubuntu
### edit /etc/network/interfaces
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0


allow-hotplug eth0
iface eth0 inet static
        address 10.29.20.62
        netmask 255.255.255.0
        network 10.29.20.0
        broadcast 10.29.20.255
        gateway 10.29.20.1
        dns-nameservers 8.8.8.8

auto eth1
iface eth1 inet manual
```
## Openvswitch configuration
```
ovs-vsctl add-br ovs-switch          ### create bridge name
ovs-vsctl add-port ovs-switch eth1 ### add physical port to bridge

ovs-vsctl show  ### check configuration
fdae1b4b-d255-41f2-b764-c535a24f5ccc
    Bridge ovs-switch
        Port "eth1"
            Interface "eth1"
        Port ovs-switch
            Interface ovs-switch
                type: internal
    ovs_version: "2.0.2"
```
**Delete default network setting and update,
Here vlan 25, we made it as a default network**
```
cd /etc/libvirt/qemu/networks/
root@monitoring:/etc/libvirt/qemu/networks# ls
autostart  default.xml
root@monitoring:/etc/libvirt/qemu/networks# > default.xml 
```
## Edit /etc/libvirt/qemu/network/default.xml
```
<network>
  <name>default</name>
  <forward mode='bridge'/>
  <bridge name='ovs-switch'/>
  <virtualport type='openvswitch'/>
  <portgroup name='vlan-20'>
    <vlan>
      <tag id='20'/>
    </vlan>
  </portgroup>
  <portgroup name='vlan-21'>
    <vlan>
      <tag id='21'/>
    </vlan>
  </portgroup>
  <portgroup name='vlan-22'>
    <vlan>
      <tag id='22'/>
    </vlan>
  </portgroup>
  <portgroup name='vlan-23'>
    <vlan>
      <tag id='23'/>
    </vlan>
  </portgroup>
  <portgroup name='vlan-24'>
    <vlan>
      <tag id='24'/>
    </vlan>
  </portgroup>

  <portgroup name='vlan-25' default='yes'>
    <vlan>
      <tag id='25'/>
    </vlan>
  </portgroup>

  <portgroup name='vlan-26'>
    <vlan>
      <tag id='26'/>
    </vlan>
  </portgroup>
  <portgroup name='vlan-27'>
    <vlan>
      <tag id='27'/>
    </vlan>
  </portgroup>
  <portgroup name='vlan-28'>
    <vlan>
      <tag id='28'/>
    </vlan>
  </portgroup>
  <portgroup name='vlan-29'>
    <vlan>
      <tag id='29'/>
    </vlan>
  </portgroup>
</network>
```
## Restart libvirt-bin
```
/etc/init.d/libvirt-bin restart 
```


## Finally reboot the ubuntu box

## VM Guest install
```
virt-install \
--name debian7 \
--ram 1024 \
--disk path=./debian7.img,bus=virtio,size=15 \
--vcpus 2 \
--os-type linux \
--os-variant debianwheezy \
--graphics none \
--console pty,target_type=serial \
--location 'http://ftp.us.debian.org/debian/dists/wheezy/main/installer-amd64/' \
--extra-args 'console=ttyS0,115200n8 serial'
```
