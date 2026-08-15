# Project Journal

## 2026-06-08 - OpenWrt Deployment and Network Segmentation

### Completed Tasks

* Installed OpenWrt
* Configured VLANs
* Configured WireGuard
* Configured Cloudflare DDNS

### Notes

Successfully replaced the stock firmware with OpenWrt and established a segmented network design using VLANs. Configured WireGuard for secure remote access and integrated Cloudflare DDNS to maintain access despite dynamic public IP changes. This setup forms the foundation for future security testing, VPN access and homelab services.

### Key Learnings

* Basic OpenWrt administration
* VLAN segmentation concepts
* WireGuard deployment and troubleshooting
* Dynamic DNS integration with Cloudflare
* Learned how to troubleshoot WireGuard using `wg show`
* Learned firewall zoning in OpenWrt

---

## 2026-06-09 - Wi-Fi Performance Troubleshooting and SQM Analysis

### Completed Tasks

* Investigated Wi-Fi performance issues
* Reconfigured wireless network design
* Verified 2.4 GHz and 5 GHz radio assignments
* Tested and analyzed SQM (CAKE) performance
* Validated router resource utilization
* Verified WAN link speed and duplex settings
* Evaluated software flow offloading

### Notes

While testing the newly segmented OpenWrt network, I noticed significantly lower Wi-Fi performance than expected. Initial speed tests showed approximately 110 Mbps download and 136 Mbps upload despite having a 250/250 Mbps fiber connection.

The troubleshooting process began by verifying the wireless connection. Using macOS wireless diagnostics, I discovered that the client was connected using the 802.11g standard on the 2.4 GHz band with a link rate of only 54 Mbps. Further investigation revealed that the Home SSID was only available on the 2.4 GHz radio, while the Guest network was operating on the 5 GHz radio.

The wireless configuration was redesigned so that the Home network was available on both 2.4 GHz and 5 GHz while maintaining Guest network isolation. After reconnecting, the client successfully negotiated an 802.11ac connection on 5 GHz with an 866 Mbps link rate, resulting in significantly improved wireless performance.

Additional testing focused on Smart Queue Management (SQM) using CAKE. Multiple configurations and bandwidth limits were tested and compared against baseline measurements. Router CPU utilization, memory usage, WAN link negotiation and CAKE statistics were analyzed to identify potential bottlenecks. Testing confirmed that the router hardware, WAN connection and wireless link were functioning correctly. While SQM improved latency management, it introduced a measurable reduction in throughput on this platform and configuration.

### Key Learnings

* Wi-Fi design and radio assignments can have a major impact on network performance
* Structured troubleshooting is more effective than making configuration changes based on assumptions
* Wireless, routing, WAN connectivity and QoS should be validated independently when investigating performance issues
* CAKE was functioning correctly, but throughput and latency improvements must be evaluated based on actual network requirements
* Evidence-based troubleshooting helps isolate root causes and prevents unnecessary configuration changes

---

## 2026-06-10 - Documentation Platform Integration

### Completed Tasks

* Deployed MkDocs Material documentation portal
* Moved technical documentation into a dedicated documentation structure
* Published documentation under the /docs path
* Added screenshots to technical documentation pages
* Redesigned the network topology diagram
* Improved navigation between portfolio, documentation and GitHub repository
* Added direct links from project cards to technical documentation
* Refined portfolio layout and user experience

### Notes

Following the deployment of the portfolio website, the next step was improving the technical documentation experience.

The documentation was migrated into a dedicated MkDocs Material environment and published alongside the portfolio under the /docs path. This approach allowed the portfolio to serve as a recruiter-friendly landing page while maintaining detailed technical documentation for projects, configurations, troubleshooting activities and learning notes.

Screenshots were added throughout the documentation to provide visual evidence of completed work and configuration steps. The network topology diagram was also redesigned to improve readability and create a more professional presentation.

Additional improvements focused on navigation and usability, creating clearer connections between the portfolio, technical documentation and GitHub repository.

### Key Learnings

* MkDocs Material deployment and configuration
* Documentation structure and information architecture
* Technical documentation publishing workflows
* Screenshot integration and asset management
* Navigation design and user experience improvements
* Maintaining separate presentation and documentation layers

---

## 2026-06-10 - Proxmox Deployment and Infrastructure Services

### Completed Tasks

* Installed Proxmox VE on dedicated hardware
* Configured ZFS storage
* Deployed Ubuntu Server virtual machine
* Verified virtual networking connectivity
* Installed Docker
* Deployed Portainer
* Deployed AdGuard Home
* Configured AdGuard Home as network DNS server
* Updated OpenWrt DHCP configuration
* Deployed Uptime Kuma
* Created infrastructure monitoring checks
* Reorganized MkDocs documentation structure
* Added virtualization documentation
* Added screenshots and technical verification steps

### Notes

This phase marked the transition from network infrastructure into virtualization and service deployment.

Proxmox VE was installed on a Fujitsu Esprimo Q7010 and configured with ZFS as the primary storage backend. The use of ZFS introduced snapshot functionality, providing a safe way to experiment with new services while maintaining recovery options.

An Ubuntu Server virtual machine was deployed as the primary infrastructure host. Network connectivity was verified through the Proxmox bridge configuration and VLAN 30 integration.

Docker was introduced as the container platform for hosting services. Portainer was deployed to simplify container management and provide visibility into the Docker environment.

AdGuard Home was then deployed as a network-wide DNS filtering service. Initial deployment required troubleshooting related to Docker networking and DNS port bindings. After resolving these issues, AdGuard Home was successfully integrated into the network and configured as the primary DNS server through OpenWrt DHCP settings.

Testing confirmed successful DNS resolution from both the Ubuntu Server virtual machine and client devices on the network.

