<div align="center">

<br>

# Aniket Kumar

**DevOps Engineer** &nbsp;·&nbsp; Azure &nbsp;·&nbsp; Terraform &nbsp;·&nbsp; Kubernetes &nbsp;·&nbsp; GitOps

*I make infrastructure boring in the right way.*

No manual clicks. No "it works on my machine." Everything reproducible, everything in code.

<br>

<img src="https://skillicons.dev/icons?i=azure,aws,terraform,kubernetes,docker,githubactions&perline=6" alt="Core stack" />

<br><br>

[![Projects](https://img.shields.io/badge/View_Projects-0D1117?style=for-the-badge&logo=github&logoColor=white)](#featured-projects)
&nbsp;
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)

<br>

| 2 years | 5 projects | Azure + AWS |
|:-:|:-:|:-:|
| hands-on DevOps | built to actually run | IaC, CI/CD, GitOps |

<br>

**Open to DevOps / Cloud Engineer roles** &nbsp;·&nbsp; Bengaluru or remote &nbsp;·&nbsp; Full-time

</div>

---

## About

DevOps Engineer with 2 years of hands-on experience across Azure infrastructure, Terraform, CI/CD automation, containerized deployments, Kubernetes, and DevSecOps.

My day job is Azure and pipelines. My own time goes into projects I build to actually run, not just to demo, because I'd rather find out where a design breaks on my own dime than on a client's.

| | |
|---|---|
| **Now** | DevOps Engineer @ DevOps Insiders |
| **Strongest at** | Azure infrastructure, Terraform, CI/CD pipelines |
| **Also building with** | AWS, ArgoCD, Prometheus, Grafana |
| **Education** | BCA, Chandigarh Group of Colleges, Mohali |
| **Based in** | Bengaluru, Karnataka, India |

---

## Featured Projects

<div align="center">

| | Project | Highlights |
|:-:|---|---|
| ⭐ | [**Axion Intelligence Platform**](#axion-intelligence-platform) | Terraform + AKS, deployed end to end |
| 🔁 | [**GitOps CI/CD Pipeline**](#gitops-cicd-pipeline) | GitHub Actions → Trivy → ArgoCD |
| 🛡️ | [**Azure Network Foundation**](#azure-network-foundation) | Hub-and-spoke, deny-by-default |
| ☁️ | [**AWS Landing Network**](#aws-landing-network) | Multi-AZ VPC, ALB, locked remote state |
| 📈 | [**Airflow Observability Pipeline**](#airflow-observability-pipeline) | StatsD → Prometheus → Grafana |

</div>

<br>

### Axion Intelligence Platform

<table>
<tr><td>

![Flagship](https://img.shields.io/badge/FLAGSHIP-0A66C2?style=flat-square) ![Azure](https://img.shields.io/badge/AZURE_·_AKS-0078D4?style=flat-square)

**A production-style industrial IoT monitoring platform running on a live AKS cluster.** 27 simulated assets (pumps, motors, compressors) across five refinery sites stream temperature, vibration, and current readings every 5 seconds into a dashboard with 3D digital twins and real-time health scoring.

`Terraform ➜ GitHub Actions ➜ ACR ➜ AKS ➜ LoadBalancer`

<img src="https://skillicons.dev/icons?i=terraform,azure,kubernetes,githubactions,fastapi,react,postgres,docker&perline=8" alt="Axion stack" />

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/axion-cloud-infrastructure/main/docs/architecture.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/axion-cloud-infrastructure/main/docs/architecture.png" alt="Axion Architecture" width="100%">
  </a>
</p>

**Engineering decisions**
- Ingestion and query split into separate services so each scales independently
- One Terraform module tree renders dev/staging/prod through `for_each` over an `environments` map
- Remote state bootstrapped in a separate stack; ACR runs with `admin_enabled = false`

<sub>**Honest scope:** portfolio build with documented gaps (inline DB credentials, `emptyDir` storage, no Ingress/TLS yet), all listed in the repo roadmap.</sub>

**[Repository ➜](https://github.com/aniket-devop/axion-cloud-infrastructure)** &nbsp;·&nbsp; **[Watch the deployment demo ➜](https://github.com/aniket-devop/axion-cloud-infrastructure/raw/main/docs/demo/axion-deployment-demo.mp4)**

</td></tr>
</table>

<br>

### GitOps CI/CD Pipeline

<table>
<tr><td>

![GitOps](https://img.shields.io/badge/GITOPS-EF7B4D?style=flat-square) ![DevSecOps](https://img.shields.io/badge/DEVSECOPS-1F883D?style=flat-square)

**Two repos, one boundary: CI never touches the cluster.** The app repo builds, tests, scans, and publishes an image. The config repo holds the desired state that ArgoCD reconciles.

`pytest ➜ Docker build ➜ Trivy CRITICAL scan ➜ GHCR ➜ Git commit ➜ ArgoCD ➜ Kind`

<img src="https://skillicons.dev/icons?i=fastapi,docker,githubactions,kubernetes&perline=8" alt="GitOps stack" />
<br>
<sub>Also: Trivy · GHCR · Helm · ArgoCD · Kind</sub>

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png" alt="GitOps Pipeline Architecture" width="100%">
  </a>
</p>

**Engineering decisions**
- Trivy CRITICAL gate hard-fails the pipeline before an image reaches GHCR
- Non-root container on a minimal `python:3.12-alpine` base
- Rollback is a pure Git operation: reverting the image-tag commit lets ArgoCD `selfHeal` restore the previous version

<sub>**Honest scope:** runs on a local Kind cluster. Only `dev` is fully automated; `staging` is manual sync.</sub>

**[App repo ➜](https://github.com/aniket-devop/gitops-ci-pipeline)** &nbsp;·&nbsp; **[GitOps repo ➜](https://github.com/aniket-devop/gitops-kubernetes-config)**

</td></tr>
</table>

<br>

### Azure Network Foundation

<table>
<tr><td>

![Azure](https://img.shields.io/badge/AZURE-0078D4?style=flat-square) ![IaC](https://img.shields.io/badge/TERRAFORM_IaC-7B42BC?style=flat-square) ![Security](https://img.shields.io/badge/NETWORK_SECURITY-D14836?style=flat-square)

**A hub-and-spoke Azure network built entirely in Terraform.** Hub VNet with Firewall and Bastion, spoke VNet with a deny-by-default NSG and an AKS-ready subnet, egress forced through the Firewall, and an RBAC-authorized Key Vault. Deployable to `dev` and `prod` from one DRY configuration.

`Hub VNet (Firewall + Bastion) ➜ Spoke VNet (NSG + AKS subnet) ➜ Key Vault`

<img src="https://skillicons.dev/icons?i=terraform,azure,githubactions&perline=8" alt="Azure network stack" />
<br>
<sub>Also: Azure Firewall · Bastion · Key Vault · Azure RBAC</sub>

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/azure-network-foundation-terraform/main/diagrams/architecture.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/azure-network-foundation-terraform/main/diagrams/architecture.png" alt="Azure Network Foundation Architecture" width="100%">
  </a>
</p>

**Engineering decisions**
- RBAC scoped to the resource group, not the subscription, to limit blast radius
- Explicit `DenyAllInbound` rule instead of relying on platform defaults
- Bastion instead of a jump box, so no VM carries a public IP

<sub>**Honest scope:** sandbox-scale project, not a full Cloud Adoption Framework landing zone. CI runs `fmt`, `init`, and `validate` only.</sub>

**[Repository ➜](https://github.com/aniket-devop/azure-network-foundation-terraform)**

</td></tr>
</table>

<br>

### AWS Landing Network

<table>
<tr><td>

![AWS](https://img.shields.io/badge/AWS-FF9900?style=flat-square&logoColor=white) ![IaC](https://img.shields.io/badge/TERRAFORM_IaC-7B42BC?style=flat-square)

**The same private-compute pattern, rebuilt in AWS.** One VPC across two AZs, ALB-fronted EC2 in private subnets, outbound-only access through a NAT Gateway, and Terraform state stored remotely in S3 with DynamoDB locking.

`Internet ➜ ALB (public) ➜ EC2 (private) ➜ NAT Gateway ➜ Internet`

<img src="https://skillicons.dev/icons?i=aws,terraform,githubactions&perline=8" alt="AWS stack" />
<br>
<sub>Also: VPC · EC2 · ALB · IAM · S3 · DynamoDB</sub>

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/aws-terraform-landing-zone-project/main/diagrams/architecture.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/aws-terraform-landing-zone-project/main/diagrams/architecture.png" alt="AWS Landing Zone Architecture" width="100%">
  </a>
</p>

**Engineering decisions**
- EC2 security groups accept traffic only from the ALB
- Every PR runs `fmt -check` ➜ `validate` ➜ `plan` through GitHub Actions

<sub>**Honest scope:** self-driven hands-on project. Azure is my primary professional cloud.</sub>

**[Repository ➜](https://github.com/aniket-devop/aws-terraform-landing-zone-project)**

</td></tr>
</table>

<br>

### Airflow Observability Pipeline

<table>
<tr><td>

![Observability](https://img.shields.io/badge/OBSERVABILITY-E6522C?style=flat-square) ![Client Project](https://img.shields.io/badge/FREELANCE_CLIENT_PROJECT-30363D?style=flat-square)

**A containerized Airflow deployment with a full metrics pipeline.** Re-architected from Airflow's official CeleryExecutor/Redis template into a single-node LocalExecutor + PostgreSQL setup, instrumented end to end, and started with one `docker compose up`.

`Airflow ➜ StatsD Exporter ➜ Prometheus (15s scrape) ➜ Grafana`

<img src="https://skillicons.dev/icons?i=docker,postgres,prometheus,grafana&perline=8" alt="Observability stack" />
<br>
<sub>Also: Docker Compose · Apache Airflow · StatsD</sub>

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/airflow-docker-grafana-monitoring/main/assets/architecture-diagram.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/airflow-docker-grafana-monitoring/main/assets/architecture-diagram.png" alt="Airflow Observability Architecture" width="100%">
  </a>
</p>

**Engineering decisions**
- Dropped the message broker and worker fleet that add no value at single-node scale
- StatsD Exporter bridges Airflow metrics into Prometheus, since Airflow exposes no native `/metrics` endpoint in this setup

<sub>**Honest scope:** working single-node deployment with a verified metrics pipeline. No pre-provisioned dashboards or alerting.</sub>

**[Repository ➜](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)**

</td></tr>
</table>

---

## Tech Stack

<div align="center">

| Domain | Tools |
|:-:|:-:|
| **Cloud** | <img src="https://skillicons.dev/icons?i=azure,aws&perline=8" alt="Cloud" /> |
| **IaC & CI/CD** | <img src="https://skillicons.dev/icons?i=terraform,githubactions&perline=8" alt="IaC and CI/CD" /> |
| **Containers** | <img src="https://skillicons.dev/icons?i=docker,kubernetes&perline=8" alt="Containers" /> |
| **Monitoring** | <img src="https://skillicons.dev/icons?i=prometheus,grafana&perline=8" alt="Monitoring" /> |
| **Languages & OS** | <img src="https://skillicons.dev/icons?i=python,bash,linux,git&perline=8" alt="Languages and OS" /> |

</div>

<br>

Also working with: **Azure DevOps Pipelines · AKS · Helm · ArgoCD · Trivy · TFLint · TFSec · Checkov · FastAPI · PostgreSQL**

---

## Experience

**DevOps Engineer · DevOps Insiders**

- Provision and manage Azure infrastructure with Terraform: resource groups, virtual networks, and AKS
- Build and maintain CI/CD pipelines with GitHub Actions and Azure DevOps Pipelines
- Containerize applications with Docker and deploy to Kubernetes/AKS using Helm
- Apply DevSecOps practices by integrating security and IaC scanning into the delivery lifecycle
- Set up monitoring and observability with Prometheus and Grafana
- Troubleshoot pipeline, infrastructure, and deployment issues across environments

---

## Let's Talk

I'm open to **DevOps / Cloud Engineer** roles, full-time, in Bengaluru or remote. If something here fits a role you're hiring for, or you want to compare notes on Terraform module design, AKS networking, or GitOps patterns, reach out.

<div align="center">

<br>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Message_me-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)

<br>

*Built to run, documented to be understood.*

</div>
