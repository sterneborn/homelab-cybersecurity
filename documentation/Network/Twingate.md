# Twingate Zero Trust Access

## Status

**Operating.** A Twingate Connector runs as a native systemd service in a dedicated Debian LXC on Proxmox.

## Purpose

Twingate provides an identity- and Resource-based route to approved homelab services. It complements the established WireGuard VPN by solving a different access problem: a remote user requests a defined Resource instead of joining a broad client network.

## Architecture

```text
Remote client
    |
Twingate service
    |
Outbound Connector tunnel
    |
Debian LXC Connector
Remote Access VLAN 50
    |
UniFi zone-based policy
    |
Approved internal Resource
    |
Optional host firewall restrictions
```

The Connector initiates outbound connections. No inbound port from the internet is opened for it.

## Connector Deployment

The Connector is installed natively in a dedicated Debian LXC and managed by systemd. A separate container provides a clear operational boundary for service health, updates, logging, and troubleshooting without mixing the access component with application workloads.

No Connector token, account information, internal host address, or Twingate network URL is stored in this public repository.

## Access Flow

1. A remote client requests a configured Resource through Twingate.
2. Twingate evaluates the request and uses the outbound Connector path.
3. The Connector routes from VLAN 50 toward the approved internal Resource.
4. UniFi policy must allow the Connector host's flow to that Resource.
5. The destination host firewall can restrict the allowed service further.
6. Stateful return traffic follows the permitted connection back through the Connector.

The initial protected Resource is the Lab / Servers network. Home Assistant, SSH, and n8n are examples of services allowed at the host layer. This does not imply that individual Twingate per-application Resources or Twingate-side port restrictions have been configured.

## VLAN 50 Design

VLAN 50 is the Connector's security segment, not a traditional VPN client network. Remote clients never receive a VLAN 50 address and do not become general members of the local segment.

The Connector is isolated there so its traffic has a distinct policy source. A Resource can remain in VLAN 30 because the Connector uses local routing to reach it. Routing alone is insufficient: the UniFi policy and any destination host firewall must also permit the intended flow.

## Policy Layers

Access is limited through several independent layers:

1. Twingate identity and Resource authorization.
2. Connector isolation in VLAN 50.
3. UniFi zone-based policy from the Connector host to approved Resources.
4. Host-level rules such as UFW for allowed services.
5. Application authentication and authorization where applicable.

This design avoids treating a successful remote connection as unrestricted internal access.

## Validation Approach

Validation is based on expected and denied outcomes:

* confirm the Connector service is active under systemd,
* confirm the Connector can establish its outbound connection,
* test a remote client against an approved Resource,
* confirm the intended service responds,
* test that unrelated services or destinations remain unavailable,
* check UniFi, host-firewall, and application evidence,
* verify that no inbound Connector port is exposed.

!!! note "Screenshot status"
    A redacted Twingate Remote Network screenshot has not been added. The page intentionally contains no broken placeholder or simulated product screenshot.

## Security Considerations

* Connector credentials and tokens remain outside Git.
* The public documentation omits the network URL, personal accounts, and internal Connector address.
* The Connector uses an outbound-only connection model.
* VLAN and firewall policy limit lateral reach.
* Host rules remain relevant even when Twingate authorizes a Resource.
* WireGuard remains available as a separate access route with a different trust and routing model.

## Troubleshooting Approach

Troubleshooting proceeds from the narrowest observable layer outward:

1. Confirm client identity and the requested Resource.
2. Check Twingate client state and name resolution.
3. Confirm Connector service status and outbound connectivity.
4. Verify routing from VLAN 50 to the Resource network.
5. Inspect UniFi policy for the Connector source and Resource destination.
6. Inspect UFW or another host firewall for the required service.
7. Test application health locally and through the remote path.
8. Record the failing layer, change, result, and rollback.

## Skills Demonstrated

* Debian and systemd service operation
* Proxmox LXC deployment
* VLAN and zone-based firewall design
* Zero Trust access concepts
* Layered policy troubleshooting
* Validation of permitted and denied flows
* Security-conscious technical documentation

## Related Documentation

* [VLAN Segmentation](VLANs.md)
* [UniFi Network](UniFi.md)
* [WireGuard Remote Access](WireGuard.md)
* [Security Practices](../Security/Security-Practices.md)
