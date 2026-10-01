# pbs-monitoring — Dashboard Usage

Import the JSON files using **Grafana → Dashboards → New → Import**. Set the data source and variables listed in [configuration](./configuration.md).

## Proxmox Backup Server

Source: [pbs-backups.json](../dashboards/pbs-backups.json). Refresh: `30s`.

<!-- Screenshot: after adding pbs-backups.png to .github/icons/pbs-monitoring/, replace this comment with ![Proxmox Backup Server](https://raw.githubusercontent.com/willtheorangeguy/.github/main/icons/pbs-monitoring/pbs-backups.png). -->

### Panels

| Panel | Type | What it shows |
|---|---|---|
| PBS API / Exporter | stat | See the query reference below. |
| Total Snapshots | stat | See the query reference below. |
| Protected VM / CT Entries | stat | Distinct snapshot groups in the selected datastore(s); the same VM ID on two PVE hosts may represent different machines. |
| Newest Snapshot Age | stat | See the query reference below. |
| Snapshots Over 48h Old | stat | Counts per-VM last snapshots older than 48 hours; not a backup-job failure count. |
| Last-Snapshot Verify Flag = 0 | stat | Raw exporter verify flag for each VM's latest snapshot. Zero is not assumed to mean a failed verification; unverified or pending snapshots may also be zero. |
| Snapshot Count by Datastore | timeseries | See the query reference below. |
| Datastore Capacity | timeseries | Used and available bytes by datastore. Separate datastores may share a backing filesystem; do not sum these as physical capacity. |
| Highest Datastore Usage | bargauge | Highest reported datastore use percentage; not a sum of physical storage. |
| Lowest Datastore Available Space | stat | See the query reference below. |
| Largest Datastore Size | stat | See the query reference below. |
| Latest Snapshot by VM / CT | table | Unix snapshot time converted to Grafana milliseconds. Verify flag is the exporter's raw latest-snapshot state, not a failure count. |
| Snapshot Count by VM / CT | table | See the query reference below. |
| Snapshot Count by Datastore | bargauge | See the query reference below. |
| Latest Snapshot Age by Datastore | timeseries | Age of newest VM snapshot in each datastore. |

<!-- Screenshot: add a focused panel or section image here after uploading it to .github/icons/pbs-monitoring/. -->

### Reading the results

Datastores can share backing storage, so summing per-datastore capacity can double count physical space. A latest-snapshot verify flag of zero can mean unverified or pending; it is not necessarily a failed verification. The dashboard adapts the pbs-exporter maintainer dashboard; retain attribution.

### Query reference

These expressions are copied from the dashboard JSON. Grafana substitutes the dashboard variables at runtime.

#### PBS API / Exporter

```promql
pbs_up{job="${job_pbs}"} * on(job, instance) up{job="${job_pbs}"}
```

#### Total Snapshots

```promql
sum(pbs_snapshot_count{job="${job_pbs}",datastore=~"$datastore"})
```

#### Protected VM / CT Entries

```promql
count(pbs_snapshot_vm_count{job="${job_pbs}",datastore=~"$datastore"})
```

#### Newest Snapshot Age

```promql
time() - max(pbs_snapshot_vm_last_timestamp{job="${job_pbs}",datastore=~"$datastore"})
```

#### Snapshots Over 48h Old

```promql
count((time() - pbs_snapshot_vm_last_timestamp{job="${job_pbs}",datastore=~"$datastore"}) > 172800) or vector(0)
```

#### Last-Snapshot Verify Flag = 0

```promql
count(pbs_snapshot_vm_last_verify{job="${job_pbs}",datastore=~"$datastore"} == 0) or vector(0)
```

#### Snapshot Count by Datastore

```promql
sum by (datastore) (pbs_snapshot_count{job="${job_pbs}",datastore=~"$datastore"})
```

#### Datastore Capacity

```promql
max by (datastore) (pbs_used{job="${job_pbs}"})
max by (datastore) (pbs_available{job="${job_pbs}"})
```

#### Highest Datastore Usage

```promql
max(100 * pbs_used{job="${job_pbs}"} / pbs_size{job="${job_pbs}"})
```

#### Lowest Datastore Available Space

```promql
min(pbs_available{job="${job_pbs}"})
```

#### Largest Datastore Size

```promql
max(pbs_size{job="${job_pbs}"})
```

#### Latest Snapshot by VM / CT

```promql
pbs_snapshot_vm_last_timestamp{job="${job_pbs}",datastore=~"$datastore"} * 1000
pbs_snapshot_vm_last_verify{job="${job_pbs}",datastore=~"$datastore"}
```

#### Snapshot Count by VM / CT

```promql
pbs_snapshot_vm_count{job="${job_pbs}",datastore=~"$datastore"}
```

#### Snapshot Count by Datastore

```promql
sum by (datastore) (pbs_snapshot_count{job="${job_pbs}",datastore=~"$datastore"})
```

#### Latest Snapshot Age by Datastore

```promql
time() - max by (datastore) (pbs_snapshot_vm_last_timestamp{job="${job_pbs}",datastore=~"$datastore"})
```
