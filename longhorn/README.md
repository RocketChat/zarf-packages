### Longhorn (`rocketchat-longhorn`)

Provides a manager for persistent storage.

* **Description:** [Longhorn](https://longhorn.io/docs/1.10.1/what-is-longhorn/)
* **Version:** `1.10.1-z1`
* **Installation requirements (all nodes)**: https://longhorn.io/docs/1.10.1/deploy/install/#installing-open-iscsi

#### IMPORTANT: this package contains a migrate-registry component which can be used to ensure longhorn is the single default class and re-init Zarf cluster with a registry volume managed by longhorn. You *must* re-deploy this package to push longhorn images once again to the new volume.

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `-` | - | `-` | - |

**Deployment Example:**

```bash
# just install longhorn
zarf package deploy zarf-package-rocketchat-longhorn-*.tar.zst --confirm

# install and migrate-registry: run twice (important note above)
zarf package deploy zarf-package-rocketchat-longhorn-*.tar.zst --components migrate-registry --confirm

```
