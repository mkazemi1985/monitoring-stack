
# Monitoring Stack (Project 7)

A reproducible **Prometheus + Grafana + Alertmanager** setup for local observability.

| Service | Port | UI Path |
|---------|------|---------|
| Prometheus | **9090** | `/graph` |
| Alertmanager | **9093** | `/` |
| Grafana | **3000** | `/` (default login **admin / admin**) |
| Node Exporter | **9100** | `/metrics` |

## Quick start

```bash
git clone https://github.com/<YourUser>/monitoring-stack.git
cd monitoring-stack
docker compose up -d          # spin up the stack
```

Point your browser to **http://localhost:3000** and import dashboard ID **1860** (Node‑Exporter Full).

## Features

* Collects host metrics via **Node Exporter**.  
* Pre‑loaded *High CPU* alert rule (`prometheus/alerts.yml`).  
* Alert routing handled by **Alertmanager** (basic config; plug in Slack, Telegram, e‑mail, …).  
* Works on Docker Desktop + WSL 2 (Windows 11) and native Linux.

## File structure

```
monitoring-stack/
├── docker-compose.yml
├── .gitignore
├── README.md
├── prometheus/
│   ├── prometheus.yml      # scrape targets + alertmanager
│   └── alerts.yml          # alert rules
└── alertmanager/
    └── alertmanager.yml    # receivers & routing
```

## Next steps

1. **Add receivers** – edit `alertmanager/alertmanager.yml` to integrate Slack / Telegram.  
2. **Expose your app metrics** – instrument your service and append a new `job_name` in `prometheus.yml`.  
3. **Dashboards** – create custom Grafana dashboards or import community ones.  
4. **Retention & backups** – tune `--storage.tsdb.retention.time` and back‑up `prom_data/`.

## License

This project is released under the MIT License – see [LICENSE](LICENSE) for details.
