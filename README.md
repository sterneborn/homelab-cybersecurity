# Cybersecurity Homelab

A personal cybersecurity and networking homelab built to develop practical skills in networking, Linux administration, virtualization, monitoring, and defensive security.

This repository documents the design, implementation, troubleshooting, and continuous improvement of my home lab environment.

---

## Objectives

The primary goals of this project are:

* Develop strong networking fundamentals
* Learn Linux system administration
* Gain hands-on cybersecurity experience
* Build practical troubleshooting skills
* Learn virtualization and infrastructure management
* Create a documented portfolio demonstrating technical growth

---

## Current Environment

### Network Infrastructure

* Netgear R7800 Router
* OpenWrt 24.10
* Cloudflare DNS & Dynamic DNS
* WireGuard VPN

### Network Segmentation

| VLAN    | Purpose         | Network         |
| ------- | --------------- | --------------- |
| VLAN 10 | Trusted LAN     | 192.168.10.0/24 |
| VLAN 20 | Guest Network   | 192.168.20.0/24 |
| VLAN 30 | Lab Environment | 192.168.30.0/24 |

### Remote Access

WireGuard VPN provides secure remote access to the lab environment.

VPN Network:

```text
10.100.100.0/24
```

---

## Hardware

### Router

* Netgear R7800
* OpenWrt 24.10

### Server

* Fujitsu Esprimo Q7010
* Intel Core i5-10400T
* 32 GB RAM
* 256 GB NVMe SSD
* 1 TB External SSD

---

## Technologies Used

### Networking

* OpenWrt
* VLANs
* DHCP
* DNS
* WireGuard
* Cloudflare DDNS

### Operating Systems

* Linux
* OpenWrt

### Security

* Network Segmentation
* Firewall Zones
* VPN Remote Access

### Planned Technologies

* Proxmox
* Docker
* Grafana
* Prometheus
* Security Onion
* IDS/IPS
* Centralized Logging

---

## Documentation

Detailed documentation can be found in the `/docs` directory.

### Available Documentation

* Network Overview
* OpenWrt Configuration
* VLAN Design
* WireGuard Deployment
* Cloudflare DDNS
* Troubleshooting Notes
* Learning Methodology

---

## Troubleshooting Philosophy

A structured troubleshooting methodology is used throughout the project:

1. Identify the problem
2. Collect relevant information
3. Form hypotheses
4. Test and verify
5. Document findings
6. Implement solutions
7. Record lessons learned

---

## Use of AI

AI tools are used as learning, research, documentation, and troubleshooting assistants.

All recommendations are independently verified through testing, log analysis, validation, and documentation before implementation.

Core principle:

> Trust, but verify.

---

## Roadmap

### Phase 1 - Network Foundation

* [x] OpenWrt Deployment
* [x] VLAN Segmentation
* [x] Firewall Configuration
* [x] WireGuard VPN
* [x] Cloudflare Dynamic DNS

### Phase 2 - Virtualization

* [ ] Proxmox Installation
* [ ] Virtual Machine Deployment
* [ ] Network Integration

### Phase 3 - Monitoring

* [ ] Grafana
* [ ] Prometheus
* [ ] System Metrics
* [ ] Network Monitoring

### Phase 4 - Security Operations

* [ ] Security Onion
* [ ] IDS/IPS
* [ ] Log Analysis
* [ ] Incident Detection

---

## Learning Journey

This repository serves as both a technical lab and a record of my progress as I transition into networking and cybersecurity.

The focus is not only on building infrastructure, but also on developing the ability to design, troubleshoot, secure, and document real-world systems.
