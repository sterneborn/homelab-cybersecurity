# Christian Sterneborn

## Network, Infrastructure & Cybersecurity Homelab

Welcome to the technical documentation for my current homelab and project portfolio.

The environment is built for hands-on learning across networking, virtualization, Linux, self-hosted services, automation, smart-home infrastructure, and cybersecurity. The documentation records both the current architecture and the earlier systems that shaped it.

---

# Current Homelab

## Network

* UniFi Cloud Gateway Ultra
* UniFi-managed Wi-Fi and access point
* Trusted, Guest, Lab/Servers, and IoT VLANs
* Zone-based firewall policies
* WireGuard remote access
* Tailscale under evaluation

## Virtualization and Services

* Proxmox VE
* Home Assistant
* Docker and Portainer
* AdGuard Home
* Uptime Kuma

## Custom Projects

* **Knut** — a major custom AI and automation project
* **Borgen Audio** — Raspberry Pi 4 audio appliance with a Raspberry Pi DAC Pro, Shairport Sync, and BlueALSA
* **Zigbee2MQTT architecture** — planned coordinator, MQTT, and Home Assistant integration

---

# Architecture Evolution

The network began with a Netgear R7800 running OpenWrt. That platform was used to learn VLAN configuration, firewall zones, WireGuard, dynamic DNS, Wi-Fi troubleshooting, and evidence-based network diagnostics.

The current architecture has migrated to UniFi. A UniFi Cloud Gateway Ultra now provides gateway and firewall functions, and a UniFi-managed access point provides centrally managed Wi-Fi. OpenWrt remains documented as an earlier architecture rather than being erased from the project history.

* [Current UniFi Network](Network/UniFi.md)
* [Previous OpenWrt Architecture](Network/OpenWrt.md)
* [Project Journal](Project-Journal.md)

---

# Skills Demonstrated

## Networking and Security

* UniFi gateway and wireless administration
* VLAN design and segmentation
* Zone-based firewall policy design
* DNS and DHCP integration
* WireGuard deployment and troubleshooting
* Network migration and validation

## Linux and Infrastructure

* Proxmox virtualization
* Ubuntu Server administration
* Docker deployment and Portainer operations
* Backup and recovery planning
* `systemd`, ALSA, and BlueZ troubleshooting

## Services and Automation

* Home Assistant
* AdGuard Home
* Uptime Kuma
* AI-assisted workflow and automation design through Knut
* Planned Zigbee2MQTT and MQTT integration

## Engineering Practice

* Structured troubleshooting
* Technical documentation
* Change tracking and project journaling
* Git and GitHub workflows
* Incremental testing and verification

---

# Current Documentation

## Network

* [Network Overview](Network-Overview.md)
* [UniFi Network](Network/UniFi.md)
* [VLAN Segmentation](Network/VLANs.md)
* [WireGuard Remote Access](Network/WireGuard.md)
* [Cloudflare DDNS](Network/Cloudflare-DDNS.md)
* [OpenWrt — Previous Architecture](Network/OpenWrt.md)

## Virtualization

* [Proxmox](Virtualization/Proxmox.md)
* [Virtual Networking](Virtualization/Virtual-Networking.md)
* [Backup Strategy](Virtualization/Backup-Strategy.md)

## Services

* [Home Assistant](Services/Home-Assistant.md)
* [Docker](Services/Docker.md)
* [Portainer](Services/Portainer.md)
* [AdGuard Home](Services/AdGuard-Home.md)
* [Uptime Kuma](Services/Uptime-Kuma.md)
* [Prometheus](Services/Prometheus.md)
* [Grafana](Services/Grafana.md)
* [Alerting](Services/Alerting.md)

## Projects

* [Knut AI & Automation](Projects/Knut.md)
* [Borgen Audio](Projects/Borgen-Audio.md)
* [Planned Zigbee2MQTT Architecture](Projects/Zigbee2MQTT.md)

## Security and Career

* [Security Onion](Security/Security-Onion.md)
* [Suricata](Security/Suricata.md)
* [Log Analysis](Security/Log-Analysis.md)
* [Career Journey](Career/Career-Journey.md)
* [Learning Methodology](Career/Learning-Methodology.md)

---

# Learning Philosophy

The best way to learn technology is through practical implementation, structured troubleshooting, validation, and documentation. This repository intentionally records both working systems and the migration history behind them.

---

# Contact

[GitHub](https://github.com/sterneborn)
