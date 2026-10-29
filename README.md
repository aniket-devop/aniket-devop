<!-- Profile README for github.com/aniket-devop/aniket-devop -->

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&height=230&color=0:0D1117,50:0078D4,100:844FBA&text=Aniket%20Kumar&fontColor=ffffff&fontSize=56&fontAlignY=38&desc=DevOps%20%26%20DevSecOps%20Engineer&descSize=20&descAlignY=60&animation=fadeIn" alt="Aniket Kumar, DevOps and DevSecOps Engineer" width="100%"/>

<a href="https://github.com/aniket-devop">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&pause=1200&color=58A6FF&center=true&vCenter=true&width=700&lines=DevOps+%26+DevSecOps+Engineer;I+make+infrastructure+boring+in+the+right+way.;Terraform+%C2%B7+AKS+%C2%B7+GitOps+%C2%B7+Observability" alt="DevOps and DevSecOps Engineer. I make infrastructure boring in the right way."/>
</a>

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-aniket484-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![GitHub](https://img.shields.io/badge/GitHub-aniket--devop-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)
![Open to roles](https://img.shields.io/badge/Open_to-DevOps_/_Cloud_roles-2ea043?style=for-the-badge)
![Location](https://img.shields.io/badge/Bengaluru-India-orange?style=for-the-badge&logo=googlemaps&logoColor=white)

<br/>

| ☁️ **2 clouds** | 🏗️ **6 real projects** | 🔁 **Git-only rollback** | 📡 **27 assets streaming live** |
|:---:|:---:|:---:|:---:|
| Azure (primary) + AWS | Terraform · K8s · GitOps | Verified with Argo CD | Running on AKS |

</div>

<br/>

## 👋 About

DevOps Engineer with **2 years** of hands-on experience in Azure infrastructure, Terraform, CI/CD, Kubernetes, and DevSecOps. At **DevOps Insiders** I work on Azure provisioning and pipeline automation.

On my own time I build things that actually run: a live AKS platform, a GitOps pipeline with Git-only rollback, a hub-and-spoke Azure network. I'd rather find where a design breaks on my own dime than on a client's.

> [!NOTE]
> Every project below states its limits openly. Gaps are in each repo's roadmap, not hidden.

📍 Bengaluru, India &nbsp;·&nbsp; 🎓 BCA, Chandigarh Group of Colleges &nbsp;·&nbsp; 💼 DevOps Insiders

<br/>

## 🔄 How I Ship

```mermaid
flowchart LR
    A["📝 Commit<br/>git · PR"] --> B["🔍 Validate + Scan<br/>terraform · pytest · Trivy"]
    B --> C["📦 Build<br/>Docker · GitHub Actions"]
    C --> D["🚀 Reconcile<br/>Argo CD · AKS · Helm"]
    D --> E["📊 Observe<br/>Prometheus · Grafana"]
    R["⏪ git revert"] -.rollback.-> D

    classDef src fill:#f1eafa,stroke:#844FBA,color:#3d1f66;
    classDef check fill:#e6f6ec,stroke:#2f855a,color:#14452f;
    classDef run fill:#e8f1fb,stroke:#0078D4,color:#003a70;
    classDef obs fill:#fff4d6,stroke:#d19a00,color:#5c4300;
    classDef back fill:#fde8e8,stroke:#c53030,color:#5a1313;
    class A src;
    class B,C check;
    class D run;
    class E obs;
    class R back;
```

**Git is the source of truth.** Changes ship by merging, and rollbacks happen by reverting a commit.

<br/>

## 🧰 Tech Stack

**☁️ Cloud &amp; IaC**<br/>
<img src="https://skillicons.dev/icons?i=azure,aws,terraform&theme=dark" alt="Azure, AWS, Terraform"/> &nbsp;<sub>Azure is primary, AWS is project-level</sub>

**📦 Containers &amp; Orchestration**<br/>
<img src="https://skillicons.dev/icons?i=docker,kubernetes&theme=dark" alt="Docker, Kubernetes"/>
<img src="https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white" alt="Helm"/>
<img src="https://img.shields.io/badge/AKS-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="AKS"/>

**🔁 CI/CD &amp; GitOps**<br/>
<img src="https://skillicons.dev/icons?i=githubactions&theme=dark" alt="GitHub Actions"/>
<img src="https://img.shields.io/badge/Azure_DevOps-0078D7?style=for-the-badge&logo=azuredevops&logoColor=white" alt="Azure DevOps"/>
<img src="https://img.shields.io/badge/Argo_CD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white" alt="Argo CD"/>

**🔐 DevSecOps**<br/>
<img src="https://img.shields.io/badge/Trivy-1904DA?style=for-the-badge" alt="Trivy"/>
<img src="https://img.shields.io/badge/TFLint-5C4EE5?style=for-the-badge" alt="TFLint"/>
<img src="https://img.shields.io/badge/tfsec-0B3D91?style=for-the-badge" alt="tfsec"/>
<img src="https://img.shields.io/badge/Checkov-1F6FEB?style=for-the-badge" alt="Checkov"/>
<img src="https://img.shields.io/badge/SonarQube-4E9BCD?style=for-the-badge&logo=sonarqubeserver&logoColor=white" alt="SonarQube"/>
<img src="https://img.shields.io/badge/Infracost-FF6B35?style=for-the-badge" alt="Infracost"/>

**📊 Observability**<br/>
<img src="https://skillicons.dev/icons?i=prometheus,grafana&theme=dark" alt="Prometheus, Grafana"/>

**🐧 Systems &amp; Code**<br/>
<img src="https://skillicons.dev/icons?i=linux,bash,python,fastapi,postgres,git&theme=dark" alt="Linux, Bash, Python, FastAPI, PostgreSQL, Git"/>

<br/>

## 🏗️ Featured Projects

### 📌 At a glance

| # | Project | Focus | Core stack |
|:-:|---|---|---|
| 1 | **[Axion Intelligence Platform](https://github.com/aniket-devop/axion-cloud-infrastructure)** | End-to-end Terraform → ACR → AKS with live traffic | Terraform · AKS · GitHub Actions |
| 2 | **[Azure Landing Zone & DevSecOps](https://github.com/aniket-devop/azure-landing-zone-devsecops)** | Secure three-tier platform with gated, scanned releases | Terraform · Azure DevOps · tfsec · Infracost |
| 3 | **[GitOps CI/CD Pipeline](https://github.com/aniket-devop/gitops-kubernetes-config)** | CI builds and scans, Argo CD deploys, rollback is `git revert` | GitHub Actions · Trivy · Argo CD |
| 4 | **[Azure Network Foundation](https://github.com/aniket-devop/azure-network-foundation-terraform)** | Hub-and-spoke, deny-by-default | Terraform · Firewall · Key Vault |
| 5 | **[AWS Landing Network](https://github.com/aniket-devop/aws-terraform-landing-zone-project)** | Azure private-compute pattern rebuilt on AWS | Terraform · VPC · ALB |
| 6 | **[Airflow Observability](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)** | Re-architected Airflow with full metrics stack | Docker Compose · Prometheus · Grafana |

<br/>

### ⭐ 1 · Axion Intelligence Platform
**Terraform → ACR → AKS, end to end, serving real traffic.**

<a href="https://github.com/aniket-devop/axion-cloud-infrastructure/blob/main/docs/demo/axion-deployment-demo.mp4">
<img src="https://github.com/aniket-devop/axion-cloud-infrastructure/raw/main/docs/screenshots/02-fleet-summary.png" alt="Axion fleet dashboard running on AKS. Click to watch the demo" width="100%"/>
</a>
<br/><sub>▶ Click the screenshot to watch the deployment walkthrough</sub>

27 simulated industrial assets stream telemetry every 5 seconds into a live dashboard with 3D digital twins and real-time health scoring. Terraform provisions Azure, GitHub Actions builds images into ACR, and Kubernetes manifests roll the workloads onto AKS.

<details>
<summary><b>⚙️ Key engineering decisions</b></summary>
<br/>

- Terraform `for_each` over an `environments` map: one module tree renders dev, staging, and prod
- Remote state bootstrapped from a separate `state-infrastructure/` stack
- Kubernetes base and overlays per environment, reconciled by Argo CD auto-sync
- Ingestion and query split into separate services so each scales on its own
- Path-filtered image builds: a frontend commit doesn't rebuild the backend

**Honest scope:** Terraform workflow is plan-only; DB credentials are inline. Key Vault, PVC, and Ingress/TLS are on the roadmap.
</details>

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![AKS](https://img.shields.io/badge/AKS-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

**[View repository →](https://github.com/aniket-devop/axion-cloud-infrastructure)**

<br/>

---

### 🛡️ 2 · Azure Landing Zone & DevSecOps
**Every release scanned, costed, reviewed and approved before it reaches Prod.**

```mermaid
flowchart LR
    U([Operators]) -->|HTTPS| AG["Application Gateway<br/>TLS + WAF"]
    AG --> FE["2 x Frontend VMs"]
    FE --> ILB["Internal<br/>Load Balancer"]
    ILB --> BE["2 x Backend VMs"]
    BE -->|private endpoint| DB[("PostgreSQL<br/>Flexible Server")]
    BE -.-> KV["Key Vault"]
    ADM([Admins]) -->|Bastion| FE

    classDef edge fill:#fde8e8,stroke:#c53030,color:#5a1313;
    classDef tier fill:#e8f1fb,stroke:#0078D4,color:#003a70;
    classDef data fill:#e6f6ec,stroke:#2f855a,color:#14452f;
    class AG edge;
    class FE,ILB,BE tier;
    class DB,KV data;
```

A three-tier Azure platform for an Industrial IoT monitoring system in petroleum refineries. I designed the Landing Zone with modular Terraform and built the Azure DevOps pipelines that ship infrastructure and application (frontend, backend, database) through Dev, Test and Prod with manual approval gates.

<details>
<summary><b>⚙️ Key engineering decisions</b></summary>
<br/>

- `terraform validate`, tfsec, TFLint and Infracost all run **before** apply, then plan review and manual approval
- Infrastructure and application CI/CD are separate, so neither waits on the other
- Build once, promote the same artifact through Dev → Test → Prod with approval gates
- Private endpoints for PostgreSQL, Azure Bastion for admin access, Key Vault for secrets
- Liquibase for versioned database migrations, with SonarQube quality checks on application code

**Honest scope:** the application code was written by the wider dev team; this repo covers the platform and delivery pipelines.
</details>

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Azure DevOps](https://img.shields.io/badge/Azure_DevOps-0078D7?style=flat-square&logo=azuredevops&logoColor=white)
![tfsec](https://img.shields.io/badge/tfsec-0B3D91?style=flat-square)
![Infracost](https://img.shields.io/badge/Infracost-FF6B35?style=flat-square)
![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=flat-square&logo=sonarqubeserver&logoColor=white)
![Liquibase](https://img.shields.io/badge/Liquibase-2962FF?style=flat-square&logo=liquibase&logoColor=white)

**[View repository →](https://github.com/aniket-devop/azure-landing-zone-devsecops)**

<br/>

---

### 🔁 3 · GitOps CI/CD Pipeline
**CI builds and scans. Argo CD deploys. CI never touches the cluster.**

<a href="https://github.com/aniket-devop/gitops-kubernetes-config">
<img src="https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png" alt="GitOps pipeline architecture" width="100%"/>
</a>

A two-repo GitOps setup. One repo owns the FastAPI app and its pipeline; the other owns the desired cluster state that Argo CD reconciles.

<details>
<summary><b>⚙️ Key engineering decisions</b></summary>
<br/>

- Trivy `CRITICAL` gate hard-fails the build before an image reaches GHCR
- Two separately scoped tokens, so GitHub Actions never holds cluster credentials
- Argo CD with `automated`, `prune`, and `selfHeal`
- **Rollback is a `git revert`**: no `kubectl rollout undo`, no Argo CD CLI
- Non-root container on `python:3.12-alpine`

**Honest scope:** runs on a local Kind cluster; only `dev` is fully automated.
</details>

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=flat-square)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)

**[App repo →](https://github.com/aniket-devop/gitops-ci-pipeline)** &nbsp;·&nbsp; **[GitOps repo →](https://github.com/aniket-devop/gitops-kubernetes-config)**

<br/>

---

### 🌐 4 · Azure Terraform Network Foundation
**Hub-and-spoke, deny-by-default, no public IPs on compute.**

<a href="https://github.com/aniket-devop/azure-network-foundation-terraform">
<img src="https://raw.githubusercontent.com/aniket-devop/azure-network-foundation-terraform/main/diagrams/architecture.png" alt="Azure network foundation architecture" width="100%"/>
</a>

A hub VNet (Firewall and Bastion), a spoke VNet with a deny-by-default NSG and an AKS-ready subnet, and an RBAC-authorized Key Vault. Deployable to `dev` and `prod` from one Terraform configuration.

<details>
<summary><b>⚙️ Key engineering decisions</b></summary>
<br/>

- Route table forces AKS egress through the Firewall, so its rules are actually enforced
- RBAC scoped to the resource group, not the subscription, to limit blast radius
- Explicit `DenyAllInbound` instead of relying on platform defaults
- Azure Bastion instead of a jump box
- Key Vault via RBAC and network ACL: a documented trade-off against Private Endpoint

**Honest scope:** sandbox-scale, not a full landing zone. CI runs `fmt`, `init`, and `validate` only.
</details>

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Azure Firewall](https://img.shields.io/badge/Azure_Firewall-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Key Vault](https://img.shields.io/badge/Key_Vault-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

**[View repository →](https://github.com/aniket-devop/azure-network-foundation-terraform)**

<br/>

---

### 🧪 5 · More Builds

<table>
<tr>
<td width="50%" valign="top">

**☁️ AWS Landing Network**<br/>
<sub>Terraform · VPC · ALB · EC2 · S3 · DynamoDB</sub>

<a href="https://github.com/aniket-devop/aws-terraform-landing-zone-project">
<img src="https://raw.githubusercontent.com/aniket-devop/aws-terraform-landing-zone-project/main/diagrams/architecture.png" alt="AWS landing zone architecture" width="100%"/>
</a>

The Azure private-compute pattern, rebuilt on AWS. Multi-AZ VPC, ALB-fronted EC2 in private subnets, outbound via NAT, and remote state in S3 with DynamoDB locking. Every PR runs `fmt`, `validate`, and `plan`.

**[View repository →](https://github.com/aniket-devop/aws-terraform-landing-zone-project)**

</td>
<td width="50%" valign="top">

**📊 Airflow Observability Pipeline**<br/>
<sub>Docker Compose · Airflow · StatsD · Prometheus · Grafana</sub>

<a href="https://github.com/aniket-devop/airflow-docker-grafana-monitoring">
<img src="https://raw.githubusercontent.com/aniket-devop/airflow-docker-grafana-monitoring/main/assets/architecture-diagram.png" alt="Airflow observability architecture" width="100%"/>
</a>

Client project. I re-architected Airflow's Celery/Redis setup into a single-node `LocalExecutor` deployment, dropping a broker and worker fleet that added nothing at that scale, then wired StatsD → Prometheus → Grafana. One `docker compose up`.

**[View repository →](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)**

</td>
</tr>
</table>

<br/>

## 🧠 How I Think

<table>
<tr>
<td width="50%" valign="top">

```yaml
# 🧠 principles
principles:
  - If it's not in Git, it doesn't exist
  - Shift security left, scan before you ship
  - A rollback you haven't tested is a hope
  - You can't fix what you can't observe
currently:
  building: AKS platform + GitOps
  learning: Platform engineering, SRE
```

</td>
<td width="50%" valign="top">

```text
# 🎯 what you get when you hire me
✔ Infra that is reproducible, not clicked
✔ Pipelines that scan before they ship
✔ Rollbacks that are one git revert away
✔ Dashboards before incidents, not after
✔ Honest docs: limits stated upfront
✔ Immediate joiner
```

</td>
</tr>
</table>

<br/>

## 📈 GitHub Activity

<div align="center">

<img src="https://streak-stats.demolab.com/?user=aniket-devop&theme=dark&background=0D1117&ring=58A6FF&fire=39D0D8&currStreakLabel=58A6FF&sideLabels=8B949E&dates=6E7681&currStreakNum=F0F6FC&sideNums=F0F6FC&stroke=30363D&hide_border=false&border_radius=12" alt="GitHub streak stats"/>

<br/><br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=aniket-devop&bg_color=0D1117&color=58A6FF&line=58A6FF&point=FFFFFF&area=true&area_color=58A6FF&hide_border=true&radius=12" alt="Contribution activity graph" width="95%"/>

<br/><br/>

<img src="https://komarev.com/ghpvc/?username=aniket-devop&label=Profile+Views&color=0e75b6&style=for-the-badge" alt="Profile views"/>

<br/><br/>

### ⚙️ _"If it's not in Git, it doesn't exist."_ 🚀

<sub>🔁 **Automate** &nbsp;·&nbsp; 🛡️ **Secure** &nbsp;·&nbsp; 📊 **Observe** &nbsp;·&nbsp; ☁️ **Repeat**</sub>

</div>

<br/>

## 📬 Let's Talk

I'm open to **DevOps / Cloud Engineer** roles, full-time, in Bengaluru or remote. If something here matches what you're hiring for, or you want to compare notes on Terraform module design, AKS networking, or GitOps patterns, message me.

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Message_me-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)

<!-- Optional: add your email as a clickable badge
[![Email](https://img.shields.io/badge/Email-Write_to_me-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:YOUR_EMAIL_HERE)
-->

<br/>

<img src="https://capsule-render.vercel.app/api?type=waving&height=100&color=0:844FBA,50:0078D4,100:0D1117&section=footer" alt="footer" width="100%"/>

</div>
