<div align="center">

# Hi, I'm Aniket Kumar 👋

**DevOps Engineer — Azure, Terraform, Kubernetes**

I build small Azure environments in Terraform and spend most of my effort on the security and CI side of them. Getting a change to deploy is the easy part. Getting it to deploy safely is the part worth doing properly.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)

</div>

<br>

## About Me

I'm a BCA graduate (Chandigarh Group of Colleges, Mohali) currently doing a DevOps internship at **DevOps Insiders**, where I write Terraform modules, build CI/CD pipelines, and help keep dev/QA/staging environments in sync for a small team.

Outside of that role, I build Azure and Terraform projects on my own time to go deeper on things I don't always get to at work — landing zone patterns, private AKS clusters, pipelines that stop a bad change instead of just logging it after the fact.

None of this is production infrastructure with real traffic. It's self-built and sized for one person to run and re-run, but I've tried to carry over the patterns a real environment needs: private networking, scoped access, gates before apply. That judgment is what I'm actually trying to build.

<br>

## 🧰 Stack

<table>
<tr>
<td valign="top" width="50%">

**Cloud**
<br>
<img src="https://skillicons.dev/icons?i=azure" height="32"/>

Azure, Azure DevOps, Entra ID — day-to-day comfortable with these

**Infrastructure as Code**
<br>
<img src="https://skillicons.dev/icons?i=terraform" height="32"/>

Terraform (main tool I use), some Bicep, Ansible for config management on a couple of projects

**Containers & Orchestration**
<br>
<img src="https://skillicons.dev/icons?i=docker,kubernetes" height="32"/>

Docker, Kubernetes (AKS), Helm, ArgoCD

</td>
<td valign="top" width="50%">

**CI/CD**
<br>
<img src="https://skillicons.dev/icons?i=githubactions,jenkins" height="32"/>

Azure Pipelines, GitHub Actions, a bit of Jenkins

**Security scanning**

Trivy and Checkov in pipelines, SonarQube for code quality, Key Vault for secrets. HashiCorp Vault I've only used in a sandbox — not comfortable calling that a strength yet.

**Monitoring**
<br>
<img src="https://skillicons.dev/icons?i=prometheus,grafana" height="32"/>

Prometheus + Grafana, provisioned alongside infra rather than bolted on after

**Languages & VCS**
<br>
<img src="https://skillicons.dev/icons?i=python,bash,git,github" height="32"/>

Python and Bash for scripting/automation, Git daily

</td>
</tr>
</table>

<br>

## 💼 Experience

**DevOps Intern — DevOps Insiders** _ Noida India

- Wrote Terraform modules to provision Azure resource groups, VNets, and VMs for dev, QA, and staging — replacing manual portal setup with version-controlled, repeatable infra.
- Built and maintained GitHub Actions and Azure DevOps pipelines for 3+ microservices (build, test, deploy stages on PRs and merges).
- Diagnosed environment/integration issues — config drift, dependency mismatches, failed deployments — with a 4-person team.
- Added automated test stages ahead of deployment steps, surfacing failures before builds reached staging.

<br>

## 🚀 Projects

