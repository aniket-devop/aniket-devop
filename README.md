<div align="center">

<img src="https://readme-typing-svg.demolab.com/?font=Fira+Code&size=26&duration=3000&pause=800&color=0078D4&center=true&vCenter=true&width=650&lines=Aniket+Kumar;DevOps+Engineer;Azure+%2B+Terraform+%2B+Kubernetes;I+ship+it+safely%2C+not+just+fast." alt="Typing SVG" />

</div>

<table width="100%">
<tr>
<td width="45%" valign="top">

### 📌 At a Glance

| | |
|---|---|
| 🎓 **Education** | BCA, Chandigarh Group of Colleges |
| 💼 **Current** | DevOps Intern @ DevOps Insiders |
| 📍 **Based in** | Noida, India |
| 🎯 **Focus** | Azure IaC + Security-gated CI/CD |
| 🛠️ **Main tool** | Terraform |
| 🌱 **Learning** | OPA/Kyverno, Crossplane |

<br>

<a href="https://linkedin.com/in/aniket484"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white"/></a>
<a href="mailto:aniketkmr484@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white"/></a>
<a href="https://github.com/aniket-devop"><img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white"/></a>

</td>
<td width="55%" valign="top">

### 👋 Why I build the way I do

I build small Azure environments in Terraform and spend most of my effort on the security and CI side of them. Getting a change to deploy is the easy part — getting it to deploy safely, with something checking the plan before it runs, is the part worth doing properly.

None of my projects are production infrastructure with real traffic. They're self-built, sized for one person to run and re-run. But I've tried to carry over the patterns a real environment needs: private networking, scoped access, gates before apply.

That judgment — not the tool list — is what I'm actually trying to build.

</td>
</tr>
</table>

<br>

---

## 🧰 Where I'm Solid vs. Still Building

<table width="100%">
<tr><th align="left" width="22%">Area</th><th align="left" width="45%">Tools</th><th align="left" width="33%">Comfort level</th></tr>
<tr><td>Cloud</td><td>Azure, Azure DevOps, Entra ID</td><td>🟢🟢🟢🟢🟢 Daily driver</td></tr>
<tr><td>IaC</td><td>Terraform, Bicep, Ansible</td><td>🟢🟢🟢🟢⚪ Terraform primary</td></tr>
<tr><td>Containers</td><td>Docker, Kubernetes, Helm, ArgoCD</td><td>🟢🟢🟢🟢⚪ Comfortable</td></tr>
<tr><td>CI/CD</td><td>Azure Pipelines, GitHub Actions, Jenkins</td><td>🟢🟢🟢🟢⚪ Azure Pipelines strongest</td></tr>
<tr><td>Security gates</td><td>Trivy, Checkov, SonarQube, Key Vault</td><td>🟢🟢🟢🟢⚪ Core to how I build</td></tr>
<tr><td>Monitoring</td><td>Prometheus, Grafana</td><td>🟢🟢🟢⚪⚪ Provision + basic dashboards</td></tr>
<tr><td>Scripting</td><td>Python, Bash, Git</td><td>🟢🟢🟢🟢⚪ Daily</td></tr>
<tr><td>Secrets mgmt</td><td>HashiCorp Vault</td><td>🟢🟢⚪⚪⚪ Sandbox only — being honest</td></tr>
</table>

<br>

## 💼 Experience

**DevOps Intern — DevOps Insiders** &nbsp;·&nbsp; `Feb 2025 – Present`

- Wrote Terraform modules provisioning Azure resource groups, VNets, and VMs for dev/QA/staging — replaced manual portal setup with version-controlled, repeatable infra
- Built and maintained GitHub Actions + Azure DevOps pipelines for 3+ microservices, with build/test/deploy stages triggered on PRs and merges
- Diagnosed config drift, dependency mismatches, and failed deployments across a 4-person team keeping three environments in sync
- Moved automated test stages ahead of deployment, catching failures before they reached staging

<br>

## 🚀 Projects — grouped by what actually runs together

Three write-ups instead of a longer list of small demos. The AKS cluster, how it gets deployed to, and how it's monitored are one system, not three separate portfolio pieces.

<br>

