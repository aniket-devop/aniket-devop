<div align="center">

# Aniket Kumar

**Azure DevOps Engineer · DevSecOps · Platform Automation**

I design Azure infrastructure as Terraform modules, then gate every change through security scanning and policy checks before it reaches `apply`.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)

![Profile Views](https://komarev.com/ghpvc/?username=aniket-devop&style=flat-square&color=blue)

</div>

<br>

## About

My focus is Azure infrastructure built with Terraform, with DevSecOps controls (Trivy, Checkov, SonarQube) enforced as pipeline gates rather than post-deployment audits. I treat infrastructure like application code: modularized, version-controlled, and reviewed before it ships.

These are self-built projects, not enterprise production systems — each one is designed to reflect the patterns a real production environment would need (private networking, least-privilege access, policy gates), so that's the level of judgment on display here, not the scale.

<br>

## Stack

<table>
<tr>
<td valign="top" width="50%">

**Cloud**
<br>
<img src="https://skillicons.dev/icons?i=azure" height="32"/>

Azure · Azure DevOps · Azure Entra ID

**Infrastructure as Code**
<br>
<img src="https://skillicons.dev/icons?i=terraform" height="32"/>

Terraform · Bicep · Ansible

**Containers & Orchestration**
<br>
<img src="https://skillicons.dev/icons?i=docker,kubernetes" height="32"/>

Docker · Kubernetes · Helm · ArgoCD

</td>
<td valign="top" width="50%">

**CI/CD**
<br>
<img src="https://skillicons.dev/icons?i=githubactions,jenkins" height="32"/>

Azure Pipelines · GitHub Actions · Jenkins

**DevSecOps**

Trivy · Checkov · SonarQube · Azure Key Vault · HashiCorp Vault (basics)

**Monitoring**
<br>
<img src="https://skillicons.dev/icons?i=prometheus,grafana" height="32"/>

Prometheus · Grafana

**Languages & VCS**
<br>
<img src="https://skillicons.dev/icons?i=python,bash,git,github" height="32"/>

</td>
</tr>
</table>

<br>

## Featured Repositories

> Fill in the `Repository` and `Stack` columns with real links once pinned. Structure only — no repo names invented below.

| # | Repository | Stack | What it demonstrates |
|---|---|---|---|
| 1 | _[link]_ | Terraform · Azure | CAF-aligned landing zone, hub-and-spoke networking |
| 2 | _[link]_ | Terraform · AKS | Private cluster, managed identity, no static credentials |
| 3 | _[link]_ | Azure Pipelines · Trivy · Checkov · SonarQube | Security scans as hard gates before `apply` |
| 4 | _[link]_ | ArgoCD · Helm · Kubernetes | Git-reconciled deployments, drift correction |
| 5 | _[link]_ | Prometheus · Grafana | Metrics and dashboards provisioned with infra |

<br>

## Projects

### Azure Landing Zone — Terraform

**Problem:** A landing zone is only useful if teams can extend it without copy-pasting Terraform. A single monolithic config doesn't survive a second environment.

**Architecture:**

```mermaid
flowchart TB
    subgraph MG["📁 Management Group: mg-platform"]
        subgraph SUB["🔷 Subscription: sub-platform-prod"]
            subgraph HUB["🔵 Hub VNet — 10.0.0.0/16"]
                FW["🛡️ Azure Firewall"]
                BASTION["🔑 Azure Bastion"]
                SHARED["⚙️ Shared Services"]
            end
            subgraph SPOKE["🟢 Spoke VNet — 10.1.0.0/16"]
                subgraph NSGB["NSG boundary"]
                    AKSC["☸️ AKS Cluster"]
                end
                KV["🔐 Key Vault"]
                RBAC["👤 RBAC — scoped per RG"]
            end
        end
    end

    HUB -.VNet Peering.- SPOKE
    FW -."controls egress".-> NSGB

    classDef hub fill:#eaf2fb,stroke:#0078D4,stroke-width:2px
    classDef spoke fill:#eafaf1,stroke:#2e7d32,stroke-width:2px
    classDef mg fill:#f5f5f5,stroke:#6c8ebf,stroke-width:1px,stroke-dasharray: 4 3
    class HUB hub
    class SPOKE,NSGB spoke
    class MG,SUB mg
```

> Rendered inline for GitHub compatibility. For the full presentation-quality version with official Azure icons, hub/spoke containers, and boundary styling matching Azure Architecture Center — see [`diagrams/landing-zone-architecture.drawio`](diagrams/landing-zone-architecture.drawio), importable directly into [diagrams.net](https://app.diagrams.net).
>
> **PNG layout (what the exported render looks like):** A dashed gray outer boundary labeled "Management Group," containing a dashed amber boundary labeled "Subscription." Inside, two solid containers side by side — a blue-bordered Hub VNet (left) with Firewall, Bastion, and Shared Services icons stacked vertically, and a green-bordered Spoke VNet (right) with an NSG sub-boundary wrapping the AKS icon, plus a Key Vault icon and RBAC label below it. A dashed peering line connects the two VNet containers; a solid arrow runs from the Firewall icon into the NSG boundary labeled "controls egress."

**Design decisions:**
- Structured around Microsoft's Cloud Adoption Framework rather than an ad-hoc layout, so the resource hierarchy matches what a reviewer coming from another CAF-based environment would already expect
- Hub-and-spoke networking with NSGs at the spoke boundary — segmentation is enforced at the network layer, not left to convention
- Azure Bastion instead of public IPs/jump boxes on VMs — removes an entire class of exposed-management-port misconfiguration
- RBAC scoped per resource group, not subscription-wide — least privilege as a default, not an afterthought

**Security considerations:**
- No public IPs on management interfaces — Bastion is the only path to compute
- Firewall sits in the hub and mediates spoke egress rather than each spoke managing its own perimeter
- Key Vault access policies scoped to the identities that need them, not broadly granted

**Outcome:** A set of parameterized Terraform modules that can stand up a new environment (dev/stage/prod-shaped) by changing variables, not rewriting configuration.

| Component | Implementation |
|---|---|
| Networking | Hub-and-spoke, NSGs, Azure Bastion |
| Identity & Access | RBAC, least-privilege scoping |
| Secrets | Azure Key Vault |
| Structure | Resource organization by environment boundary |
| Reusability | Modularized, parameterized Terraform |

**Repository:** _[link placeholder — add once pinned]_
**Documentation:** _[README / architecture doc placeholder]_

### AKS Production Infrastructure — Terraform

**Problem:** Default AKS quickstarts expose the API server publicly and use static credentials for registry access — neither is something a production cluster should ship with.

**Terraform module structure:**

```mermaid
flowchart TD
    ROOT["📦 Root Module"] --> NET["🌐 Networking"]
    NET --> SEC["🛡️ Security"]
    SEC --> ID["🪪 Identity"]
    ID --> AKSM["☸️ AKS"]
    AKSM --> MON["📊 Monitoring"]

    classDef mod fill:#e6d9f2,stroke:#7B42BC,stroke-width:2px
    class ROOT,NET,SEC,ID,AKSM,MON mod
```

**Network architecture:**

```mermaid
flowchart LR
    subgraph VNET["🔵 Private VNet — 10.2.0.0/16"]
        subgraph APISUB["Private API Server Subnet"]
            API["☸️ AKS API Server&#10;(private endpoint only)"]
        end
        subgraph NODESUB["Node Subnet"]
            SYS["System Node Pool"]
            USR["User Node Pool"]
        end
        subgraph PESUB["Private Endpoints Subnet"]
            ACRPE["ACR Private Endpoint"]
            KVPE["Key Vault Private Endpoint"]
        end
    end
    ACR["📦 Azure Container Registry"]
    MI["🪪 Managed Identity"]
    MON2["📊 Azure Monitor"]

    USR -->|pulls images via| ACRPE
    ACRPE -.-> ACR
    USR -->|authenticates via| MI
    MI -.no stored credentials.-> ACR
    NODESUB -->|metrics| MON2

    classDef vnet fill:#eaf2fb,stroke:#0078D4,stroke-width:2px
    classDef ext fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    class VNET,APISUB,NODESUB,PESUB vnet
    class ACR,MI,MON2 ext
```

> For the presentation-quality version with official Azure icons and subnet-level boundaries — see [`diagrams/aks-architecture.drawio`](diagrams/aks-architecture.drawio).
>
> **PNG layout:** A blue-bordered VNet container split into three dashed sub-boundaries stacked vertically — a private API server subnet, a node subnet showing System and User node pool boxes side by side, and a private endpoints subnet with ACR and Key Vault private-endpoint icons. To the right, outside the VNet, sit the Container Registry icon, a Managed Identity box, and an Azure Monitor icon, each connected back into the VNet with labeled arrows ("pulls images via," "authenticates via," "no stored credentials").

**Design decisions:**
- Private networking for the control plane, closing off the most common AKS misconfiguration
- Managed Identity for AKS→ACR authentication instead of stored service principal credentials — nothing to rotate, nothing to leak
- Monitoring provisioned in the same Terraform run as the cluster, so observability isn't a manual step someone forgets after the fact
- Module ordering follows a strict dependency chain — identity exists before AKS references it, monitoring attaches only after the cluster is up

**Security considerations:**
- No static credentials anywhere in the AKS↔ACR trust path
- Control plane not reachable from the public internet
- Each module only receives the inputs it needs, not the full variable set

**Outcome:** An AKS + ACR pair where the trust relationship is identity-based end to end, provisioned as one reproducible Terraform apply.

**Repository:** _[link placeholder — add once pinned]_
**Documentation:** _[README / architecture doc placeholder]_

### Azure DevOps CI/CD Pipeline

**Problem:** Security scanning that runs *after* deployment only tells you what already broke. The gate needs to sit before `apply`, not after.

**Pipeline flow:**

```mermaid
flowchart LR
    GIT["📝 Git Push"] --> VAL["Terraform Validate"]
    VAL --> PLAN["Terraform Plan"]
    PLAN --> GATE

    subgraph GATE["🛡️ Security Gate — fails closed"]
        direction TB
        CHECKOV["Checkov&#10;IaC static analysis"]
        TRIVY["Trivy&#10;vulnerability scan"]
        SONAR["SonarQube&#10;quality gate"]
    end

    GATE --> APPROVE["✅ Manual Approval"]
    APPROVE --> APPLY["Terraform Apply"]
    APPLY --> AZURE["☁️ Azure"]
    AZURE --> MON["📊 Monitoring"]

    classDef tf fill:#e6d9f2,stroke:#7B42BC,stroke-width:2px
    classDef gate fill:#fde8e6,stroke:#c0392b,stroke-width:2px
    classDef approve fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    classDef azure fill:#dae8fc,stroke:#0078D4,stroke-width:2px
    class VAL,PLAN,APPLY tf
    class GATE,CHECKOV,TRIVY,SONAR gate
    class APPROVE approve
    class AZURE,MON azure
```

> For the presentation-quality version with a dedicated gate boundary and Azure-style edge coloring — see [`diagrams/cicd-pipeline-architecture.drawio`](diagrams/cicd-pipeline-architecture.drawio).
>
> **PNG layout:** A horizontal left-to-right flow — Git Push, Terraform Validate, Terraform Plan — feeding into a red-dashed "Security Gate" boundary containing Checkov, Trivy, and SonarQube stacked vertically. The gate exits into a single amber Manual Approval box, then Terraform Apply, then an Azure box, then a Monitoring icon. A dashed red line labeled "fails closed" runs from the gate directly to the approval step, visually reinforcing that any scan failure blocks progression.

**Design decisions:**
- Trivy and Checkov run against the Terraform plan output, not the live infrastructure — issues get caught before anything is provisioned
- SonarQube quality gates block on code smell / maintainability thresholds, not just pass/fail test results
- Manual approval sits between `plan` and `apply` deliberately — automated gates catch known issues, but infra changes still get a human review before they're irreversible

**Security considerations:**
- Static analysis runs before any resource is created, not after
- Approval gate means no single automated failure — or single reviewer — can push infra to `apply` alone
- Pipeline fails closed: any scan failure blocks progression by default

**Outcome:** No infrastructure change reaches `apply` without passing static analysis and a human sign-off — the pipeline enforces this, not a checklist.

**Repository:** _[link placeholder — add once pinned]_
**Documentation:** _[README / pipeline doc placeholder]_

### GitOps Deployment — ArgoCD + Helm

**Problem:** Manual `kubectl apply` means cluster state and Git history diverge silently over time, and nobody notices until something breaks.

**Workflow:**

```mermaid
flowchart LR
    DEV["👤 Developer"] --> REPO["📁 Git Repository&#10;Helm charts, desired state"]
    REPO -->|pushes| ARGOCD["🔄 ArgoCD&#10;continuous reconciliation"]

    subgraph CLUSTER["☸️ AKS Cluster"]
        PODS["Application Pods"]
        PROM["Prometheus"]
        GRAFANA["Grafana"]
        PODS -->|metrics| PROM
        PROM -->|dashboards| GRAFANA
    end

    ARGOCD -->|syncs / reconciles| PODS
    ARGOCD -.watches drift.-> CLUSTER

    classDef gitops fill:#e6d9f2,stroke:#7B42BC,stroke-width:2px
    classDef cluster fill:#eaf2fb,stroke:#0078D4,stroke-width:2px
    class ARGOCD,REPO gitops
    class CLUSTER,PODS,PROM,GRAFANA cluster
```

> For the presentation-quality version — see [`diagrams/gitops-architecture.drawio`](diagrams/gitops-architecture.drawio).
>
> **PNG layout:** Developer → Git Repository → ArgoCD flowing left to right, then a blue-bordered AKS Cluster boundary on the right containing Application Pods, Prometheus, and Grafana connected in sequence. A solid arrow runs from ArgoCD into the pods labeled "syncs / reconciles"; a dashed arrow loops from ArgoCD to the cluster boundary labeled "watches drift," visually showing continuous reconciliation rather than a one-time deploy.

**Design decisions:**
- Helm charts define desired state as versioned, reviewable artifacts instead of imperative commands
- ArgoCD continuously reconciles live cluster state against Git — drift is corrected automatically rather than discovered during an incident

**Security considerations:**
- No direct `kubectl` access needed for deployment — reduces the number of credentials with cluster-write access
- ArgoCD's sync state gives an audit trail of what changed and when, tied back to a Git commit

**Outcome:** Git is the actual source of truth for what's running, not a record of what was *supposed* to be applied.

**Repository:** _[link placeholder — add once pinned]_
**Documentation:** _[README / workflow doc placeholder]_

### Monitoring Stack — Prometheus + Grafana

**Problem:** Observability bolted on after infrastructure exists usually means half the metrics you need were never exposed.

**Architecture:**

```mermaid
flowchart LR
    AKSM["☸️ AKS"] --> PROM["Prometheus&#10;metrics scraping"]
    PROM --> GRAFANA["Grafana&#10;visualization"]
    GRAFANA --> DASH["📊 Dashboards"]
    GRAFANA --> ALERT["🔔 Alerts"]

    classDef aks fill:#eaf2fb,stroke:#0078D4,stroke-width:2px
    classDef prom fill:#fde8e6,stroke:#c0392b,stroke-width:2px
    classDef graf fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    classDef out fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px
    class AKSM aks
    class PROM prom
    class GRAFANA graf
    class DASH,ALERT out
```

> For the presentation-quality version — see [`diagrams/monitoring-architecture.drawio`](diagrams/monitoring-architecture.drawio).
>
> **PNG layout:** A simple left-to-right chain — AKS icon feeding into a red-bordered Prometheus box, into an amber-bordered Grafana box, which branches into two green-bordered outputs side by side: Dashboards and Alerts.

**Design decisions:**
- Prometheus and Grafana provisioned in the same IaC workflow as the infrastructure they monitor, so dashboards exist from day one instead of being retrofitted

**Outcome:** Metrics and dashboards ship with the infrastructure, not as a follow-up task.

**Repository:** _[link placeholder — add once pinned]_
**Documentation:** _[README / dashboard doc placeholder]_

<br>

## GitHub Activity

<div align="center">
<table>
<tr>
<td><img src="https://github-readme-stats.vercel.app/api?username=aniket-devop&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" height="165"/></td>
<td><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aniket-devop&layout=compact&theme=tokyonight&hide_border=true" height="165"/></td>
</tr>
</table>

<img src="https://github-readme-streak-stats.herokuapp.com/?user=aniket-devop&theme=tokyonight&hide_border=true"/>
</div>

<br>

## Engineering Principles

- Infrastructure is reviewed before it is deployed, not after.
- Security checks are enforced in the pipeline, not left to manual process.
- Identity-based access is preferred over stored secrets wherever the platform supports it.
- Repetitive operations get automated rather than repeated by hand.
- If it isn't reproducible from code, it isn't finished.

<br>

## Currently Working On

| Area | Specifically |
|---|---|
| Governance | Azure Policy at the landing-zone level |
| Kubernetes Security | OPA and Kyverno for admission control |
| Terraform | Module testing practices |
| Control Planes | Crossplane as an alternative to direct provider modules |

<br>

## Contact

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)

</div>


