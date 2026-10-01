# Getting started

## Prerequisites

natrontech/pbs-exporter with read-only Audit and DatastoreAudit permissions, Prometheus and Grafana.

## Set up

Install and configure the upstream natrontech/pbs-exporter with PBS credentials. Adapt examples/prometheus-scrape.yml, confirm pbs_up is available and import dashboards/pbs-backups.json.

The example Prometheus scrape job names are `pbs`.

## Confirm data

In Prometheus, check `up{job="pbs"}` and inspect a panel query in Grafana.
For missing data, see [Troubleshooting](troubleshooting.md).
