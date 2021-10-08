# Home Lab (Work in progress)
I've setup a custom network configuration at home as both a learning project as well as for security. Listed below are the configurations and features that I've implemented.

## Table of Contents
- Network Topology
- Network Hardware
- Network Configuration
- Unraid Server


### Network Topology
-----

![Network Topology]()

### Networking Hardware
-----
- Unifi Security Gateway
- 2x Unifi POE Switch 
- 3x Unifi Access Points
- Unraid Server

### Network Configuration
-----

#### Virtual Local Area Networks (VLANs)
The following VLANs are configured on the network.

![VLANS]()

- Private: Network equipment, Unraid server, Personal devices
- IoT (Internet of Things): All IoT devices such as thermostats, fire alarms, speakers, TVs, Nanoleafs, smart lights
- Guest: Guest network

#### Wireless Networks

- Private
- IoT
- Guest

#### Wireless Access Points
Seamless roaming for all wireless networks achieved

#### Firewall Configuration
My network is setup to isolate all IoT devices on their own VLAN for added security. Clients on the IoT VLAN are unable to start connections across other VLANs but Private/Guest are able to start connections with IoT. Additional rules were required to allow specific connections from IoT to Private/Guest to allow for smart device functionality (ie. speakers, lights and other home automation).

The following rules are in place:

![Screenshot of firewall rules]() 



### Unraid Server
-----

Main server hosting multiple services via virutal machines and containers. Virtual machines supported by Linux Kernal Virtual Machine (KVM) and containers supported by Docker.


