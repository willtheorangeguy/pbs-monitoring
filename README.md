# Proxmox Backup Server dashboard

Portable monitoring bundle with example configuration. Replace example addresses and token paths for your installation; no live credentials are included.

## Requirements

The natrontech/pbs-exporter and a Prometheus scrape job.

## Dashboards

- `dashboards/pbs-backups.json`

Import the JSON in Grafana using **Dashboards > New > Import**. Select your data source from the dashboard variable(s) at the top. Update the Prometheus job variables to match your `scrape_configs` job names; use the Instance selector when present. The dashboard's JSON is also suitable for file provisioning after you have selected or provisioned data source UIDs.

Expected default job labels:

- `pbs-backups.json`: pbs

## Monitoring code

See the code and example configuration in this folder, if present. Keep API keys and metrics bearer tokens in local secret files or another secret manager; never commit them. Scrape examples use documentation addresses and must be edited for your network.

## Before publishing

Test against the application and Grafana versions you intend to support. Add a license you choose and check attribution for upstream components. No release or Grafana catalog upload has been performed.

## PBS setup

Install the upstream natrontech/pbs-exporter with read-only `Audit` and `DatastoreAudit` permissions. Scrape it as job `pbs`, then select that job in the dashboard. Multiple datastores can share one backing filesystem; do not sum their reported capacity as though it were separate physical storage.

The dashboard adapts the pbs-exporter maintainer dashboard; check and retain upstream attribution and license terms before publication. Capacity panels show each datastore separately because datastores can share physical storage.

A sample `scrape_configs` fragment is in `examples/prometheus-scrape.yml`; replace the example hosts and token paths.
