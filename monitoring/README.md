### Monitoring (`rocketchat-monitoring`)

Provides observability for the Rocket.Chat stack using Prometheus and Grafana.

* **Description:** A basic stack with Prometheus and Grafana.
* **Version:** `0.0.10-z1`

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `MONITORING_STORAGECLASS_NAME` | The StorageClass name | `longhorn` | Yes |
| `MONITORING_LOKI_RETENTION_PERIOD` | Logs older than this period are automatically deleted by the compactor | `15d` | Yes |
| `MONITORING_LOKI_PERSISTENCE_SIZE` | The total disk space allocated for storing logs. Hint: Size=(Daily Raw Volume×Retention Days×0.15)+Safety Buffer (20%) | `30Gi` | Yes |

**Deployment Example:**

```bash
zarf package deploy zarf-package-rocketchat-monitoring-*.tar.zst --confirm

```
