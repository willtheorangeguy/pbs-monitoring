# PBS Monitoring

A Grafana dashboard for PBS snapshots, datastore usage and recent backup age using natrontech/pbs-exporter.

## Key features

- Snapshot counts and latest backup age by VM or CT.
- Datastore capacity and usage panels.
- Raw latest snapshot verification flags.
- Datastore and job selectors for focused views.

## Quick start

Open Grafana and import `dashboards/pbs-backups.json` through **Dashboards → New → Import**. Select the configured data source and match the dashboard variables to your labels. See [Getting started](getting-started.md) for prerequisites and setup.

## Where to next

<div class="wt-grid" markdown>

[:material-rocket-launch: **Getting started**<br>Set up the required integrations](getting-started.md){ .wt-card }

[:material-download: **Installation**<br>Install and connect the required services](installation.md){ .wt-card }

[:material-tune: **Configuration**<br>Review scrape examples and dashboard variables](configuration.md){ .wt-card }

[:material-sitemap: **Architecture**<br>Follow metrics from source to dashboard](architecture.md){ .wt-card }

[:material-view-dashboard: **Dashboard usage**<br>Import and use the dashboard](usage.md){ .wt-card }

</div>

## Support

{{ support() }}
