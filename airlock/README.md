### Rocket.Chat Airlock (`rocketchat-airlock`)

The Airlock operator manages data access and workspace-specific MongoDB clusters.

* **Description:** Airlock operator for data access management.
* **Version:** `0.0.1-z1`

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `AIRLOCK_ADMIN_USER` | The admin user for workspaces cluster | `workspaces-admin` | Yes |
| `AIRLOCK_ADMIN_PASSWORD` | The admin password for workspaces cluster | `b4n4n4-5up3r` | Yes |

**Deployment Example:**

```bash
zarf package deploy zarf-package-rocketchat-airlock-*.tar.zst --set AIRLOCK_ADMIN_PASSWORD=my-pass --confirm # using MDB pkg built-in user

```
