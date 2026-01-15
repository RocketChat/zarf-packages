### Cert Manager (`rocketchat-cert-manager`)

Provides automated TLS certificate management within the cluster.

* **Description:** Certificate management utilizing Jetstack's cert-manager.
* **Version:** `1.18.2-z1`

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `CERTMANAGER_CA_ISSUER_SECRET_NAME` | Internal CA issuer secret name expected in cert-manager namespace | `root-secret` | Yes |
| `CERTMANAGER_SELFSIGNED_CA_COMMON_NAME` | Default self-signed CA common name | `Rocket.Chat/Zarf built-in` | Yes |
| `CERTMANAGER_WEBHOOK` | Specific configuration for the cert-manager webhook | `{hostNetwork: true, securePort: 10260}` | No |

**Deployment Example:**

```bash
zarf package deploy zarf-package-rocketchat-cert-manager-*.tar.zst --confirm

```