### 🏗️ 1 — Azure Landing Zone in Terraform
`Terraform` `Hub-and-Spoke` `Azure Firewall` `Bastion` `Key Vault` &nbsp;|&nbsp; 🔗 [Repo](https://github.com/aniket-devop/azure-landing-zone-terraform)

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

<details>
<summary><b>Design decisions — why, not just what</b></summary>
<br>

- Hub-and-spoke instead of one flat network, so the firewall and Bastion live in one place instead of every spoke reinventing them
- NSGs at the spoke boundary (deny-by-default, explicit allow) so the AKS subnet isn't just trusting whatever's on the VNet
- Bastion instead of a jump box with a public IP — a mistake in an earlier version of this project I fixed on purpose here
- RBAC scoped to the resource group, not the subscription
- Firewall rule collections + UDRs forcing spoke egress through the firewall
- Key Vault behind a private endpoint with a Private DNS zone
- Remote state in Azure Storage with locking; `terraform fmt/validate/plan` on every PR with a manual approval gate before apply

Parameterized enough that a second "environment" is a tfvars change, not a duplicated module. That was the actual goal, more than the security stuff, if I'm honest.

</details>

<br>

### ☸️ 2 — Private AKS Platform: cluster + GitOps + observability
`AKS` `ArgoCD` `Helm` `Prometheus/Grafana` &nbsp;|&nbsp; 🔗 *repo link on request*

Started as "can I stand up an AKS cluster without a public API server," and grew to cover deployment and observability because I kept adding to it instead of starting something new each time I learned more.

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

<details>
<summary><b>Cluster → GitOps → observability — how the pieces connect</b></summary>
<br>

**The cluster:** module split (networking → security → identity → AKS → monitoring) came from trial and error — Terraform kept creating resources out of order because of implicit dependencies I hadn't thought through. Splitting fixed that. Core goal: AKS talks to ACR through a managed identity, nothing to rotate, nothing that leaks in a `.tfvars` file. Private endpoints for ACR and Key Vault.

**Deploying to it:** Helm charts hold desired state, ArgoCD reconciles and flags drift with self-healing — instead of finding out something changed when a pod is already crash-looping. Dev/staging/prod from one repo via Helm value overrides + ApplicationSets, rollback via ArgoCD revision history.

**Watching it:** Prometheus + Grafana provisioned by the same Terraform run as the cluster — dashboards exist from the first `apply`, not bolted on later. Alerting is still just defaults; real alert rules are next.

**What I haven't done:** no real load testing, haven't tried to break private endpoint routing or ArgoCD sync under actual traffic. Only run with a couple of test pods.

</details>

<br>

### 🔒 3 — Azure DevOps CI/CD + DevSecOps Pipeline
`Checkov` `Trivy` `SonarQube` `Terraform` &nbsp;|&nbsp; 🔗 *repo link on request*

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

<details>
<summary><b>Why the gate is before apply, not after</b></summary>
<br>

Checkov and Trivy scan the `terraform plan` output before anything gets created, plus a SonarQube quality gate — if any fail, the pipeline stops. An early version just warned and continued, which defeats the point.

There's a manual approval step between plan and apply, kept deliberately rather than automated away. During the internship, a Terraform apply once did something I hadn't expected — since then I want a moment to actually read the plan before anything changes.

This pipeline (commit → build → scan → quality gate → deploy → monitor) is what deploys the landing zone and AKS platform above. Not a standalone demo — the gate for both.

</details>

<br>

---

## 📊 Activity

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=aniket-devop&show_icons=true&theme=transparent&hide_border=true&title_color=0078D4&icon_color=7B42BC&text_color=333333" height="165"/>
<img src="https://github-readme-streak-stats.herokuapp.com/?user=aniket-devop&theme=transparent&hide_border=true&ring=0078D4&fire=7B42BC&currStreakLabel=0078D4" height="165"/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=aniket-devop&theme=minimal&hide_border=true&color=0078D4&line=7B42BC&point=333333" width="100%"/>

</div>

<br>

## 🔭 Right Now

- Azure Policy at the landing-zone level — governance I skipped the first time around
- OPA / Kyverno for admission control on the AKS project
- Actually testing Terraform modules instead of just running `plan` and eyeballing it
- Looking at Crossplane vs. the provider modules I use now — no strong opinion yet

<br>

<div align="center">

**Open to DevOps / DevSecOps roles where I can keep building this judgment on real infrastructure.**

<a href="https://linkedin.com/in/aniket484"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white"/></a>
<a href="mailto:aniketkmr484@gmail.com"><img src="https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white"/></a>

</div>

