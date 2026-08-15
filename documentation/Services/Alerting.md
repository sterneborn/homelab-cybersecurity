# Alerting

## Status

**Planned — not currently deployed as a separate alerting stack.**

Uptime Kuma currently provides service visibility. A broader alerting workflow will be evaluated alongside Prometheus and Grafana.

---

## Design Goals

* Alert on actionable service or infrastructure conditions
* Avoid excessive or duplicate notifications
* Include enough context to begin troubleshooting
* Define ownership and recovery steps for each alert
* Test delivery without creating alert fatigue

---

## Planned Workflow

```text
Metrics or service check
        |
Alert condition
        |
Notification channel
        |
Operator verification and documented response
```

No notification platform is listed as current until it has been deployed and tested.
