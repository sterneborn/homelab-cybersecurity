# Network Overview

## Status

**Operating — UniFi-based architecture with five segmented networks.**

![Current UniFi homelab network topology](assets/network-topology.svg)

The UniFi Cloud Gateway Ultra is the current gateway, router, and firewall. A UniFi U7 Lite provides managed wireless access, while zone-based policy controls traffic between networks.

## Current Topology

```text
Internet
   |
UniFi Cloud Gateway Ultra
   |
Zone-based firewall policies
   |-- VLAN 10  Trusted
   |-- VLAN 20  Guest
   |-- VLAN 30  Lab / Servers
   |      |-- Proxmox, VMs and containers
   |      |-- Home Assistant, n8n and core services
   |      `-- Prometheus, Grafana and monitoring
   |-- VLAN 40  IoT
   `-- VLAN 50  Remote Access
          `-- Debian LXC Twingate Connector
```

## Remote Access Architecture

Two separate access models are maintained:

* **Twingate** provides identity- and resource-based access through a dedicated Connector. The Connector initiates outbound connections and does not require inbound port forwarding.
* **WireGuard** provides an established tunnel- and routing-based VPN path for use cases that need that network model.

The Twingate path is:

```text
Remote client
    |
Twingate service
    |
Outbound Connector tunnel
    |
Debian LXC Connector — VLAN 50
    |
UniFi zone-based policy
    |
Approved Resource — for example in VLAN 30
    |
Optional host firewall restrictions
```

Remote clients do not receive an address in VLAN 50. That VLAN is the Connector's security segment. The protected resource can remain in VLAN 30 because the Connector uses normal routing plus explicit UniFi policy to reach it; host firewalls can then restrict the allowed service.

## Segmentation Intent

| VLAN | Name | Policy intent |
| ---: | --- | --- |
| 10 | Trusted | Controlled access to approved services |
| 20 | Guest | Internet only |
| 30 | Lab / Servers | Explicitly exposed infrastructure services |
| 40 | IoT | Isolation with required integration exceptions |
| 50 | Remote Access | Connector-only segment with explicit access to approved Resources |

Policy is deliberately layered. A successful route is not by itself authorization to every destination or service.

## Operational Visibility

* Prometheus collects host and service metrics, including Node Exporter data.
* Grafana visualizes operational trends and supports troubleshooting.
* Uptime Kuma provides availability-oriented service checks.
* SmokePing adds latency and packet-loss visibility.

These views complement one another and help locate problems across the network, host, and application layers.

## Related Documentation

* [UniFi Network](Network/UniFi.md)
* [VLAN Segmentation](Network/VLANs.md)
* [Twingate Zero Trust Access](Network/Twingate.md)
* [WireGuard Remote Access](Network/WireGuard.md)
* [Security Practices](Security/Security-Practices.md)
* [OpenWrt — Previous Architecture](Network/OpenWrt.md)
