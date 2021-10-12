# Home Lab (Write up in progress)
I've setup a custom network configuration at home for defence-in-depth as an experiment and learning experience. I'm using Ubiquitous networking equipment to manage the network with multiple access points across multiple floors. I have created multiple virtual local area networks (VLAN) to personal devices, guest devices and Internet of Things (IoT) devices. Next I've created firewall rules to segregate the VLANs from each other with some exceptions made for personal devices to be able to access IoT devices. I've also setup a honeypot running on the IoT network as another layer of defence.

On the monitoring side I have a virtual machine running Security Onion with all network traffic being mirrored to it as well as information from Wazuh EDR running on hosts.

In addition to this configuration I have some extra elements setup for various things such as a L2VPN, Nextcloud storage, Plex Media Server, Pihole and DNSCrypt.

More details are listed below.

## Table of Contents
- Network Topology
- Network Hardware
- Network Configuration
- Unraid Server

-----

### Network Topology
-----

![Network Topology]()

### Networking Hardware
-----
- Unifi Security Gateway
- 2x Unifi POE Switch 
- 3x Unifi Access Points
- Unifi Cloudkey
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
There is a wireless network configured for each VLAN. Seamless roaming between multiple access points was setup with RSSI tuning (Received Signal Strength Indication).

#### Firewall Configuration
My network is setup to isolate all IoT devices on their own VLAN for added security. Clients on the IoT VLAN are unable to start connections across other VLANs but Private/Guest are able to start connections with IoT. Additional rules were required to allow specific connections from IoT to Private/Guest to allow for smart device functionality (ie. speakers, lights and other home automation).

The following rules are in place:

![Screenshot of firewall rules]() 



### Unraid Server
-----

Main server hosting multiple services via virutal machines and containers. Virtual machines supported by Linux Kernal Virtual Machine (KVM) and containers supported by Docker.


