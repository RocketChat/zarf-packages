# Rocket.Chat Zarf Packages

This repository contains a collection of **Zarf packages** designed to deploy and manage a complete Rocket.Chat ecosystem in air-gapped or restricted environments.
Zarf is an open-source tool designed to simplify the delivery of software into air-gapped, secure, or highly regulated environments by bundling all necessary dependencies into [packages](https://docs.zarf.dev/ref/packages/).

## Deploying packages

It is recommended that your Kubernetes cluster contains  at least 3 nodes with 2 vCPUs, 6 GiB memory and 100G disk each.
For testing, you can decrease storage and mongod limits. There's a README.md in each package folder with variables and defaults.

### Init the cluster

```
KUBECONFIG=<kubeconfig> zarf init [--storage-class longhorn] [--confirm]
```

If there's no reliable storage class in the target cluster, init with what you have, then:
```
KUBECONFIG=<kubeconfig> zarf package deploy zarf-package-rocketchat-longhorn-*.tar.zst --components migrate-registry --confirm # move to longhorn
```

### Deploying

Deploy in order:
- monitoring (requires a storage class)
- traefik
- cert-manager
- mongodb-kubernetes (requires a storage class)
- airlock
- launchcontrol (requires airlock)
- server-workspace (requires launchcontrol)

#### High-level architectural diagram

```mermaid
graph TD
    %% Define external actor
    User[External User / Client]

    %% Define the Cluster Boundary
    subgraph Kubernetes Cluster
        
        %% --- EDGE LAYER ---
        subgraph Edge Layer
            Traefik(rocketchat-traefik\nIngress Controller)
            CertMgr(rocketchat-cert-manager\nCertificate Management)
        end

        %% --- MANAGEMENT LAYER (Operators) ---
        subgraph Management Operators
            LaunchControl(rocketchat-launchcontrol\nRC Server Operator)
            Airlock(rocketchat-airlock\nData Access Operator)
        end

        %% --- DATA LAYER ---
        subgraph Data Layer
            Mongo(rocketchat-mongodb\nDatabase Cluster)
        end

        %% --- APPLICATION LAYER ---
        subgraph Application Layer
            RCWorkspace[rocketchat-server-workspace\nRocket.Chat Microservices]
        end
        
        %% --- OBSERVABILITY LAYER ---
        subgraph Observability
            Monitoring(rocketchat-monitoring\nPrometheus & Grafana)
        end
    end

    %% --- CONNECTIONS ---

    %% Traffic Flow (Solid Lines)
    User == HTTPS Traffic ==> Traefik
    Traefik == Routes Request ==> RCWorkspace
    RCWorkspace == Reads/Writes Data ==> Mongo

    %% Supporting Services & Control Plane (Dotted Lines)
    CertMgr -.->|Provides TLS Certs| Traefik
    LaunchControl -.->|Manages Deployment| RCWorkspace
    Airlock -.->|Provisions DB Credentials| Mongo
    
    %% Monitoring connections (Simplified for readability)
    Monitoring -.->|Scrapes Metrics| Traefik
    Monitoring -.->|Scrapes Metrics| Mongo
    Monitoring -.->|Scrapes Metrics| RCWorkspace

    %% Styling for clarity
    classDef operator fill:#f9f,stroke:#333,stroke-width:2px,color:black;
    class LaunchControl,Airlock operator;
    
    classDef db fill:#ff9,stroke:#333,stroke-width:2px,color:black;
    class Mongo db;

    classDef ingress fill:#cce5ff,stroke:#333,stroke-width:2px,color:black;
    class Traefik ingress;
```

---

## Developers: Getting Started

Most likely you'll need a lab setup.
There's a guide for developing Zarf packages https://rocketchat.atlassian.net/wiki/spaces/RnD/pages/756842503/Developing+Rocket.Chat+Zarf+packages

---

That's all for now, folks!
