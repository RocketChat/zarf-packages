### Traefik (`rocketchat-traefik`)

The edge router and load balancer for the cluster.

* **Description:** Traefik loadbalancer.
* **Version:** `3.5.0-z1`

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `LOADBALANCER_SERVICE_TYPE` | The Kubernetes Service type for Traefik | `LoadBalancer` | No |
| `LOADBALANCER_SERVICE_ANNOTATIONS` | Cloud-specific annotations for Traefik | `{}` | No |

**Deployment Example:**

```bash
zarf package deploy zarf-package-rocketchat-traefik-*.tar.zst --confirm

```

