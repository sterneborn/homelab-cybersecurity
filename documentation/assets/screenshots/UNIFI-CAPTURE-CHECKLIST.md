# UniFi Capture Checklist

Current UniFi screenshots are still required. Capture these three views from the active UniFi console and update this branch and draft PR after review.

## 1. Networks and VLAN 50

Save as `unifi-networks-vlan50.png`.

Capture the UniFi **Settings → Networks** view where all five networks are visible and Remote Access clearly shows VLAN ID 50. Include enough interface context to establish that this is the current UniFi network list. Do not open or expose credentials, DHCP leases, client details, or sensitive addressing panels.

Place the reviewed image on `documentation/Network/VLANs.md` with a caption identifying it as point-in-time evidence of the five-network implementation.

## 2. Zone-Based Firewall

Save as `unifi-zone-firewall.png`.

Capture the UniFi **Settings → Security → Traffic & Firewall Rules** or equivalent zone-policy view. Show the zone relationship or rule summary that demonstrates the explicit policy from the Remote Access / Connector segment to approved internal Resources. The screenshot must not imply broad access from VLAN 50.

Place the reviewed image on `documentation/Network/UniFi.md` under **Firewall Model**, with a point-in-time evidence caption.

## 3. Current Topology

Save as `unifi-topology.png`.

Capture the UniFi **Topology** view showing the Cloud Gateway Ultra and UniFi U7 Lite with enough surrounding context to demonstrate the current managed network. Collapse, rename, or mask personal client details before capture.

Place the reviewed image on `documentation/Network/UniFi.md` under **Current Components**, with a point-in-time evidence caption.

## Redaction Review for Every Capture

Before adding any image, mask or crop:

* public IP addresses,
* unnecessary internal host addresses,
* MAC addresses,
* serial numbers and device IDs,
* email addresses and personal account names,
* full personal client names,
* tokens, API keys, and credentials,
* QR codes,
* Twingate Access Tokens and Refresh Tokens.

VLAN IDs 10, 20, 30, 40, and 50 may remain visible. Confirm that no browser profile, notification, or unrelated private data appears around the UniFi interface.

## Final Checks

* Use real current UniFi captures; do not substitute historical OpenWrt images.
* Keep the original aspect ratio and use readable resolution.
* Verify the final redacted file, not only the source capture.
* Add descriptive alt text and a point-in-time caption.
* Rebuild MkDocs and check desktop and mobile rendering.
