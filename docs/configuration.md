# Configuration

## Precedence

This repository combines dashboard defaults with settings for external services. It defines no shared command-line, environment variable and configuration-file override order; each external service resolves its own settings.

## Integration settings

The example scrape uses job pbs, port 10019, a 60-second interval and a 45-second timeout. Select the Prometheus data source, job_pbs and optional datastore filter in Grafana.

## Dashboard variables

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `pbs-backups.json / prometheus_ds` | datasource | `prometheus` | Grafana data source selected by the dashboard. |
| `pbs-backups.json / job_pbs` | textbox | `pbs` | Dashboard variable whose value selects a scrape job, instance or endpoint. |
| `pbs-backups.json / datastore` | query | `label_values(pbs_snapshot_count{job="${job_pbs}"}, datastore)` | Queries the data source for available values. |

## Prometheus jobs

The supplied [scrape example](https://github.com/willtheorangeguy/pbs-monitoring/blob/HEAD/examples/prometheus-scrape.yml) defines `pbs`. Copy its entries into your own scrape_configs and replace documentation hostnames. Job names can change if the dashboard variables change with them.

## Examples

The complete scrape job examples are in [`examples/prometheus-scrape.yml`](https://github.com/willtheorangeguy/pbs-monitoring/blob/HEAD/examples/prometheus-scrape.yml). Copy the relevant job into your Prometheus configuration and replace the example targets.
