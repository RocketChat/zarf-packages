### Server Workspace (`rocketchat-server-workspace`)

The actual Rocket.Chat application instance configuration.

* **Description:** Rocket.Chat workspace deployment.
* **Version:** `8.2.0-z1`

| Variable | Description | Default | Prompt |
| --- | --- | --- | --- |
| `WORKSPACE_MONGO_URL` | Connection string to MongoDB (Defaults to airlock) | `""` | No |
| `WORKSPACE_NAME` | The name of the workspace | `my-chat` | Yes |
| `WORKSPACE_ADDRESS` | The address to be used for ingress | `my-chat.my.local` | Yes |
| `WORKSPACE_ROCKETCHAT_REPLICAS` | Number of deployment replicas | `2` | No |
| `WORKSPACE_DDPSTREAMER_REPLICAS` | Number of deployment replicas | `1` | No |
| `WORKSPACE_ACCOUNTSERVICE_REPLICAS` | Number of deployment replicas | `1` | No |
| `WORKSPACE_AUTHORIZATIONSERVICE_REPLICAS` | Number of deployment replicas | `1` | No |
| `WORKSPACE_PRESENCESERVICE_REPLICAS` | Number of deployment replicas | `1` | No |
| `WORKSPACE_ENABLE_OMNI_TRANSCRIPT` | Enable the omni transcript alpha feature | `false` | No |
| `WORKSPACE_LABELS` | Deploy-specific labels | `{x-launchpad-monitoring: active}` | No |
| `WORKSPACE_CLOUD_ID` | Cloud registration ID | `""` | No |
| `WORKSPACE_CLOUD_CLIENT_ID` | Cloud workspace client ID | `zarf-offline` | No |
| `WORKSPACE_CLOUD_CLIENT_SECRET` | Cloud workspace client secret | `zarf-offline` | No |
| `WORKSPACE_CLOUD_PUBLIC_KEY` | Cloud workspace public key | `""` | No |
| `WORKSPACE_CLOUD_REGISTRATION_CLIENT_URI` | Cloud workspace client URI | `""` | No |
| `WORKSPACE_SHOW_SETUP_WIZARD` | Show setup wizard | `completed` | No |
| `WORKSPACE_LICENSE` | Workspace license | `""` | No |

**Deployment Example:**

```bash
zarf package deploy zarf-package-rocketchat-server-workspace-*.tar.zst --set WORKSPACE_NAME=hq-chat --set WORKSPACE_ADDRESS=chat.internal.corp --set WORKSPACE_LICENSE="$(cat license.txt)" --confirm # uses airlock

```
