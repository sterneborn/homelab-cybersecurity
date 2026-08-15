# Grafana

## Status

**Operating.** Grafana is installed and used to visualize Prometheus metrics.

## Operational Role

Grafana provides dashboards for selected host and service metrics collected by Prometheus. Its purpose is operational visibility: showing trends, comparing related measurements, and giving troubleshooting work a useful time-based view.

## Dashboards and Trend Analysis

Current dashboard use focuses on:

* host health and resource trends,
* service behavior over time,
* comparison of related metrics during an incident,
* identifying persistent patterns that simple availability checks may miss,
* presenting a concise operational view rather than every available metric.

The dashboards complement Uptime Kuma availability checks and SmokePing latency history. A dashboard is treated as evidence to investigate, not as proof of a root cause by itself.

## Troubleshooting Support

During troubleshooting, Grafana helps establish when a symptom started and whether other signals changed at the same time. This supports a structured path from user-visible behavior to network, host, and application checks.

Useful dashboards are kept focused enough that a change is visible and explainable. Default dashboards are not presented as meaningful operational work without understanding the panels and data behind them.

## Network and Access

Grafana operates inside the segmented Lab / Servers environment and uses Prometheus as its metrics source. Access is limited within the network's zone-based policy model and can be narrowed further at the host layer. Internal ports, authentication details, and addresses are not published.

## Operations

* Keep dashboard purpose and data sources documented.
* Validate dashboards after Prometheus, exporter, or network changes.
* Include configuration in backup and recovery planning.
* Review permissions and avoid unnecessarily broad access.
* Use trends alongside logs, availability checks, and direct service tests.

## Related Documentation

* [Prometheus](Prometheus.md)
* [Uptime Kuma](Uptime-Kuma.md)
* [Alerting — Planned / In Progress](Alerting.md)
* [Security Practices](../Security/Security-Practices.md)
