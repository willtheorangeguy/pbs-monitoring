# Architecture

This project connects its data source to its Grafana dashboard through the components shown below.

## Overview

This diagram shows the data path for this project.

```mermaid
graph LR
  A[Proxmox Backup Server] -->|queried by| B[natrontech pbs-exporter]
  B -->|exposes metrics to| C[Prometheus]
  C -->|queried by| D[Grafana dashboard]
```

## Components

### Data source

Proxmox Backup Server -> natrontech/pbs-exporter -> Prometheus -> Grafana dashboard.

### Dashboard

`dashboards/pbs-backups.json` contains the Grafana dashboard definition.

## Data flow

Proxmox Backup Server -> natrontech/pbs-exporter -> Prometheus -> Grafana dashboard. Grafana evaluates dashboard queries against the selected data source and label values.

## Directory layout

```text
.
├── dashboards/  Grafana dashboard JSON files
├── examples/  Scrape and deployment examples
├── docs/        Documentation source
└── README.md    Project overview and quick links
```
