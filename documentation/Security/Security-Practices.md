# Security Practices

## Status

**Current working practices.** These controls are applied in an active homelab using enterprise-inspired methods and are documented without implying organization-wide production ownership.

## Network Segmentation

Five VLANs separate Trusted, Guest, Lab / Servers, IoT, and Remote Access roles. Segmentation reduces unnecessary reachability and creates clear sources and destinations for policy decisions.

## Zone-Based Firewall

UniFi zone-based policies default to isolation between roles and add explicit exceptions for required traffic. Stateful return traffic is permitted for an allowed connection, but unrelated unsolicited traffic is not made generally available.

## Host-Level Firewall

Host controls such as UFW provide a second policy boundary near the service. A gateway rule can make a route possible while the host firewall limits the reachable application. Home Assistant, SSH, and n8n are examples of services permitted for the Twingate Connector at the host layer.

## Twingate Connector Isolation

The Twingate Connector runs in a dedicated Debian LXC in VLAN 50. It initiates outbound connections and requires no inbound internet port. Remote clients do not join VLAN 50; the segment exists to isolate the Connector and make its access rules explicit.

## WireGuard

WireGuard remains an established VPN route for use cases suited to tunnel- and routing-based access. It is maintained as a separate model from Twingate and does not remove the need for gateway, host, and application controls.

## Least-Privilege Exceptions

Required integrations are opened narrowly. Validation includes both the flow that should work and a representative flow that should remain blocked. Exceptions are documented so they can be reviewed and removed when no longer needed.

## Credential and Secret Handling

Credential hygiene uses Bitwarden-based password management, unique credentials, and careful handling of secrets outside the public repository. Bitwarden is a security routine, not presented as a standalone homelab service or an enterprise IAM platform.

Tokens, private keys, account identifiers, and sensitive network values are excluded from Git. Public examples use descriptions rather than live credentials.

## Screenshot Redaction

Screenshots are point-in-time evidence and are reviewed before publication. Public IP addresses, MAC addresses, serial numbers, email addresses, personal client names, tokens, keys, QR codes, and unnecessary internal addresses are masked or excluded.

Historical OpenWrt screenshots are labelled as historical and are never reused as if they were current UniFi evidence.

## Backup and Recovery Validation

Backups, snapshots, and scheduled jobs are part of the operating model. Recovery thinking includes verifying that a backup completed, understanding where it is stored, documenting dependencies, and planning restoration tests rather than assuming that a backup file is sufficient.

## Change and Troubleshooting Workflow

1. Define expected behavior and scope.
2. Capture relevant evidence before the change.
3. Form a testable hypothesis.
4. Make one controlled change with a rollback path.
5. Test the intended outcome and important denied paths.
6. Review network, host, and application evidence.
7. Record the result and follow-up work.

## Related Documentation

* [Twingate Zero Trust Access](../Network/Twingate.md)
* [VLAN Segmentation](../Network/VLANs.md)
* [Backup Strategy](../Virtualization/Backup-Strategy.md)
* [Learning Methodology](../Career/Learning-Methodology.md)
