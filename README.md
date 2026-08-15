# Cybersecurity Homelab

![Status](https://img.shields.io/badge/Status-Active-green)
![Gateway](https://img.shields.io/badge/Gateway-UniFi%20Cloud%20Gateway%20Ultra-blue)
![VPN](https://img.shields.io/badge/VPN-WireGuard-orange)
![Virtualization](https://img.shields.io/badge/Virtualization-Proxmox-E57000)

A personal networking, infrastructure, automation, and cybersecurity homelab built for practical learning through implementation, troubleshooting, validation, and documentation.

The current environment is based on UniFi networking and Proxmox virtualization. The repository also preserves the earlier OpenWrt architecture as part of the project's technical history.

## Current Environment

### Network

* UniFi Cloud Gateway Ultra
* UniFi-managed Wi-Fi and access point
* Trusted, Guest, Lab/Servers, and IoT VLANs
* Zone-based firewall policies
* WireGuard remote access
* Tailscale under evaluation

### Virtualization and Services

* Proxmox VE
* Ubuntu Server
* Home Assistant
* Docker and Portainer
* AdGuard Home
* Uptime Kuma

### Custom Projects

* **Knut** — a major custom AI and automation project
* **Borgen Audio** — Raspberry Pi 4 with Raspberry Pi DAC Pro, AirPlay through Shairport Sync, and Android Bluetooth audio through BlueALSA
* **Zigbee2MQTT** — planned Zigbee coordinator, MQTT broker, and Home Assistant architecture

## Network Segmentation

| Network | Purpose |
| ------- | ------- |
| Trusted | Personal and administrative devices |
| Guest | Isolated visitor access |
| Lab/Servers | Proxmox, VMs, containers, and infrastructure services |
| IoT | Smart-home and lower-trust devices |

Inter-network access is controlled with zone-based firewall policies and explicit exceptions for required services.

## Hardware

### Network

* UniFi Cloud Gateway Ultra
* UniFi-managed access point

### Virtualization Server

* Fujitsu Esprimo Q7010
* Intel Core i5-10400T
* 32 GB RAM
* 256 GB NVMe SSD
* 1 TB external SSD

### Audio Project

* Raspberry Pi 4
* Raspberry Pi DAC Pro

## Architecture History

The first segmented homelab network ran on a Netgear R7800 with OpenWrt 24.10. It provided hands-on experience with VLANs, firewall zones, WireGuard, Cloudflare Dynamic DNS, DHCP/DNS integration, Wi-Fi configuration, and systematic network troubleshooting.

That architecture was later migrated to UniFi. The old topology, screenshots, configuration notes, and project journal entries remain in the repository as evidence of the earlier implementation and the learning that informed the current design.

![Previous OpenWrt Network Topology](diagrams/network-topology.png)

## Documentation

The MkDocs source lives in [`documentation/`](documentation/), and generated site output is written to [`docs/`](docs/).

### Network

* [Network Overview](documentation/Network-Overview.md)
* [UniFi Network](documentation/Network/UniFi.md)
* [VLAN Segmentation](documentation/Network/VLANs.md)
* [WireGuard Remote Access](documentation/Network/WireGuard.md)
* [Cloudflare DDNS](documentation/Network/Cloudflare-DDNS.md)
* [OpenWrt — Previous Architecture](documentation/Network/OpenWrt.md)

### Virtualization

* [Proxmox](documentation/Virtualization/Proxmox.md)
* [Virtual Networking](documentation/Virtualization/Virtual-Networking.md)
* [Backup Strategy](documentation/Virtualization/Backup-Strategy.md)

### Services

* [Home Assistant](documentation/Services/Home-Assistant.md)
* [Docker](documentation/Services/Docker.md)
* [Portainer](documentation/Services/Portainer.md)
* [AdGuard Home](documentation/Services/AdGuard-Home.md)
* [Uptime Kuma](documentation/Services/Uptime-Kuma.md)

### Projects

* [Knut AI & Automation](documentation/Projects/Knut.md)
* [Borgen Audio](documentation/Projects/Borgen-Audio.md)
* [Planned Zigbee2MQTT Architecture](documentation/Projects/Zigbee2MQTT.md)

### Project Tracking

* [Project Journal](documentation/Project-Journal.md)
* [Learning Methodology](documentation/Career/Learning-Methodology.md)

## Troubleshooting Philosophy

1. Identify the problem.
2. Collect relevant information.
3. Form testable hypotheses.
4. Test and verify each layer.
5. Implement the solution.
6. Record the result and lessons learned.

This repository intentionally documents both successful implementations and the troubleshooting processes behind them.

## Roadmap

### Operating

* [x] UniFi gateway and managed Wi-Fi
* [x] Trusted, Guest, Lab/Servers, and IoT segmentation
* [x] Zone-based firewall policy
* [x] WireGuard remote access
* [x] Proxmox virtualization
* [x] Docker and Portainer
* [x] Home Assistant
* [x] AdGuard Home and Uptime Kuma
* [x] Knut and Borgen Audio projects

### Evaluating and Planned

* [ ] Complete Tailscale evaluation
* [ ] Deploy Zigbee coordinator and Zigbee2MQTT architecture
* [ ] Expand Prometheus, Grafana, and alerting
* [ ] Continue Security Onion, Suricata, and log-analysis work

## Author

**Christian Sterneborn**

Aspiring Network & Cybersecurity Professional

[GitHub](https://github.com/sterneborn)
