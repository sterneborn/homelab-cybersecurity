# Prometheus

## Status

**Operating.** Prometheus is installed and collecting metrics in the current homelab.

## Operational Role

Prometheus collects time-series metrics from selected hosts and services. Node Exporter provides host-level visibility such as system resource and operating-system metrics. The resulting data helps distinguish a transient availability issue from a resource, host, or service trend.

## Monitoring Relationships

The monitoring tools have complementary roles:

* **Prometheus** collects and stores metrics for querying and trend analysis.
* **Node Exporter** exposes selected host metrics to Prometheus.
* **Grafana** visualizes Prometheus data in operational dashboards.
* **Uptime Kuma** focuses on availability and endpoint checks.
* **SmokePing** provides latency and packet-loss history.

Together they provide more context than a single up/down signal.

## Troubleshooting Use

Prometheus data is used to compare the time of an incident with host or service behavior. A typical investigation can ask:

1. Did the endpoint fail, slow down, or remain reachable?
2. Did CPU, memory, storage, or another host metric change at the same time?
3. Was the symptom isolated to one service or visible across the host or network?
4. Do Uptime Kuma and SmokePing observations support the same conclusion?

Metrics support a diagnosis but do not replace service logs, network evidence, or controlled testing.

## Network and Access

Prometheus runs within the segmented environment. Scrape access is limited to documented targets, and cross-network flows are opened only where collection requires them. The public documentation intentionally omits internal addresses, authentication data, and exposed ports.

Administrative and dashboard access remains subject to the network's zone-based and host-level controls.

## Operations

* Keep scrape targets purposeful and documented.
* Review failed scrapes as both monitoring and connectivity signals.
* Track storage and retention needs.
* Include configuration and data requirements in backup planning.
* Validate the monitoring path after network or host-firewall changes.

Alerting beyond current service checks remains an area for continued development; this page does not claim a complete Alertmanager deployment.

## Related Documentation

* [Grafana](Grafana.md)
* [Uptime Kuma](Uptime-Kuma.md)
* [Alerting — Planned / In Progress](Alerting.md)
* [Network Overview](../Network-Overview.md)
