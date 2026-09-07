<div align="center">

# Hi, I'm Aniket Kumar 👋

### DevOps Engineer — Azure · Terraform · Kubernetes · CI/CD · GitOps

---

![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHubActions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![AzureDevOps](https://img.shields.io/badge/Azure_DevOps-0078D7?style=for-the-badge&logo=azuredevops&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/aniket-devop)

</div>

<br/>

## 📌 About Me

DevOps Engineer with 2 years of hands-on experience focused on Azure infrastructure, Terraform, CI/CD automation, containerized deployments, Kubernetes, and DevSecOps practices.

I work with Infrastructure as Code using Terraform, deploy containerized workloads on Azure Kubernetes Service (AKS), build CI/CD pipelines using GitHub Actions and Azure DevOps, and implement monitoring and security checks across the delivery lifecycle.

- 🔧 DevOps Engineer @ **DevOps Insiders**
- ☁️ Azure infrastructure provisioning and automation using Terraform
- ☸️ Containerized application deployments using Docker, Kubernetes, AKS, and Helm
- 🚀 CI/CD automation using GitHub Actions and Azure DevOps
- 🔐 DevSecOps and IaC security using Trivy, TFLint, TFSec, and Checkov
- 📊 Monitoring and observability using Prometheus and Grafana
- 🔄 GitOps deployments using ArgoCD
- 🌱 Hands-on AWS infrastructure project using Terraform
- 🎓 BCA, Chandigarh Group of Colleges, Mohali
- 📍 Noida, India

<br/>

## 💼 Professional Experience

**DevOps Engineer — DevOps Insiders**

- Provision and manage Azure infrastructure using Terraform, working with resource groups, virtual networks, and Azure Kubernetes Service (AKS)
- Build and maintain CI/CD pipelines using GitHub Actions and Azure DevOps Pipelines to automate build, test, and deployment workflows
- Containerize applications with Docker and deploy workloads to Kubernetes/AKS using Helm charts
- Apply DevSecOps practices — integrating security and IaC scanning tooling into the delivery lifecycle
- Set up monitoring and observability using Prometheus and Grafana
- Troubleshoot pipeline, infrastructure, and deployment issues across environments
- Collaborate with developers and QA to support smooth, reliable release cycles

<br/>

## 🏗️ Featured Projects

| Project | What it does | Stack |
|---|---|---|
| [Airflow Observability Pipeline](#1-airflow--observability-pipeline-docker-compose--prometheus--grafana) | Containerized Airflow re-architected to single-node LocalExecutor, instrumented with a StatsD → Prometheus → Grafana metrics pipeline | Docker Compose, Airflow, PostgreSQL, Prometheus, Grafana |
| [GitOps CI/CD Deployment Pipeline](#2-gitops-cicd-deployment-pipeline-fastapi--argocd--kind) | Two-repo GitOps setup — CI builds/scans/publishes an image, ArgoCD reconciles the cluster; rollback done entirely through Git | FastAPI, Docker, Trivy, GHCR, Helm, ArgoCD, Kind |
| [Azure Terraform Network Foundation](#3-azure-terraform-network-foundation) | Hub-and-spoke Azure network foundation — Firewall, Bastion, deny-by-default NSGs, RBAC-scoped Key Vault | Terraform, Azure Firewall, Bastion, Key Vault, GitHub Actions |
| [AWS Landing Network (Hands-on Project)](#4-aws-landing-network-hands-on-project) | Multi-AZ AWS network with ALB, private EC2 compute, and locked remote Terraform state | Terraform, VPC, ALB, IAM, S3, DynamoDB |

---

<br/>

## 1. Airflow + Observability Pipeline (Docker Compose + Prometheus + Grafana)

🔗 **Repo:** [airflow-docker-grafana-monitoring](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)
`Docker Compose` `Apache Airflow` `PostgreSQL` `Prometheus` `Grafana` `StatsD`

A containerized Apache Airflow deployment, delivered as a freelance client project and re-architected from Airflow's official CeleryExecutor/Redis reference template into a single-node **LocalExecutor + PostgreSQL** setup. Instrumented end-to-end with a StatsD → Prometheus → Grafana metrics pipeline, fully orchestrated with a single `docker compose up`.

### Architecture

![Airflow Observability Architecture](https://raw.githubusercontent.com/aniket-devop/airflow-docker-grafana-monitoring/main/assets/architecture-diagram.png)

**Components:** Airflow API Server, Scheduler (executes tasks directly via LocalExecutor — no separate worker), DAG Processor, Triggerer, PostgreSQL 16 (metadata store), StatsD Exporter, Prometheus, Grafana — all running as isolated services on one Docker Compose network.

**Monitoring flow:** Airflow services emit StatsD metrics → StatsD Exporter republishes them in Prometheus format → Prometheus scrapes every 15s → Grafana added as a visualization data source.

### ⚙️ Key Engineering Decisions
- Swapped the official CeleryExecutor + Redis worker model for **LocalExecutor**, removing a message broker and separate worker fleet with no benefit at single-node scale — while keeping health checks, dependency ordering, and persistent metadata storage
- Bridged metrics via **StatsD → Prometheus** since Airflow doesn't expose a native `/metrics` endpoint in this configuration

### 🔒 Honest Scope
This is a working local/single-node deployment with a verified metrics pipeline — not a distributed production platform. No Grafana dashboards or alerting are pre-provisioned, and Prometheus/Grafana have no persistent storage; these are documented as deliberate scope boundaries, not oversights.

### 🖥️ Commands
```bash
docker compose up -d
docker compose ps
curl http://localhost:8080  # Airflow UI
```

### 🚀 Future Improvements
- Ship a starter Grafana dashboard + automatic Prometheus datasource provisioning
- Add Alertmanager with basic failure-rate alerts
- Pin third-party image versions currently tracking `:latest`

<br/>

---

<br/>

## 2. GitOps CI/CD Deployment Pipeline (FastAPI → ArgoCD → Kind)

🔗 **App repo:** [gitops-ci-pipeline](https://github.com/aniket-devop/gitops-ci-pipeline) · **GitOps repo:** [gitops-kubernetes-config](https://github.com/aniket-devop/gitops-kubernetes-config)
`FastAPI` `Docker` `GitHub Actions` `Trivy` `GHCR` `Helm` `ArgoCD` `Kind`

A two-repository GitOps demonstration: one repo owns the FastAPI application and its CI pipeline; the other owns the desired Kubernetes state that ArgoCD reconciles against. CI never touches the cluster — the boundary is enforced by design, not just documented.

### Architecture

![GitOps Pipeline Architecture](https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png)

**Flow:**
```
Developer → gitops-ci-pipeline → GitHub Actions → pytest → Docker build
   → Trivy CRITICAL scan → GHCR → Git commit to gitops-kubernetes-config
   → ArgoCD → Kind Kubernetes
```

### 🔁 CI/CD
On every push to `main`: checkout → `pytest` → tag image with short commit SHA → Docker build → Trivy scan (`severity: CRITICAL`, hard-fails the job on a finding) → push to GHCR → commit the new tag to `gitops-kubernetes-config`. ArgoCD (running with `automated`, `prune: true`, `selfHeal: true`) picks up that commit on its own watch cycle and reconciles the Kind cluster — GitHub Actions never runs `kubectl` or holds cluster credentials.

### 🔒 Security
- Trivy CRITICAL gate hard-fails before an image reaches GHCR
- Non-root container (`appuser`) on a minimal `python:3.12-alpine` base
- Two separately scoped credentials — `GITHUB_TOKEN` for GHCR, a distinct `GITOPS_REPO_TOKEN` for the cross-repo commit — so neither can touch the cluster directly

### 🔄 Rollback — a pure Git operation
A `git revert` on the image-tag commit in `gitops-kubernetes-config` was enough for ArgoCD's `selfHeal` to reconcile the cluster back to the previous version — no `kubectl rollout undo`, no ArgoCD CLI. Verified with matching commit SHAs in both repos.

### 🖥️ Commands
```bash
kubectl scale deployment gitops-demo --replicas=5 -n gitops-demo-dev
kubectl get pods -n gitops-demo-dev -w
argocd app get gitops-demo-dev
```

### 📚 Honest Scope
Runs on a local Kind cluster, not a managed cloud environment — no production traffic, uptime, or scale claims. Only the `dev` environment is fully automated; `staging` exists but requires manual sync with no promotion path yet.

### 🚀 Future Improvements
- `dev` → `staging` promotion workflow
- Move to a managed cloud Kubernetes service (e.g. AKS) and registry (e.g. ACR)
- Ingress + TLS, Horizontal Pod Autoscaler, NetworkPolicy/RBAC

<br/>

---

<br/>

## 3. Azure Terraform Network Foundation

🔗 **Repo:** [azure-network-foundation-terraform](https://github.com/aniket-devop/azure-network-foundation-terraform)
`Terraform` `Azure Firewall` `Azure Bastion` `Key Vault` `Azure RBAC` `GitHub Actions`

A Terraform-built Azure networking and security foundation: a hub VNet (Firewall + Bastion), a spoke VNet with a deny-by-default NSG and an AKS-designated subnet, egress forced through the Firewall via a route table, an RBAC-authorized Key Vault, and role assignments scoped to the resource group rather than the subscription. Deployable across two environments (`dev`, `prod`) from one DRY Terraform configuration.

### Architecture

![Azure Network Foundation Architecture](https://raw.githubusercontent.com/aniket-devop/azure-network-foundation-terraform/main/diagrams/architecture.png)

### ⚙️ Key Engineering Decisions
- RBAC scoped to the **resource group**, not the subscription — limits blast radius of a compromised credential
- Explicit `DenyAllInbound` NSG rule rather than relying on Azure's implicit platform defaults
- **Azure Bastion** instead of a jump box — no VM in the design carries a public IP
- Route table forcing all egress from the AKS subnet through the Firewall's private IP, so the firewall's allow-rules are actually enforced, not just configured
- Key Vault secured via **RBAC + network ACL** (not a Private Endpoint) — a deliberate, documented trade-off for this project's scope

### 🔁 CI/CD
`.github/workflows/terraform-ci.yml` runs `terraform fmt -check`, `terraform init -backend=false`, and `terraform validate` on every PR and push to `main`. There is no `plan`/`apply` automation and no security-scanning step in this pipeline yet — noted here rather than overstated.

### 🖥️ Commands
```bash
cd environments/dev
terraform init
terraform validate
```

### 📚 Honest Scope
This is a personal, sandbox-scale project — not a Cloud Adoption Framework "landing zone" (no management-group hierarchy, no Azure Policy, no multi-subscription governance) and no compute is deployed yet. `dev` and `prod` are two `.tfvars`-differentiated instances of the same module set; there's no separate QA/staging environment.

### 🚀 Future Improvements
- Post `terraform plan` output as a PR comment before adding `apply` automation
- Add `terraform test` coverage against real module resource names
- Deploy an actual AKS cluster into the prepared `snet-aks` subnet

<br/>

---

<br/>

## 4. AWS Landing Network (Hands-on Project)

🔗 **Repo:** [aws-terraform-landing-zone-project](https://github.com/aniket-devop/aws-terraform-landing-zone-project)
`Terraform` `VPC` `EC2` `ALB` `IAM` `S3` `DynamoDB`

A self-driven, hands-on project applying the same private-compute networking pattern used in the Azure project — this time in AWS. Multi-AZ VPC, ALB-fronted EC2 in private subnets, and locked remote Terraform state. AWS is a secondary, personal-project skill area alongside Azure as the primary professional cloud.

### Architecture

![AWS Landing Zone Architecture](https://raw.githubusercontent.com/aniket-devop/aws-terraform-landing-zone-project/main/diagrams/architecture.png)

**How it works:** one VPC (`10.0.0.0/16`) across two AZs, each with a public subnet (ALB + NAT Gateway) and a private subnet (EC2 + Security Group + IAM role). The Internet Gateway only reaches the public subnets; EC2 security groups accept traffic only from the ALB; outbound-only internet access goes through the NAT Gateway; Terraform state is remote in S3 with DynamoDB locking.

### 🔁 CI/CD
Every PR runs `terraform fmt -check` → `terraform validate` → `terraform plan` via GitHub Actions before anything is applied.

### 🖥️ Commands
```bash
terraform init
terraform plan
terraform apply
```

### 🚀 Future Improvements
- HTTPS listener on the ALB with an ACM certificate
- Auto Scaling Group instead of a static EC2 instance
- CloudWatch alarms and a basic monitoring dashboard

<br/>

---

<br/>

## 🧰 Tech Stack

<div align="center">

![Azure](https://skillicons.dev/icons?i=azure) ![AWS](https://skillicons.dev/icons?i=aws) ![Terraform](https://skillicons.dev/icons?i=terraform) ![Docker](https://skillicons.dev/icons?i=docker) ![Kubernetes](https://skillicons.dev/icons?i=kubernetes) ![GithubActions](https://skillicons.dev/icons?i=githubactions) ![Grafana](https://skillicons.dev/icons?i=grafana) ![Prometheus](https://skillicons.dev/icons?i=prometheus) ![Python](https://skillicons.dev/icons?i=python) ![Bash](https://skillicons.dev/icons?i=bash) ![Linux](https://skillicons.dev/icons?i=linux) ![Git](https://skillicons.dev/icons?i=git)

</div>

| Category | Tools |
|---|---|
| **Cloud** | Microsoft Azure (primary) · AWS — Hands-on Project |
| **IaC** | Terraform |
| **CI/CD** | GitHub Actions, Azure DevOps Pipelines |
| **Containers & Orchestration** | Docker, Kubernetes, AKS, Helm |
| **GitOps** | ArgoCD |
| **Security** | Trivy, TFLint, TFSec, Checkov |
| **Monitoring** | Prometheus, Grafana |
| **Scripting & OS** | Python, Bash, Linux |
| **Version Control** | Git, GitHub |

<br/>

---

## 🎓 Education
**Bachelor of Computer Applications (BCA) — Chandigarh Group of Colleges, Mohali**

<br/>

## 📊 GitHub Stats

<div align="center">

<img src="https://streak-stats.demolab.com/?user=aniket-devop&hide_border=true&theme=dark&background=0D1117&ring=378ADD&fire=22C55E&currStreakLabel=378ADD" alt="GitHub Streak Stats"/>

</div>

<details>
<summary><b>📈 GitHub profile stats — click to expand</b></summary>
<br/>

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=aniket-devop&show_icons=true&theme=default&hide_border=true&count_private=true" alt="GitHub Stats" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aniket-devop&layout=compact&hide_border=true&theme=default" alt="Top Languages" height="165"/>

</div>

</details>

<br/>

## 📬 Contact

*Always happy to connect with fellow DevOps engineers and recruiters — feel free to reach out!*

<div align="center">

<a href="https://linkedin.com/in/aniket484"><img src="icons/linkedin-flat.png" width="45" height="45"/></a>
&nbsp;&nbsp;
<a href="https://github.com/aniket-devop"><img src="icons/github-flat.png" width="45" height="45"/></a>
&nbsp;&nbsp;
<a href="mailto:aniketkmr484@gmail.com"><img src="icons/email-flat-blue.png" width="45" height="45"/></a>

<br/><br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/aniket-devop)

</div>
