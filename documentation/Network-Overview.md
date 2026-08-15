# Homelab Network Overview

## Current Architecture

The current network is built around a **UniFi Cloud Gateway Ultra** with a **UniFi-managed access point**. The gateway provides routing, VLANs, and zone-based firewall policy, while UniFi-managed Wi-Fi maps wireless clients into the appropriate trust zone.

The design supports the wider homelab: Proxmox virtualization, containerized services, Home Assistant, DNS filtering, monitoring, remote access, and future Zigbee integration.

---

## Architecture at a Glance

```text
Internet
   |
UniFi Cloud Gateway Ultra
   |
   +-- UniFi-managed Wi-Fi / access point
   |
   +-- Trusted VLAN
   +-- Guest VLAN
   +-- Lab/Servers VLAN
   |      +-- Proxmox
   |      +-- Docker / Portainer
   |      +-- AdGuard Home
   |      +-- Uptime Kuma
   |      +-- Home Assistant integrations
   |
   +-- IoT VLAN
          +-- Smart-home and connected devices
          +-- Planned Zigbee2MQTT environment
```

WireGuard provides remote access. Tailscale is currently being evaluated as a complementary option and is not documented as a replacement.

---

## Network Segments

| Segment | Primary role | Policy intent |
| ------- | ------------ | ------------- |
| Trusted | Personal and administrative clients | Controlled access to required infrastructure services |
| Guest | Visitor and temporary clients | Internet access without access to private networks |
| Lab/Servers | Proxmox, VMs, containers, and infrastructure services | Explicit service exposure and restricted inter-zone access |
| IoT | Smart-home and lower-trust devices | Isolation with only required integration traffic allowed |

See [VLAN Segmentation](Network/VLANs.md) for more detail.

---

## Core Infrastructure

### Gateway and Wi-Fi

* UniFi Cloud Gateway Ultra
* UniFi-managed access point
* Centralized network and wireless management
* Zone-based firewall policies

### Virtualization

* Fujitsu Esprimo Q7010
* Intel Core i5-10400T
* 32 GB RAM
* 256 GB NVMe SSD
* 1 TB external SSD
* Proxmox VE

### Services and Projects

* Home Assistant
* Docker and Portainer
* AdGuard Home
* Uptime Kuma
* Knut AI and automation
* Borgen Audio on Raspberry Pi 4
* Planned Zigbee coordinator and Zigbee2MQTT

---

## Architecture History

The previous network used a Netgear R7800 running OpenWrt. It established the first segmented design and provided practical experience with VLANs, firewall zones, WireGuard, Cloudflare DDNS, and Wi-Fi troubleshooting.

That design was later migrated to UniFi. The original topology diagram and configuration notes remain in the [OpenWrt history](Network/OpenWrt.md) so the repository continues to show the evolution of the lab.

---

## Related Documentation

* [UniFi Network](Network/UniFi.md)
* [VLAN Segmentation](Network/VLANs.md)
* [WireGuard Remote Access](Network/WireGuard.md)
* [OpenWrt — Previous Architecture](Network/OpenWrt.md)
