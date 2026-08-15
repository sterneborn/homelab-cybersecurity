# VLAN Segmentation

## Status

**Current design on UniFi**

The homelab uses VLANs to separate devices and services by role and trust level. Routing and policy enforcement are handled by the UniFi Cloud Gateway Ultra through zone-based firewall policies.

---

## VLAN Overview

| Network | Purpose | Examples |
| ------- | ------- | -------- |
| Trusted | Personal and administrative devices | Workstations, phones, and management clients |
| Guest | Visitor and temporary devices | Guest Wi-Fi clients |
| Lab/Servers | Infrastructure and test workloads | Proxmox, VMs, Docker, and self-hosted services |
| IoT | Smart-home and lower-trust devices | Connected devices and future Zigbee integrations |

VLAN identifiers and addressing are intentionally kept out of this public overview. The design focus is the trust boundary and the policy applied between segments.

---

## Zone-Based Firewall Model

The firewall starts from isolation between zones. Cross-zone communication is enabled only when a documented service or administrative workflow requires it.

| Source zone | Policy intent |
| ----------- | ------------- |
| Trusted | Permit required administration and service access; avoid unrestricted access where it is unnecessary |
| Guest | Internet access only; block access to private networks |
| Lab/Servers | Allow required outbound traffic; expose services only through explicit rules |
| IoT | Isolate from Trusted and Lab/Servers; allow only required controller, DNS, and internet traffic |
| Remote access | Limit WireGuard clients to the resources they are intended to administer or use |

This approach follows least privilege and makes the expected traffic flow easier to review as the homelab grows.

---

## Wireless Segmentation

The UniFi-managed access point maps wireless networks to the appropriate VLAN. This keeps guest and IoT clients separated even when they share the same physical access point as trusted devices.

---

## Lab/Servers Segment

The Lab/Servers network hosts the virtualization and service layer, including:

* Proxmox VE
* Ubuntu Server workloads
* Docker and Portainer
* AdGuard Home
* Uptime Kuma
* Home Assistant integrations

Administrative access originates from approved clients in the Trusted zone and is controlled through firewall policy.

---

## IoT Segment

The IoT network provides a dedicated trust boundary for smart-home devices. The planned Zigbee coordinator and Zigbee2MQTT architecture will integrate with Home Assistant without granting IoT devices broad access to the rest of the homelab.

See [Planned Zigbee2MQTT Architecture](../Projects/Zigbee2MQTT.md).

---

## Migration History

The earlier OpenWrt design used Trusted, Guest, and Lab VLANs plus a recovery network. Its screenshots and address plan remain in the [OpenWrt documentation](OpenWrt.md) as historical implementation evidence, but they do not describe the current UniFi policy model.

---

## Skills Demonstrated

* VLAN and SSID design
* Zone-based firewall policy
* Trust-boundary definition
* Least-privilege network access
* IoT isolation
* Network migration and documentation
