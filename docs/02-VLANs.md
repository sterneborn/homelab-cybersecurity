# 02-VLANs.md

# VLAN Design

## Objective

The purpose of VLAN segmentation is to separate trusted devices, guest devices, and lab systems into different network zones.

This improves security, reduces unnecessary network exposure, and creates a more realistic enterprise-style network design.

---

## VLAN Overview

| VLAN    | Name     | Subnet          | Purpose                              |
| ------- | -------- | --------------- | ------------------------------------ |
| VLAN 1  | Recovery | 192.168.1.0/24  | Emergency access                     |
| VLAN 10 | LAN      | 192.168.10.0/24 | Trusted devices                      |
| VLAN 20 | Guest    | 192.168.20.0/24 | Guest and untrusted devices          |
| VLAN 30 | Lab      | 192.168.30.0/24 | Security lab and Proxmox environment |

---

## VLAN 1 - Recovery

Purpose:

* Emergency router access
* Recovery if VLAN configuration breaks

Gateway:

```text
192.168.1.1
```

---

## VLAN 10 - LAN

Purpose:

* Trusted personal devices
* Daily-use devices

Gateway:

```text
192.168.10.1
```

Access:

* Internet access allowed
* Access to Lab VLAN allowed

---

## VLAN 20 - Guest

Purpose:

* Guest devices
* Untrusted devices

Gateway:

```text
192.168.20.1
```

Access:

* Internet access allowed
* Access to LAN blocked
* Access to Lab blocked

---

## VLAN 30 - Lab

Purpose:

* Proxmox
* Linux servers
* Docker
* Security tools
* Monitoring systems

Gateway:

```text
192.168.30.1
```

Access:

* Internet access allowed
* Administrative access from LAN allowed
* Future lab services hosted here

---

## Firewall Logic

The firewall is designed around the principle of least privilege.

| Source    | Destination | Status  |
| --------- | ----------- | ------- |
| LAN       | Internet    | Allowed |
| LAN       | Lab         | Allowed |
| Guest     | Internet    | Allowed |
| Guest     | LAN         | Blocked |
| Guest     | Lab         | Blocked |
| Lab       | Internet    | Allowed |
| WireGuard | LAN         | Allowed |
| WireGuard | Lab         | Allowed |
| WireGuard | WAN         | Allowed |

---

## Lessons Learned

VLANs are not only about separating devices. They are about controlling trust.

A flat network treats all devices as equally trusted. A segmented network allows different rules for different device groups.

This is a core concept in both enterprise networking and cybersecurity.
