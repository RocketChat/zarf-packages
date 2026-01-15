### Launch Control (`rocketchat-launchcontrol`)

The core operator responsible for managing Rocket.Chat server instances.

* **Description:** Rocket.Chat server operator.
* **Version:** `0.0.1-z1`

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `LAUNCHCONTROL_CLUSTER_ISSUER` | A cert-manager's ClusterIssuer name to be used for TLS ingress | `ca-issuer` | No |

**Deployment Example:**

```bash
zarf package deploy zarf-package-rocketchat-launchcontrol-*.tar.zst  --confirm # using CM pkg built-in issuer

```
