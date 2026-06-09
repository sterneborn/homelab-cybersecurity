# Cybersecurity Homelab

![Status](https://img.shields.io/badge/Status-Active-green)
![OpenWrt](https://img.shields.io/badge/OpenWrt-24.10-blue)
![WireGuard](https://img.shields.io/badge/VPN-WireGuard-orange)
![Cloudflare](https://img.shields.io/badge/DDNS-Cloudflare-yellow)

A personal cybersecurity and networking homelab built to develop practical skills in networking, Linux administration, virtualization, monitoring, and defensive security.

This repository documents the design, implementation, troubleshooting, and continuous improvement of my home lab environment.

---

# Network Topology

![Network Topology](diagrams/network-topology.png)

---

# Objectives

The primary goals of this project are:

* Develop strong networking fundamentals
* Learn Linux system administration
* Gain hands-on cybersecurity experience
* Build practical troubleshooting skills
* Learn virtualization and infrastructure management
* Create a documented portfolio demonstrating technical growth

---

# Current Environment

## Network Infrastructure

* Netgear R7800 Router
* OpenWrt 24.10
* Cloudflare DNS & Dynamic DNS
* WireGuard VPN

## Network Segmentation

| VLAN    | Purpose         | Network         |
| ------- | --------------- | --------------- |
| VLAN 1  | Rescue Network  | 192.168.1.0/24  |
| VLAN 10 | Trusted LAN     | 192.168.10.0/24 |
| VLAN 20 | Guest Network   | 192.168.20.0/24 |
| VLAN 30 | Lab Environment | 192.168.30.0/24 |

## Remote Access

WireGuard VPN provides secure remote access to the lab environment.

VPN Network:

```text
10.100.100.0/24
```

---

# Hardware

## Router

* Netgear R7800
* OpenWrt 24.10

## Server

* Fujitsu Esprimo Q7010
* Intel Core i5-10400T
* 32 GB RAM
* 256 GB NVMe SSD
* 1 TB External SSD

---

# Technologies Used

## Networking

* OpenWrt
* VLANs
* DHCP
* DNS
* WireGuard
* Cloudflare DDNS

## Operating Systems

* Linux
* OpenWrt

## Security

* Network Segmentation
* Firewall Zones
* VPN Remote Access

## Planned Technologies

* Proxmox
* Docker
* Grafana
* Prometheus
* Security Onion
* IDS/IPS
* Centralized Logging

---

# Documentation

Detailed documentation can be found in the `/docs` directory.

## Networking

* [Network Overview](docs/00-Network-Overview.md)
* [OpenWrt Configuration](docs/01-OpenWrt.md)
* [VLAN Design](docs/02-VLANs.md)
* [WireGuard Deployment](docs/03-WireGuard.md)
* [Cloudflare DDNS](docs/04-Cloudflare-DDNS.md)

## Virtualization

* [Proxmox](docs/10-Proxmox.md)
* [Virtual Networking](docs/11-Virtual-Networking.md)
* [Backup Strategy](docs/12-Backup-Strategy.md)

## Containers

* [Docker](docs/20-Docker.md)
* [AdGuard Home](docs/21-AdGuard-Home.md)

## Monitoring

* [Prometheus](docs/30-Prometheus.md)
* [Grafana](docs/31-Grafana.md)
* [Alerting](docs/32-Alerting.md)

## Security Operations

* [Security Onion](docs/40-Security-Onion.md)
* [Suricata](docs/41-Suricata.md)
* [Log Analysis](docs/42-Log-Analysis.md)

## Learning & Project Tracking

* [Learning Methodology](docs/99-Learning-Methodology.md)
* [Project Journal](docs/Project-Journal.md)

---

# Troubleshooting Philosophy

A structured troubleshooting methodology is used throughout the project:

1. Identify the problem
2. Collect relevant information
3. Form hypotheses
4. Test and verify
5. Document findings
6. Implement solutions
7. Record lessons learned

This repository intentionally documents both successful implementations and troubleshooting processes.

---

# Use of AI

AI tools are used as learning, research, documentation, and troubleshooting assistants.

All recommendations are independently verified through testing, log analysis, validation, and documentation before implementation.

Core principle:

> Trust, but verify.

---

# Roadmap

## Phase 1 - Network Foundation

* [x] OpenWrt Deployment
* [x] VLAN Segmentation
* [x] Firewall Configuration
* [x] WireGuard VPN
* [x] Cloudflare Dynamic DNS

## Phase 2 - Virtualization

* [ ] Proxmox Installation
* [ ] Virtual Machine Deployment
* [ ] Virtual Network Design

## Phase 3 - Monitoring

* [ ] Grafana
* [ ] Prometheus
* [ ] System Metrics
* [ ] Network Monitoring

## Phase 4 - Security Operations

* [ ] Security Onion
* [ ] IDS/IPS
* [ ] Log Analysis
* [ ] Incident Detection

---

# Learning Journey

This repository serves as both a technical lab and a record of my progress as I transition into networking and cybersecurity.

The focus is not only on building infrastructure, but also on developing the ability to design, troubleshoot, secure, and document real-world systems.

---

# Author

**Christian Sterneborn**

Aspiring Network & Cybersecurity Professional

GitHub: https://github.com/sterneborn
