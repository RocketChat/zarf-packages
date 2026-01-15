### MongoDB (`rocketchat-mongodb`)

Deploy the MongoDB Community Operator and the underlying database clusters used by Rocket.Chat.

* **Description:** MongoDB Controllers for Kubernetes (MCK) and workspaces CE cluster.
* **Version:** `1.6.1-z1`

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `DATABASE_STORAGECLASS_NAME` | The StorageClass name | `longhorn` | Yes |
| `DATABASE_MEMBERS` | The size of replica set | `3` | Yes |
| `DATABASE_MONGOD_CPU_LIMITS` | Mongod resource CPU limits | `1500m` | No |
| `DATABASE_MONGOD_MEMORY_LIMITS` | Mongod resource memory limits | `6Gi` | No |
| `DATABASE_MONGOD_CPU_REQUESTS` | Mongod resource CPU requests | `500m` | No |
| `DATABASE_MONGOD_MEMORY_REQUESTS` | Mongod resource memory requests | `3Gi` | No |
| `DATABASE_DATA_STORAGE_SIZE` | Data volume size | `30G` | Yes |
| `DATABASE_LOGS_STORAGE_SIZE` | Logs volume size | `2G` | No |
| `DATABASE_METRICS_PASSWORD_INTERNAL` | Password for internal monitoring stack | `randomly-auto-generated` | No |
| `DATABASE_ADMIN_PASSWORD` | The cluster admin password | `b4n4n4-5up3r` | Yes |

**Deployment Example:**

```bash
zarf package deploy zarf-package-rocketchat-mongodb-*.tar.zst --set DATABASE_DATA_STORAGE_SIZE=2G --confirm
```
