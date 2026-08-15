# Home Assistant

## Overview

Home Assistant is the homelab's smart-home automation platform. It brings device state, automations, and integrations into a locally managed service while the network keeps IoT devices separated from trusted clients and server workloads.

---

## Role in the Homelab

Home Assistant is used to:

* Centralize smart-home integrations
* Build and test local automations
* Reduce dependence on separate vendor applications
* Provide a controlled integration point between services and IoT devices
* Support future Zigbee devices through the planned Zigbee2MQTT architecture

---

## Network Considerations

Smart-home devices belong to the dedicated IoT segment. Any communication that must cross into the Trusted or Lab/Servers zones is handled through explicit zone-based firewall policy rather than broad inter-VLAN access.

This separates convenience devices from administrative clients while allowing the specific integrations Home Assistant needs.

---

## Related Work

* [VLAN Segmentation](../Network/VLANs.md)
* [Planned Zigbee2MQTT Architecture](../Projects/Zigbee2MQTT.md)
* [Knut AI & Automation](../Projects/Knut.md)

---

## Skills Demonstrated

* Home automation platform administration
* Service integration
* IoT network segmentation
* Automation design
* Troubleshooting across application and network layers
