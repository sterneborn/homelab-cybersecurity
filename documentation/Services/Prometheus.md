# Prometheus

## Status

**Planned — not currently deployed.**

Prometheus is being considered for metrics collection beyond the availability checks already provided by Uptime Kuma.

---

## Intended Role

* Collect time-series metrics from selected hosts and services
* Provide visibility into resource usage and service behavior
* Supply data to Grafana dashboards
* Support alerting based on measurable conditions

---

## Architecture Considerations

The future deployment must fit the Lab/Servers network and the UniFi zone-based firewall model. Exporters and scrape targets will be limited to the systems that need monitoring rather than opening broad cross-zone access.

---

## Before Deployment

* Define useful metrics and retention requirements
* Select initial scrape targets
* Document authentication and firewall needs
* Plan storage, backup, and upgrade procedures
* Avoid duplicating checks already handled well by Uptime Kuma
