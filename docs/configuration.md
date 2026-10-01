# pbs-monitoring — Configuration

The example scrape uses job pbs, port 10019, a 60-second interval and a 45-second timeout. Select the Prometheus data source, job_pbs and optional datastore filter in Grafana.

## Dashboard variables

| Dashboard | Variable | Type | Default or query |
|---|---|---|---|
| `pbs-backups.json` | `prometheus_ds` | datasource | `prometheus` |
| `pbs-backups.json` | `job_pbs` | textbox | `pbs` |
| `pbs-backups.json` | `datastore` | query | `label_values(pbs_snapshot_count{job="${job_pbs}"}, datastore)` |

## Prometheus jobs

The supplied [scrape example](../examples/prometheus-scrape.yml) defines `pbs`. Copy its entries into your own scrape_configs and replace documentation hostnames. Job names can change if the dashboard variables change with them.
