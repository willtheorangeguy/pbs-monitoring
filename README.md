<h1 align="center">pbs-monitoring</h1>
<h4 align="center">A Grafana dashboard for PBS snapshots, datastore usage and recent backup age using natrontech/pbs-exporter.</h4>

<div align="center">
  <img alt="GitHub Issues" src="https://img.shields.io/github/issues/willtheorangeguy/pbs-monitoring">
  <img alt="GitHub Pull Requests" src="https://img.shields.io/github/issues-pr/willtheorangeguy/pbs-monitoring">
  <img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-blue">
  <img alt="gitleaks workflow" src="https://github.com/willtheorangeguy/pbs-monitoring/actions/workflows/gitleaks.yml/badge.svg">
  <img alt="testing workflow" src="https://github.com/willtheorangeguy/pbs-monitoring/actions/workflows/testing.yml/badge.svg">
</div>

<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#installation">Installation</a> •
  <a href="#usage">Usage</a> •
  <a href="#documentation">Documentation</a> •
  <a href="#support">Support</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#license">License</a>
</p>

<!-- Screenshot: after adding pbs-monitoring/overview.png to .github/icons/, replace this comment with ![Dashboard overview](https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/pbs-monitoring/overview.png). -->

A Grafana dashboard for PBS snapshots, datastore usage and recent backup age using natrontech/pbs-exporter.

## Key Features

- Snapshot counts and latest backup age by VM or CT.
- Datastore capacity and usage panels.
- Raw latest snapshot verification flags.
- Datastore and job selectors for focused views.

## Installation

natrontech/pbs-exporter with read-only Audit and DatastoreAudit permissions, Prometheus and Grafana. Install and configure the upstream natrontech/pbs-exporter with PBS credentials. Adapt examples/prometheus-scrape.yml, confirm pbs_up is available and import dashboards/pbs-backups.json. See [installation](docs/installation.md) for more detail.

## Usage

Import [pbs-backups.json](dashboards/pbs-backups.json) in Grafana using **Dashboards → New → Import**. Choose the data source and match the dashboard variables to your monitoring labels. See [dashboard usage](docs/usage.md).

## Documentation

Full documentation lives in [docs/](docs/README.md): [Quickstart](docs/quickstart.md) · [Configuration](docs/configuration.md) · [Architecture](docs/architecture.md) · [Dashboard usage](docs/usage.md) · [Troubleshooting](docs/troubleshooting.md).

## Support

Open a [GitHub Discussion](https://github.com/willtheorangeguy/pbs-monitoring/discussions/new) or file an [issue](https://github.com/willtheorangeguy/pbs-monitoring/issues/new/choose).

## Contributing

Contributions welcome. See the org-wide [Contributing Guide](https://github.com/willtheorangeguy/.github/blob/main/CONTRIBUTING.md) and [Code of Conduct](https://github.com/willtheorangeguy/.github/blob/main/CODE_OF_CONDUCT.md).

## License

MIT — see [LICENSE.md](LICENSE.md).
