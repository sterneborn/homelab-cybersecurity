# Cybersecurity Homelab Documentation

This documentation records an active, structured homelab used to build practical experience in IT support, networking, Linux, infrastructure operations, automation, and cybersecurity. It focuses on what is running, how the parts connect, how changes are validated, and what was learned during troubleshooting.

!!! success "Current environment"
    UniFi networking, five VLAN segments, Twingate and WireGuard remote access, Proxmox virtualization, core self-hosted services, and the Prometheus/Grafana monitoring stack are operating now.

## Current Architecture

![Current UniFi homelab topology with five VLANs and two remote-access paths](assets/network-topology.svg)

The UniFi Cloud Gateway Ultra provides routing and zone-based policy for five networks:

| VLAN | Name | Primary role |
| ---: | --- | --- |
| 10 | Trusted | Personal and administrative clients |
| 20 | Guest | Internet-only visitor access |
| 30 | Lab / Servers | Proxmox, virtual machines, containers, and services |
| 40 | IoT | Smart-home and lower-trust devices |
| 50 | Remote Access | Dedicated Twingate Connector infrastructure |

Twingate provides resource-based Zero Trust access through an outbound-only Connector in a Debian LXC. WireGuard remains a separate, established tunnel- and routing-based VPN path. Remote Twingate clients do not join VLAN 50.

## Operating Platforms and Services

* **Networking:** UniFi Cloud Gateway Ultra, UniFi U7 Lite, VLAN segmentation, and zone-based firewall policy
* **Virtualization:** Proxmox VE, Ubuntu Server, and Debian LXC workloads
* **Containers:** Docker and Portainer
* **Core services:** Home Assistant, AdGuard Home, and n8n
* **Monitoring:** Prometheus, Node Exporter, Grafana, Uptime Kuma, and SmokePing
* **Remote access:** Twingate and WireGuard, used as distinct access models
* **Custom work:** Knut AI and automation, plus Borgen Audio

## Working Method

The repository demonstrates four habits relevant to support and junior infrastructure roles:

1. **Structured troubleshooting** across client, network, host, and application layers.
2. **Clear documentation** of architecture, changes, evidence, and outcomes.
3. **Secure-by-default design** using segmentation and explicit exceptions.
4. **Practical operations** including monitoring, maintenance, backup, and recovery validation.

## Security Practices

Network segmentation, zone-based firewall rules, host-level UFW controls, Connector isolation, least-privilege access exceptions, screenshot redaction, and secret handling are documented in [Security Practices](Security/Security-Practices.md).

Credential hygiene uses Bitwarden-based password management, unique credentials, and careful handling of secrets outside the public repository. Bitwarden is a working practice rather than a standalone infrastructure project.

## Documentation Map

### Network

* [Network Overview](Network-Overview.md)
* [UniFi Network](Network/UniFi.md)
* [VLAN Segmentation](Network/VLANs.md)
* [Twingate Zero Trust Access](Network/Twingate.md)
* [WireGuard Remote Access](Network/WireGuard.md)
* [Cloudflare DDNS](Network/Cloudflare-DDNS.md)
* [OpenWrt — Previous Architecture](Network/OpenWrt.md)

### Virtualization and Services

* [Proxmox VE](Virtualization/Proxmox.md)
* [Virtual Networking](Virtualization/Virtual-Networking.md)
* [Backup Strategy](Virtualization/Backup-Strategy.md)
* [Docker](Services/Docker.md) and [Portainer](Services/Portainer.md)
* [Home Assistant](Services/Home-Assistant.md) and [AdGuard Home](Services/AdGuard-Home.md)
* [Uptime Kuma](Services/Uptime-Kuma.md), [Prometheus](Services/Prometheus.md), and [Grafana](Services/Grafana.md)
* [Alerting — Planned / In Progress](Services/Alerting.md)

### Projects and Security Learning

* [Knut AI & Automation](Projects/Knut.md)
* [Borgen Audio](Projects/Borgen-Audio.md)
* [Planned Zigbee2MQTT Architecture](Projects/Zigbee2MQTT.md)
* [Security Onion — Planned](Security/Security-Onion.md)
* [Suricata — Planned](Security/Suricata.md)
* [Log Analysis — Planned](Security/Log-Analysis.md)

## Architecture History

The original segmented network used OpenWrt. Its diagrams and screenshots remain available as clearly labelled historical evidence. They are not presented as current UniFi configuration.

## Portfolio Relevance

This project supports roles such as IT Support Technician, IT Technician, Service Desk, NOC Technician, and junior network, infrastructure, or cybersecurity operations positions. It demonstrates a practical ability to build, operate, troubleshoot, verify, and explain working technical systems.
