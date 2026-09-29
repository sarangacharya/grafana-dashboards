<p align="center">
  <img src="assets/banner.svg" alt="Grafana Dashboards: Kubernetes capacity, bottlenecks and troubleshooting" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Grafana-10%2B-F46800?logo=grafana&logoColor=white" alt="Grafana 10+">
  <img src="https://img.shields.io/badge/Prometheus-PromQL-E6522C?logo=prometheus&logoColor=white" alt="Prometheus">
  <img src="https://img.shields.io/badge/Kubernetes-any%20cluster-326CE5?logo=kubernetes&logoColor=white" alt="Kubernetes">
  <img src="https://img.shields.io/badge/Amazon%20EKS-tested-FF9900?logo=amazoneks&logoColor=white" alt="Tested on Amazon EKS">
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="MIT License">
</p>

Grafana dashboards for Kubernetes, built while debugging real clusters.

Each dashboard starts from a question an engineer asks during an incident ("why won't this pod schedule?", "is it CPU, memory or the network?") rather than from a list of available metrics. Every panel has a tooltip that explains it, and every dashboard comes with a troubleshooting playbook.

---

## Dashboards

| Dashboard | What it answers | Preview |
|---|---|---|
| **[Kubernetes Capacity & Bottlenecks](dashboards/k8s-capacity-bottlenecks/)** | Why is my pod `Pending`? Which node is full, and full of what: CPU, memory or pod slots? Which workloads over-request, get throttled, or are about to be OOMKilled? Is it the network? | <a href="dashboards/k8s-capacity-bottlenecks/"><img src="dashboards/k8s-capacity-bottlenecks/screenshots/overview.png" width="420" alt="Kubernetes Capacity & Bottlenecks preview"></a> |

More dashboards are on the way. ⭐ Star the repo to follow along.

---

## Quick start

1. Open the dashboard's folder and download its `.json` file.
2. In Grafana, go to **Dashboards → New → Import** and upload the file.
3. Choose your Prometheus data source and click **Import**.

Each dashboard's own README covers its requirements, how to provision it as code (sidecar ConfigMap or the Grafana API), and how to read it during an incident.

---

## Design principles

- **Question-first.** Rows are ordered the way you debug: overview, then where the pressure is, then which workload, then the network.
- **Scheduler-aware.** Requests, allocatable capacity and real usage appear side by side. The scheduler uses requests, so usage alone never explains a `Pending` pod.
- **Portable.** No hard-coded data source UIDs. The data source is a dashboard variable, so the JSON imports cleanly into any Grafana.
- **Explained.** Every panel carries a description tooltip, and every dashboard has a playbook that maps symptom to panel to fix.

---

## Repository layout

```
.
├── README.md                          ← you are here
├── LICENSE
├── assets/
│   ├── banner.svg
│   └── social-preview.png             ← link-card image for LinkedIn / social
└── dashboards/
    └── k8s-capacity-bottlenecks/
        ├── README.md                  ← dashboard docs + troubleshooting playbook
        ├── k8s-capacity-bottlenecks-dashboard.json
        └── screenshots/
            └── overview.png
```

Every dashboard gets its own folder with the same layout. GitHub renders the folder's `README.md` when you open it.

---

## Contributing

Issues and pull requests are welcome, whether that's a new dashboard, a panel for a common bottleneck, or a fix for label differences between Prometheus setups.

## License

[MIT](LICENSE)

## Author

**[sarangacharya](https://github.com/sarangacharya)** · DevOps / Platform Engineer · [LinkedIn](https://www.linkedin.com/in/<your-linkedin-handle>)