Uptime Kuma was deployed to provide service monitoring and availability tracking. Monitors were created for critical infrastructure components including Ubuntu Server, Portainer, AdGuard Home and internet connectivity.

Significant improvements were also made to the documentation platform. The MkDocs structure was reorganized into dedicated sections for Networking, Virtualization, Services, Security and Career Development. Additional screenshots and verification procedures were added to improve documentation quality and portfolio presentation.

### Key Learnings

* Proxmox VE installation and administration
* ZFS storage fundamentals and snapshot strategy
* Virtual machine deployment and networking
* Docker installation and container management
* Portainer administration
* DNS service deployment with AdGuard Home
* DHCP and DNS integration within OpenWrt
* Infrastructure monitoring with Uptime Kuma
* Technical documentation organization
* Git-based documentation workflows
* Structured troubleshooting of containerized services

---

## 2026-06-12 – Backup Infrastructure and Recovery Strategy

### Objectives

The objective of this session was to implement a dedicated backup solution for the Proxmox environment and establish a foundation for enterprise-inspired backup and recovery procedures.

### Activities Completed

#### External Backup Storage

A Kingston XS2000 1 TB SSD was provisioned as dedicated backup storage.

Tasks completed:

* Removed existing APFS configuration
* Created a GPT partition table
* Created a Linux filesystem partition
* Formatted the partition using ext4
* Created a dedicated mount point at `/backup`
* Configured automatic mounting through `/etc/fstab`
* Verified read and write functionality

#### Proxmox Backup Storage

The external SSD was integrated into Proxmox as storage:

```text
backup-ssd
```

This repository is used exclusively for virtual machine backups.

#### Backup Verification

A manual backup of the Ubuntu Server virtual machine was performed to validate the backup infrastructure.

Backup Details:

* VM ID: 100
* Backup Mode: Snapshot
* Compression: ZSTD

Results:

* Backup completed successfully
* Backup archive stored on external SSD
* Backup file verified on disk

#### Automated Backup Scheduling

A scheduled backup job was created within Proxmox to automate future backups.

This establishes a repeatable backup process and reduces reliance on manual backups.

#### Cloudflare DDNS Troubleshooting

Investigated Dynamic DNS errors reported by OpenWrt.

Actions performed:

* Reviewed DDNS configuration
* Created a new Cloudflare API token
* Updated token permissions
* Verified DNS resolution for vpn.sterneborn.org

The issue appears resolved, although additional monitoring will be performed during future sessions.

### Lessons Learned

This session provided practical experience with:

* Linux storage management
* GPT partitioning
* ext4 filesystem creation
* Persistent mounting using fstab
* Proxmox backup repositories
* Snapshot-based VM backups
* Backup verification procedures
* Cloudflare DDNS troubleshooting

The backup infrastructure now provides a significantly improved recovery capability for the homelab environment.

---

## 2026-08-15 – UniFi Migration and Homelab Expansion

### Current State Documented

* Migrated the gateway and firewall role from OpenWrt to a UniFi Cloud Gateway Ultra
* Moved wireless management to a UniFi-managed access point
* Organized the network into Trusted, Guest, Lab/Servers, and IoT VLANs
* Adopted zone-based firewall policies between network segments
* Retained WireGuard for remote access
* Retained WireGuard as the established VPN path while preparing a separate resource-based access model
* Added Home Assistant to the documented service stack
* Continued operating Proxmox, Docker, Portainer, AdGuard Home, and Uptime Kuma
* Added Knut as a major custom AI and automation project
* Documented the Raspberry Pi 4 Borgen Audio project
* Planned a Zigbee coordinator and Zigbee2MQTT architecture for Home Assistant

### Borgen Audio Work

The Borgen Audio project combines a Raspberry Pi 4 and Raspberry Pi DAC Pro with AirPlay playback through Shairport Sync and Android Bluetooth playback through BlueALSA. Troubleshooting crossed `systemd`, ALSA, BlueZ, and audio-service configuration, reinforcing the value of validating each layer independently.

### Architecture Note

The OpenWrt documentation remains in the repository as a record of the original network architecture. Current documentation now clearly distinguishes that historical deployment from the UniFi environment.

### Key Learnings

* Network migration and policy translation
* UniFi gateway and managed Wi-Fi administration
* Zone-based firewall design
* IoT segmentation and smart-home integration planning
* AI and automation project development
* Linux audio, Bluetooth, and service troubleshooting

---

## 2026-08-15 – Twingate and Remote Access Segmentation

### Completed Work

* Added VLAN 50 as a dedicated Remote Access segment
* Deployed a Twingate Connector in a separate Debian LXC on Proxmox
* Installed the Connector as a native systemd service
* Verified its outbound-only connection model without opening an inbound internet port
* Added the initial protected Lab / Servers Resource
* Applied UniFi policy from the Connector host to approved internal Resources
* Used host-firewall rules to limit access to required services, including Home Assistant, SSH, and n8n where applicable
* Verified remote access through the complete client, Connector, network-policy, host-firewall, and application path

### Architecture Decision

VLAN 50 isolates Connector infrastructure; it is not an address pool for remote clients. A remote client requests an approved Resource through Twingate, while the Connector routes locally to that Resource under explicit UniFi and host-level policy. WireGuard remains available as a separate VPN model.

### Security and Documentation

Connector credentials, account details, internal addresses, and tokens were excluded from public material. Validation included both allowed access and representative denied paths so that the new route was not treated as broad internal access.

### Key Learnings

* Resource-based remote access architecture
* Debian LXC and systemd service operation
* Dedicated Connector segmentation
* UniFi zone-policy troubleshooting
* Host-firewall enforcement
* Secure validation and public documentation
