# pbs-monitoring — Architecture

PBS API -> upstream pbs-exporter -> Prometheus -> Grafana dashboard.

## Components

- [dashboards/](../dashboards): Grafana dashboard definitions
- [examples/](../examples): deployment and scrape examples

## Data interpretation

Datastores can share backing storage, so summing per-datastore capacity can double count physical space. A latest-snapshot verify flag of zero can mean unverified or pending; it is not necessarily a failed verification. The dashboard adapts the pbs-exporter maintainer dashboard; retain attribution.
