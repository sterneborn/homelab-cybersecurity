# OpenWrt Network Configuration

## Router

Model: Netgear Nighthawk R7800
Firmware: OpenWrt 24.10

## VLANs

| VLAN | Purpose | Network |
|--------|----------|----------|
| 1 | Rescue | 192.168.1.0/24 |
| 10 | LAN | 192.168.10.0/24 |
| 20 | Guest | 192.168.20.0/24 |
| 30 | Lab | 192.168.30.0/24 |

## Interfaces

LAN: br-lan.10
Guest: br-lan.20
Lab: br-lan.30
Rescue: br-lan.1