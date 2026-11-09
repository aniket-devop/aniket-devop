<div align="center">

# Aniket Kumar

<a href="https://github.com/aniket-devop">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&pause=1200&color=58A6FF&center=true&vCenter=true&width=700&lines=DevOps+Engineer+%7C+Cloud+Infrastructure+%7C+Automation;I+make+infrastructure+boring+in+the+right+way.;Terraform+%C2%B7+AKS+%C2%B7+GitOps+%C2%B7+Observability" alt="DevOps Engineer | Cloud Infrastructure | Automation. I make infrastructure boring in the right way."/>
</a>

<br/>

<a href="https://linkedin.com/in/aniket484"><img src="https://skillicons.dev/icons?i=linkedin" width="32" height="32" alt="LinkedIn"/></a>
&nbsp;&nbsp;&nbsp;
<a href="https://github.com/aniket-devop"><img src="https://cdn.simpleicons.org/github/181717" width="32" height="32" alt="GitHub"/></a>
&nbsp;&nbsp;&nbsp;
<a href="https://medium.com/@aniketkmr484"><img src="https://cdn.simpleicons.org/medium/000000" width="32" height="32" alt="Medium"/></a>
<a href="https://medium.com/@aniketkmr484"><b>Medium</b></a>

![Open to roles](https://img.shields.io/badge/Open_to-DevOps_/_Cloud_roles-2ea043?style=for-the-badge)

<br/>

| ☁️ **2 clouds** | 🏗️ **6 real projects** | 🔁 **Git-only rollback** | 📡 **27 assets streaming live** |
|:---:|:---:|:---:|:---:|
| Azure (primary) + AWS | Terraform · K8s · GitOps | Verified with ArgoCD | Running on AKS |

</div>

<br/>

## 👋 About

DevOps Engineer with 2 years of hands-on experience in Azure infrastructure, Terraform, CI/CD, Kubernetes, and DevSecOps. At **DevOps Insiders** I work on Azure provisioning and pipeline automation.

On my own time I build things that actually run: a live AKS platform, a GitOps pipeline with Git-only rollback, a hub-and-spoke Azure network. I'd rather find where a design breaks on my own dime than on a client's.

> [!NOTE]
> Every project below states its limits openly. Gaps are in each repo's roadmap, not hidden.

📍 Bengaluru, India &nbsp;·&nbsp; 🎓 BCA, Chandigarh Group of Colleges

<br/>

## 💼 Experience

**DevOps Engineer** · DevOps Insiders &nbsp;|&nbsp; Nov 2024 – Present<br/>
<sub>Industrial IoT monitoring application for a UK-based refinery client</sub>

- Built and maintained 6+ CI/CD pipelines on Azure DevOps and GitHub Actions across Dev, QA and Staging
- Provisioned Azure infrastructure with reusable Terraform modules and remote state; added 4 automated checks (fmt/validate, TFLint, tfsec, Checkov) to CI/CD
- Deployed containerized services on AKS with Docker and Helm; built Prometheus and Grafana dashboards for application, pod and infrastructure health

**DevOps Engineer** · Freelance &nbsp;|&nbsp; Jul 2026 – Aug 2026<br/>
<sub>Airflow Observability Pipeline</sub>

- Delivered a single-node Apache Airflow setup on Docker Compose (8 services), migrating from CeleryExecutor + Redis to LocalExecutor + PostgreSQL
- Built Airflow-to-Grafana monitoring with StatsD, Prometheus and Grafana, and verified ~129 airflow_* metrics

<br/>
## 🔄 How I Ship

```mermaid
flowchart LR
    A["📝 Commit<br/>git · PR"] --> B["🔍 Validate + Scan<br/>terraform · pytest · Trivy"]
    B --> C["📦 Build<br/>Docker · GitHub Actions"]
    C --> D["🚀 Reconcile<br/>Argo CD · AKS · Helm"]
    D --> E["📊 Observe<br/>Prometheus · Grafana"]
```

<br/>

## Tech Stack

<table>
<tr>
<td width="170"><b>Cloud &amp; IaC</b></td>
<td align="center" width="100"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/azure/azure-original.svg" width="40" height="40" alt="Azure"/><br/><sub>Azure</sub></td>
<td align="center" width="100"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original.svg" width="40" height="40" alt="AWS"/><br/><sub>AWS</sub></td>
<td align="center" width="100"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/terraform/terraform-original.svg" width="40" height="40" alt="Terraform"/><br/><sub>Terraform</sub></td>
<td></td><td></td><td></td>
</tr>
<tr>
<td><b>Containers</b></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" width="40" height="40" alt="Docker"/><br/><sub>Docker</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kubernetes/kubernetes-original.svg" width="40" height="40" alt="Kubernetes"/><br/><sub>Kubernetes</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/helm/helm-original.svg" width="40" height="40" alt="Helm"/><br/><sub>Helm</sub></td>
<td></td><td></td><td></td>
</tr>
<tr>
<td><b>CI/CD &amp; GitOps</b></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/githubactions/githubactions-original.svg" width="40" height="40" alt="GitHub Actions"/><br/><sub>GitHub Actions</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/azuredevops/azuredevops-original.svg" width="40" height="40" alt="Azure DevOps"/><br/><sub>Azure DevOps</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/argocd/argocd-original.svg" width="40" height="40" alt="Argo CD"/><br/><sub>Argo CD</sub></td>
<td></td><td></td><td></td>
</tr>
<tr>
<td><b>Observability</b></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/prometheus/prometheus-original.svg" width="40" height="40" alt="Prometheus"/><br/><sub>Prometheus</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/grafana/grafana-original.svg" width="40" height="40" alt="Grafana"/><br/><sub>Grafana</sub></td>
<td></td><td></td><td></td><td></td>
</tr>
<tr>
<td><b>Systems &amp; Code</b></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" width="40" height="40" alt="Linux"/><br/><sub>Linux</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bash/bash-original.svg" width="40" height="40" alt="Bash"/><br/><sub>Bash</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="40" height="40" alt="Python"/><br/><sub>Python</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/fastapi/fastapi-original.svg" width="40" height="40" alt="FastAPI"/><br/><sub>FastAPI</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" width="40" height="40" alt="PostgreSQL"/><br/><sub>PostgreSQL</sub></td>
<td align="center"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" width="40" height="40" alt="Git"/><br/><sub>Git</sub></td>
</tr>
<tr>
<td><b>DevSecOps</b></td>
<td colspan="6"><code>Trivy</code> &nbsp; <code>tfsec</code> &nbsp; <code>TFLint</code> &nbsp; <code>Checkov</code> &nbsp; <code>SonarQube</code> &nbsp; <code>Infracost</code></td>
</tr>
</table>

<sub>Azure is my primary cloud (AKS in production work); AWS at project level.</sub>

<br/>
## 🏗️ Featured Projects

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
- ACR `admin_enabled = false`: identity-based auth only
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

- `terraform validate`, tfsec, TFLint and Infracost all run before apply, then plan review and manual approval
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

### 🛡️ 4 · Azure Terraform Network Foundation
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

## 📈 GitHub Activity

<div align="center">

<img src="https://streak-stats.demolab.com/?user=aniket-devop&theme=dark&background=0D1117&ring=58A6FF&fire=39D0D8&currStreakLabel=58A6FF&sideLabels=8B949E&dates=6E7681&currStreakNum=F0F6FC&sideNums=F0F6FC&stroke=30363D&hide_border=false&border_radius=12" alt="GitHub streak stats"/>

</div>

<br/>

<div align="center">

<h3><i>"If it's not in Git, it doesn't exist."</i></h3>

<sub>Automate &nbsp;·&nbsp; Secure &nbsp;·&nbsp; Observe &nbsp;·&nbsp; Repeat</sub>

<br/>

## What I Bring

<table>
<tr>
<td align="center" width="33%">
<img src="https://skillicons.dev/icons?i=terraform&theme=dark" width="48" alt="Terraform"/><br/><br/>
<b>Reproducible infrastructure</b><br/>
<sub>Modular Terraform with remote state,<br/>no manual console changes</sub>
</td>
<td align="center" width="33%">
<img src="https://skillicons.dev/icons?i=githubactions&theme=dark" width="48" alt="GitHub Actions"/><br/><br/>
<b>Pipelines with security gates</b><br/>
<sub>Trivy, tfsec and Checkov run<br/>before anything ships</sub>
</td>
<td align="center" width="33%">
<img src="https://skillicons.dev/icons?i=git&theme=dark" width="48" alt="Git"/><br/><br/>
<b>Git-based rollbacks</b><br/>
<sub>Argo CD reconciles from Git,<br/>rollback is a <code>git revert</code></sub>
</td>
</tr>
<tr>
<td align="center">
<img src="https://skillicons.dev/icons?i=kubernetes&theme=dark" width="48" alt="Kubernetes"/><br/><br/>
<b>Kubernetes delivery</b><br/>
<sub>AKS deployments with Docker and Helm</sub>
</td>
<td align="center">
<img src="https://skillicons.dev/icons?i=grafana&theme=dark" width="48" alt="Grafana"/><br/><br/>
<b>Observability</b><br/>
<sub>Prometheus and Grafana dashboards<br/>for apps, pods and infrastructure</sub>
</td>
<td align="center">
<img src="https://skillicons.dev/icons?i=azure&theme=dark" width="48" alt="Azure"/><br/><br/>
<b>Azure-first cloud</b><br/>
<sub>Landing zones, hub-and-spoke networking,<br/>AWS at project level</sub>
</td>
</tr>
</table>

<br/>

## Let's Talk

![Status](https://img.shields.io/badge/Status-Open_to_work-2ea043?style=flat-square)
![Role](https://img.shields.io/badge/Role-DevOps_/_Cloud_Engineer-0078D4?style=flat-square)
![Location](https://img.shields.io/badge/Location-Bengaluru_/_Remote-555555?style=flat-square)
![Notice](https://img.shields.io/badge/Notice_period-Immediate-555555?style=flat-square)

<br/>

Happy to compare notes on Terraform module design, AKS networking, or GitOps patterns.

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484) [![Email](https://img.shields.io/badge/Email-aniketkmr484@gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com) [![Resume](https://img.shields.io/badge/Resume-PDF-2ea043?style=flat&logo=adobeacrobatreader&logoColor=white)](https://github.com/aniket-devop/aniket-devop/blob/main/Aniket_Kumar_Resume.pdf)

<br/>

<img src="https://komarev.com/ghpvc/?username=aniket-devop&label=Profile+Views&color=0e75b6&style=flat-square" alt="Profile views"/>

</div>
