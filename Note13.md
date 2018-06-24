# Linux 
# Basic networking 
---
## Network interfaces

Network interfaces are a connection channel between a _device_ and a _network_. Physically, network interfaces can proceed through a _network interface card_ (NIC) or can be more abstractly implemented as software. 

Specific interfaces can be _brought up_ (activated) or _brought down_ (de-activated) at __any time__.
A list of currently active network interfaces is reported by the ifconfig utility.

The ip is a very powerful program that can do many things.
```
$ ip addr show
$ ip route show

```

## Routing table
The route command is used to view or change the IP routing table. You may want to change the IP routing table to add, delete or modify static routes to specific hosts or networks.

Show route table: 
```
aa32007@a32007:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0b1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0b1
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0b1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
```
Add IP route table:
```
$ route add 10.58.47.235
```
Delete route table: 
```
$ route delete 10.58.47.235 
```
