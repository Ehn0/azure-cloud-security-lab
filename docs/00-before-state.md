# Before: the original setup

## What existed
- One Windows Server VM (vm-winsvr-01) built with the Azure VM wizard
- Its own VNet: address space 10.0.0.0/16
- one subnet default (10.0.0.0/24)
- NSG inbound rules:
- NSG attached to the VM's NIC, not the subnet
- One custom inbound rule: RDP (3389/TCP) allowed from a single IP
- VM has a public IP, so it's reachable from the internet at the network level
- A public IP attached directly to the VM

## Problems with this design
- The VM is reachable from the internet
- One flat network with no separation between workloads
- Nothing centralized for security or access

## What I'm changing
Rebuilding as hub-and-spoke with Bastion, so no VM has a public IP.

## What I did
Deleted the flat setup and rebuilt as hub-and-spoke with Bastion,
so no VM has a public IP.
