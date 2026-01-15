### Monitoring (`rocketchat-monitoring`)

Provides observability for the Rocket.Chat stack using Prometheus and Grafana.

* **Description:** A basic stack with Prometheus and Grafana.
* **Version:** `0.0.9-z1`

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `MONITORING_STORAGECLASS_NAME` | The StorageClass name | `longhorn` | Yes |

**Deployment Example:**

```bash
zarf package deploy zarf-package-rocketchat-monitoring-*.tar.zst --confirm

```
