# 01: VNets and address plan

## Goal
Create a hub VNet and two spoke VNets (prod, dev) with
non-overlapping address spaces, so they can be peered later.

## Address plan
| VNet      | Address space | Subnets                                             |
|-----------|---------------|-----------------------------------------------------|
| vnet-hub  | 10.0.0.0/16   | AzureBastionSubnet 10.0.1.0/26, snet-mgmt 10.0.2.0/24 |
| vnet-prod | 10.1.0.0/16   | snet-web 10.1.1.0/24, snet-db 10.1.2.0/24, snet-pe 10.1.3.0/24 |
| vnet-dev  | 10.2.0.0/16   | snet-dev 10.2.1.0/24                                |

## Why these choices
- Non-overlapping ranges: VNets with overlapping address spaces can't be peered.
- Hub holds shared services only (Bastion); workloads live in spokes.
- AzureBastionSubnet is /26 because Bastion requires at least that size.
- Separate web, db, and private endpoint subnets so each gets its own NSG rules.

## What I verified
- Available IPs per subnet matched the math (size minus Azure's 5 reserved)
- (screenshot of each VNet's Subnets blade)

## What I learned



## Screen Shots

<img width="1888" height="819" alt="image" src="https://github.com/user-attachments/assets/5beb0061-7811-44e6-b4b4-abfb62ef14c4" />