Three projects here instead of a longer list of smaller ones — grouping the pieces that actually run together (the AKS cluster, how it gets deployed to, how it's monitored) felt more honest than presenting them as separate demos.

<br>

### 1. Azure Landing Zone in Terraform
🔗 [Repo](https://github.com/aniket-devop/azure-landing-zone-terraform)

Started because I kept copy-pasting the same networking module between two "environments." Rebuilt as a proper hub-and-spoke setup instead.

```mermaid
flowchart TB
    subgraph MG["Management Group: mg-platform"]
        subgraph SUB["Subscription: sub-platform-prod"]
            subgraph HUB["Hub VNet — 10.0.0.0/16"]
                FW["Azure Firewall"]
                BASTION["Azure Bastion"]
                SHARED["Shared Services"]
            end
            subgraph SPOKE["Spoke VNet — 10.1.0.0/16"]
                subgraph NSGB["NSG boundary"]
                    AKSC["AKS Cluster"]
                end
                KV["Key Vault"]
                RBAC["RBAC — scoped per RG"]
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

**What I went with, and why:**
- Hub-and-spoke instead of one flat network, so the firewall and Bastion live in one place instead of every spoke reinventing them.
- NSGs at the spoke boundary (deny-by-default, explicit allow) so the AKS subnet isn't just trusting whatever's on the VNet.
- Bastion instead of a jump box with a public IP — a mistake in an earlier version of this project I fixed on purpose here.
- RBAC scoped to the resource group, not the subscription.
- Firewall rule collections + UDRs forcing spoke egress through the firewall.
- Key Vault behind a private endpoint with a Private DNS zone for internal resolution.
- Remote state in Azure Storage with locking; `terraform fmt/validate/plan` on every PR with a manual approval gate before apply.

Parameterized enough that a second "environment" is a tfvars change, not a duplicated module. That was the actual goal, more than the security stuff, if I'm honest.

<br>

### 2. Private AKS Platform — cluster, deployments, and observability together
🔗 *Repo link once pushed / share on request*

The biggest of the three — kept adding to it instead of starting something new each time I learned a bit more. Started as "can I stand up an AKS cluster without a public API server," and grew to cover deployment and observability too.

**The cluster itself**

Default AKS quickstart tutorials leave the API server public and use a service principal secret for pulling from ACR. I wanted to avoid both.

```mermaid
flowchart TD
    ROOT["Root Module"] --> NET["Networking"]
    NET --> SEC["Security"]
    SEC --> ID["Identity"]
    ID --> AKSM["AKS"]
    AKSM --> MON["Monitoring"]

    classDef mod fill:#e6d9f2,stroke:#7B42BC,stroke-width:2px
    class ROOT,NET,SEC,ID,AKSM,MON mod
```

```mermaid
flowchart LR
    subgraph VNET["Private VNet — 10.2.0.0/16"]
        subgraph APISUB["Private API Server Subnet"]
            API["AKS API Server (private endpoint only)"]
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
    ACR["Azure Container Registry"]
    MI["Managed Identity"]
    MON2["Azure Monitor"]

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

The module split (networking → security → identity → AKS → monitoring) came out of trial and error, not planning — Terraform kept trying to create resources out of order because of implicit dependencies I hadn't thought through. Splitting fixed that.

Core goal: AKS talking to ACR through a managed identity — nothing to rotate, nothing that could leak in a `.tfvars` file by accident. Private endpoints for ACR and Key Vault so nothing goes over the public endpoint even inside the VNet.

**Getting things onto the cluster — ArgoCD + Helm**

```mermaid
flowchart LR
    DEV["Developer"] --> REPO["Git Repo (Helm charts)"]
    REPO -->|pushes| ARGOCD["ArgoCD"]
    ARGOCD -->|syncs| PODS["Application Pods"]
    ARGOCD -.watches drift.-> CLUSTER["AKS Cluster"]

    classDef gitops fill:#e6d9f2,stroke:#7B42BC,stroke-width:2px
    classDef cluster fill:#eaf2fb,stroke:#0078D4,stroke-width:2px
    class ARGOCD,REPO gitops
    class CLUSTER,PODS cluster
```

Helm charts hold desired state; ArgoCD reconciles the cluster against them and flags drift with automated self-healing, instead of me finding out something changed when a pod is already crash-looping. Dev/staging/prod configs are managed from a single repo via Helm value overrides and ApplicationSets, with rollback via ArgoCD's revision history when a deploy goes bad.

**Knowing what's happening — Prometheus + Grafana**

```mermaid
flowchart LR
    AKSM["AKS"] --> PROM["Prometheus"]
    PROM --> GRAFANA["Grafana"]
    GRAFANA --> DASH["Dashboards"]
    GRAFANA --> ALERT["Alerts"]

    classDef aks fill:#eaf2fb,stroke:#0078D4,stroke-width:2px
    classDef prom fill:#fde8e6,stroke:#c0392b,stroke-width:2px
    classDef graf fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    classDef out fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px
    class AKSM aks
    class PROM prom
    class GRAFANA graf
    class DASH,ALERT out
```

Prometheus and Grafana are provisioned by the same Terraform run as the cluster, tracking pod health, CPU/memory, and request latency from the first `apply`. Alerting is still just the defaults — building out real alert rules is next.

**What I haven't done:** no real load testing, and I haven't tried to break private endpoint routing or ArgoCD sync under actual traffic. Everything above has only run with a couple of test pods.

<br>

### 3. Azure DevOps CI/CD + DevSecOps Pipeline
🔗 *Repo link once pushed / share on request*

Most pipeline examples I found online run security scans after you've already applied. By then the scan is just telling you what you already broke.

```mermaid
flowchart LR
    GIT["Git Push"] --> VAL["Terraform Validate"]
    VAL --> PLAN["Terraform Plan"]
    PLAN --> GATE

    subgraph GATE["Security Gate"]
        direction TB
        CHECKOV["Checkov — IaC scan"]
        TRIVY["Trivy — vuln scan"]
        SONAR["SonarQube — quality gate"]
    end

    GATE --> APPROVE["Manual Approval"]
    APPROVE --> APPLY["Terraform Apply"]
    APPLY --> AZURE["Azure"]
    AZURE --> MON["Monitoring"]

    classDef tf fill:#e6d9f2,stroke:#7B42BC,stroke-width:2px
    classDef gate fill:#fde8e6,stroke:#c0392b,stroke-width:2px
    classDef approve fill:#fff2cc,stroke:#d6b656,stroke-width:2px
    classDef azure fill:#dae8fc,stroke:#0078D4,stroke-width:2px
    class VAL,PLAN,APPLY tf
    class GATE,CHECKOV,TRIVY,SONAR gate
    class APPROVE approve
    class AZURE,MON azure
```

This pipeline runs Checkov and Trivy against the `terraform plan` output before anything gets created, plus a SonarQube quality gate — if any of them fail, the pipeline stops. An early version just warned and continued, which defeats the point.

There's a manual approval step between plan and apply, kept deliberately rather than automated away. During the internship, a Terraform apply once did something I hadn't expected — since then I want a moment to actually read the plan output before anything changes.

This pipeline (commit → build → scan → quality gate → deploy → monitor) is what deploys the landing zone and AKS platform above. It's not a standalone demo, it's the gate for both.

<br>

## 📊 GitHub Activity

<div align="center">
<table>
<tr>
<td><img src="https://github-readme-stats.vercel.app/api?username=aniket-devop&show_icons=true&theme=tokyonight&hide_border=true" height="165"/></td>
<td><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aniket-devop&layout=compact&theme=tokyonight&hide_border=true" height="165"/></td>
</tr>
</table>
</div>

<br>

## 🔭 What I'm working on right now

- Azure Policy at the landing-zone level — governance I skipped the first time around
- OPA / Kyverno for admission control on the AKS project
- Actually testing Terraform modules instead of just running `plan` and eyeballing it
- Looking at Crossplane as an alternative to the provider modules I've been using — no strong opinion yet

<br>

## 📫 Contact

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)

</div>

