# pbs-monitoring — Installation

## Requirements

natrontech/pbs-exporter with read-only Audit and DatastoreAudit permissions, Prometheus and Grafana.

## Procedure

Install and configure the upstream natrontech/pbs-exporter with PBS credentials. Adapt examples/prometheus-scrape.yml, confirm pbs_up is available and import dashboards/pbs-backups.json.

The files under [examples](../examples) are reference configuration. Replace example addresses, token paths and bind addresses for your deployment.

Next, review [configuration](./configuration.md) and [dashboard usage](./usage.md).
