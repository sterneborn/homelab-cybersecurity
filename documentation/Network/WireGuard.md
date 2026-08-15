# WireGuard Remote Access

## Status

**Operating — established VPN path.**

WireGuard remains part of the homelab and provides a tunnel- and routing-based remote-access model. It is maintained separately from Twingate rather than being described as the only remote-access solution.

## Role

WireGuard is useful when a conventional VPN tunnel and explicit network routing are appropriate. Access depends on the configured tunnel, routes, gateway policy, and destination service controls.

## WireGuard and Twingate

| Model | WireGuard | Twingate |
| --- | --- | --- |
| Access concept | Tunnel- and routing-based VPN | Identity- and Resource-based access |
| Local component | VPN endpoint and routes | Outbound Connector |
| Client network behavior | Uses configured VPN addressing and routes | Does not join VLAN 50 |
| Policy focus | Tunnel peers, routes, firewall rules | Identity, Resource, Connector, and layered firewall policy |

The two paths have different operational uses. See [Twingate Zero Trust Access](Twingate.md) for the Connector design.

## Validation Approach

1. Confirm the peer and tunnel state.
2. Verify the intended client routes.
3. Check gateway policy for the VPN source.
4. Test only the destinations and services expected for the use case.
5. Confirm unrelated paths remain unavailable.
6. Record evidence without publishing keys or sensitive addresses.

## Security Considerations

* Private keys and peer secrets stay outside the public repository.
* VPN reachability does not replace destination authentication or host-firewall policy.
* Allowed routes and firewall rules should remain no broader than the use case requires.
* Changes are tested from both the remote client and the destination side.

## Historical OpenWrt Evidence

![Historical OpenWrt WireGuard interface](../assets/screenshots/interfaces-wan-wireguard.png)

*Point-in-time implementation evidence from the previous OpenWrt architecture. It is not a current UniFi screenshot and may include values that no longer represent the active network.*

## Related Documentation

* [Twingate Zero Trust Access](Twingate.md)
* [Network Overview](../Network-Overview.md)
* [UniFi Network](UniFi.md)
* [OpenWrt — Previous Architecture](OpenWrt.md)
