# segmented-homelab-project
Secure homelab environment built in Proxmox VE using pfSense for network segmentation, firewall policy enforcement, and controlled inter-zone communication across management, internal, and DMZ networks. Includes virtual bridge-based networking and validation of access controls through SSH and connectivity testing.

## Problem Statement
To create an environment suitable for hosting my own music sever, backing up phots and other files without reliance on outside companies as well as a playground for cyber focused labs to develop skills and better understand tools that will be useful in my career. 

## Design Goals
For the basic setup of this lab/server environment I aimed to have the following: 
- Create 3 isolated virtual networks
    * management
    * internal
    * DMZ
- deploy a firewall VM to control traffic between networks
- configure firewall rules to restrict access between networks
  
## Network Diagram


## Tools used
- Ventoy
- Proxmox VE
- PfSense
- Ubuntu server iso
- Ubuntu desktop iso

## Security Reasoning
This segmented 3-network structure was chosen to reduce unnecessary communication between systems and services and mimics the common setup of corporate networks. Separating the networks limits the damage that can be done by an outfacing device that is compromised.  
The management network is reserved for administrative access, while the internal network holds trusted systems and private contents and the DMZ is intended for services that may require more limited or controlled access to the internet.

## Testing results
Source | Destination | Result
:---: | :---: | :---: 
Management | Internet | 
Management | DMZ | Allowed
Management | Internal | Allowed
DMZ | Internet | Allowed
DMZ | Internal | Blocked
DMZ | Management | Blocked
Internal | Internet | Allowed
Internal | DMZ | Allowed
Internal | Management | Blocked
Internet/WAN | Internal |
Internet/WAN | DMZ |
Internet/WAN | Management |
Internet/WAN | Firewall admin interface |
