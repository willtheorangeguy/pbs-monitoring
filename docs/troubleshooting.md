# pbs-monitoring — Troubleshooting

| Symptom | Check |
|---|---|
| Panels blank | check pbs_up, exporter reachability and job_pbs. |
| Datastore selector empty | inspect pbs_snapshot_count labels. |
| Old snapshot count high | check each VM or CT latest timestamp; the panel does not indicate backup-job failures. |

## First checks

Check the selected Grafana data source and dashboard variables in [configuration](./configuration.md). For Prometheus, inspect the target state and the exact job and instance labels before changing panel queries.
