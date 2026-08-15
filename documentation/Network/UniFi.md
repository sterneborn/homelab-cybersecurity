# UniFi Network

## Status

**Current network architecture**

The homelab now uses a **UniFi Cloud Gateway Ultra** as its gateway, router, and firewall platform. Wi-Fi is provided through a **UniFi-managed access point**, bringing wired and wireless policy management into the same environment.

The UniFi deployment replaced the earlier Netgear R7800 and OpenWrt architecture. The [OpenWrt documentation](OpenWrt.md) remains available as a record of that earlier phase and the skills developed while operating it.

![Current UniFi homelab network topology](../assets/network-topology-v2.png)

---

## Current Components

* UniFi Cloud Gateway Ultra
* UniFi-managed Wi-Fi and access point
* VLAN-backed network segmentation
* Zone-based firewall policies
* WireGuard remote access
* Centralized visibility and configuration through UniFi Network

---

## Segmented Networks

The network is divided by role and trust level:

| Network | Purpose |
| ------- | ------- |
| Trusted | Personal and administrative devices |
| Guest | Visitor devices with isolated internet access |
| Lab/Servers | Proxmox, virtual machines, containers, and infrastructure services |
| IoT | Smart-home and other lower-trust devices |

See [VLAN Segmentation](VLANs.md) for the security goals and policy model.

---

## Firewall Model

Inter-network traffic is controlled with zone-based firewall policies. The design starts from isolation between trust zones and adds only the access required for administration, infrastructure services, and smart-home integrations.

This model makes policy intent clearer than a flat collection of device-specific rules and supports continued expansion of the lab without treating every connected device as equally trusted.

---

## Remote Access

WireGuard remains the established remote-access path. Tailscale is being evaluated as a possible complementary option for simpler device-to-device access and administration; it has not replaced WireGuard.

See [WireGuard Remote Access](WireGuard.md) for details.

---

## Skills Demonstrated

* UniFi gateway and Wi-Fi administration
* VLAN and SSID design
* Zone-based firewall policy design
* Network migration planning
* Segmentation and least-privilege access
* Remote-access integration
