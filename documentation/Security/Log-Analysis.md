# Log Analysis

## Status

**Planned expansion.**

Service-specific logs are already used during troubleshooting, but a centralized log-analysis platform is not currently documented as deployed.

---

## Current Practice

Troubleshooting uses the logs closest to the failing layer, including:

* `journalctl` and `systemctl` for Linux services
* Docker container logs
* Proxmox task and system logs
* UniFi gateway and firewall events
* Application logs from self-hosted services

---

## Planned Direction

* Centralize selected logs without collecting unnecessary personal data
* Normalize timestamps and host identity
* Build repeatable searches for common failures
* Correlate network, host, and application events
* Define retention, access, and backup requirements

The goal is useful investigation capability rather than collecting every available log by default.
