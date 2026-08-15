# VLAN Segmentation

## Status

**Operating — five networks managed by UniFi.**

Segmentation separates devices and services by role and trust. Routing between segments is possible only when the gateway policy permits the flow, and host firewalls can restrict it further.

## Current VLANs

| VLAN | Name | Role | Policy intent |
| ---- | ---- | ---- | ------------- |
| 10 | Trusted | Personal and administrative clients | Controlled access to approved services |
| 20 | Guest | Visitor devices | Internet only |
| 30 | Lab / Servers | Proxmox, VMs and services | Explicitly exposed infrastructure services |
| 40 | IoT | Smart-home and lower-trust devices | Isolation with required integration exceptions |
| 50 | Remote Access | Twingate Connector infrastructure | Connector-only segment with explicit access to approved Resources |

## VLAN 10 — Trusted

Trusted contains personal and administrative clients. Its higher trust does not imply unrestricted access; connections to infrastructure remain limited to approved services.

## VLAN 20 — Guest

Guest is intended for visitor devices. It provides internet access while blocking private-network access.

## VLAN 30 — Lab / Servers

Lab / Servers contains Proxmox, virtual machines, containers, monitoring, and self-hosted applications. Services are exposed explicitly rather than by opening the full segment.

## VLAN 40 — IoT

IoT contains smart-home and lower-trust devices. Required integrations with Home Assistant are handled as narrow exceptions. The planned Zigbee2MQTT architecture will follow the same model.

## VLAN 50 — Remote Access

Remote Access contains the dedicated Debian LXC Twingate Connector. The segment reduces the Connector's exposure to normal client and server traffic and makes the source of Connector-to-Resource flows clear in UniFi policy.

Twingate clients do **not** join VLAN 50 and do not receive a VLAN 50 address. A client requests an approved Resource through Twingate; the Connector then reaches that Resource using local routing and explicit policy. The Resource can remain in VLAN 30.

The Connector host is permitted to reach approved internal Resources at the UniFi layer. Host firewalls can narrow the flow to the required service. This separates route availability from service authorization.

!!! note "Screenshot status"
    A current `unifi-networks-vlan50.png` capture is pending. No placeholder is embedded here, and historical OpenWrt images are not reused as UniFi evidence.

## Validation

Validation checks both intended access and isolation:

* confirm a device receives the expected network assignment,
* verify Guest cannot reach private networks,
* verify only required IoT integration flows,
* confirm the Twingate Connector reaches an approved Resource,
* confirm the same path does not imply broad access to other services,
* verify remote clients remain outside the local VLAN addressing model.

## Related Documentation

* [Network Overview](../Network-Overview.md)
* [UniFi Network](UniFi.md)
* [Twingate Zero Trust Access](Twingate.md)
* [Security Practices](../Security/Security-Practices.md)
