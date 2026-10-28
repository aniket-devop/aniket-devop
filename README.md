<div align="center">

# Aniket Kumar

### DevOps Engineer

**I make infrastructure boring in the right way.**

No manual clicks. No "it works on my machine." Everything reproducible, everything in code.

<br>

[Projects](#featured-projects) · [Stack](#tech-stack) · [Experience](#experience) · [Contact](#lets-talk)

<br>

<img src="https://skillicons.dev/icons?i=azure,aws,terraform,kubernetes,docker,githubactions&perline=6" alt="Core stack" />

<br><br>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)

</div>

<br>

> **Open to DevOps / Cloud Engineer roles** · Bengaluru or remote · Full-time

---

## About

DevOps Engineer with **2 years** of hands-on experience across Azure infrastructure, Terraform, CI/CD automation, containerized deployments, Kubernetes, and DevSecOps.

My day job is Azure and pipelines. My own time goes into projects I build to actually run, not just to demo, because I'd rather find out where a design breaks on my own dime than on a client's.

| | |
|---|---|
| **Role** | DevOps Engineer @ DevOps Insiders |
| **Focus** | Azure · Terraform · Kubernetes · CI/CD · GitOps · DevSecOps |
| **Also working with** | AWS (hands-on project), ArgoCD (personal project) |
| **Education** | BCA, Chandigarh Group of Colleges, Mohali |
| **Location** | Bengaluru, Karnataka, India |

---

## Featured Projects

<div align="center">

| # | Project | What it shows |
|:-:|---|---|
| 1 | [**Axion Intelligence Platform**](#1--axion-intelligence-platform) | Terraform + AKS, end to end |
| 2 | [**GitOps CI/CD Pipeline**](#2--gitops-cicd-pipeline) | GitHub Actions → Trivy → ArgoCD |
| 3 | [**Azure Network Foundation**](#3--azure-network-foundation) | Hub-and-spoke, deny-by-default |
| 4 | [**AWS Landing Network**](#4--aws-landing-network) | Multi-AZ VPC, ALB, remote state |
| 5 | [**Airflow Observability**](#5--airflow-observability-pipeline) | StatsD → Prometheus → Grafana |

</div>

<br>

### 1 · Axion Intelligence Platform

<img src="https://skillicons.dev/icons?i=terraform,azure,kubernetes,githubactions,fastapi,react,postgres,docker&perline=8" alt="Axion stack" />

**An industrial IoT monitoring platform running on a live AKS cluster.** 27 simulated assets (pumps, motors, compressors) across five refinery sites stream temperature, vibration, and current readings every 5 seconds into a dashboard with 3D digital twins and real-time health scoring.

Terraform provisions the Azure footprint, GitHub Actions builds and pushes images to ACR, and Kubernetes manifests roll the workloads onto AKS.

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/axion-cloud-infrastructure/main/docs/architecture.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/axion-cloud-infrastructure/main/docs/architecture.png" alt="Axion Architecture" width="90%">
  </a>
</p>

- Ingestion and query split into separate services so each scales independently
- One Terraform module tree renders dev/staging/prod through `for_each` over an `environments` map
- Remote state bootstrapped in a separate stack; ACR runs with `admin_enabled = false`

<sub>**Scope:** portfolio build with documented gaps (inline DB credentials, `emptyDir` storage, no Ingress/TLS yet), listed openly in the repo roadmap.</sub>

**[Repository](https://github.com/aniket-devop/axion-cloud-infrastructure)** · **[Watch the deployment demo](https://github.com/aniket-devop/axion-cloud-infrastructure/raw/main/docs/demo/axion-deployment-demo.mp4)**

<br>

### 2 · GitOps CI/CD Pipeline

<img src="https://skillicons.dev/icons?i=fastapi,docker,githubactions,kubernetes&perline=8" alt="GitOps stack" />

**Two repos, one boundary: CI never touches the cluster.** The app repo builds, tests, scans, and publishes an image; the config repo holds the desired state that ArgoCD reconciles.

Stack: FastAPI · Docker · Trivy · GHCR · Helm · ArgoCD · Kind

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png" alt="GitOps Pipeline Architecture" width="90%">
  </a>
</p>

- Trivy CRITICAL gate hard-fails the pipeline before an image reaches GHCR
- Non-root container on a minimal `python:3.12-alpine` base
- Rollback is a pure Git operation: reverting the image-tag commit lets ArgoCD `selfHeal` restore the previous version

<sub>**Scope:** runs on a local Kind cluster. Only `dev` is fully automated; `staging` is manual sync.</sub>

**[App repo](https://github.com/aniket-devop/gitops-ci-pipeline)** · **[GitOps repo](https://github.com/aniket-devop/gitops-kubernetes-config)**

<br>

### 3 · Azure Network Foundation

<img src="https://skillicons.dev/icons?i=terraform,azure,githubactions&perline=8" alt="Azure network stack" />

**A hub-and-spoke Azure network built entirely in Terraform.** Hub VNet with Firewall and Bastion, spoke VNet with a deny-by-default NSG and an AKS-ready subnet, egress forced through the Firewall, and an RBAC-authorized Key Vault. Deployable to `dev` and `prod` from one DRY configuration.

Stack: Terraform · Azure Firewall · Bastion · Key Vault · Azure RBAC · GitHub Actions

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/azure-network-foundation-terraform/main/diagrams/architecture.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/azure-network-foundation-terraform/main/diagrams/architecture.png" alt="Azure Network Foundation Architecture" width="90%">
  </a>
</p>

- RBAC scoped to the resource group, not the subscription, to limit blast radius
- Explicit `DenyAllInbound` rule instead of relying on platform defaults
- Bastion instead of a jump box, so no VM carries a public IP

<sub>**Scope:** sandbox-scale project, not a full Cloud Adoption Framework landing zone. CI runs `fmt`, `init`, and `validate` only.</sub>

**[Repository](https://github.com/aniket-devop/azure-network-foundation-terraform)**

<br>

### 4 · AWS Landing Network

<img src="https://skillicons.dev/icons?i=aws,terraform,githubactions&perline=8" alt="AWS stack" />

**The same private-compute pattern, rebuilt in AWS.** One VPC across two AZs, ALB-fronted EC2 in private subnets, outbound-only access through a NAT Gateway, and Terraform state stored remotely in S3 with DynamoDB locking.

Stack: Terraform · VPC · EC2 · ALB · IAM · S3 · DynamoDB

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/aws-terraform-landing-zone-project/main/diagrams/architecture.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/aws-terraform-landing-zone-project/main/diagrams/architecture.png" alt="AWS Landing Zone Architecture" width="90%">
  </a>
</p>

- EC2 security groups accept traffic only from the ALB
- Every PR runs `fmt -check` → `validate` → `plan` via GitHub Actions

<sub>**Scope:** self-driven hands-on project. Azure is my primary professional cloud.</sub>

**[Repository](https://github.com/aniket-devop/aws-terraform-landing-zone-project)**

<br>

### 5 · Airflow Observability Pipeline

<img src="https://skillicons.dev/icons?i=docker,postgres,prometheus,grafana&perline=8" alt="Observability stack" />

**A containerized Airflow deployment with a full metrics pipeline.** Delivered as a freelance client project: re-architected from Airflow's official CeleryExecutor/Redis template into a single-node LocalExecutor + PostgreSQL setup, instrumented with StatsD → Prometheus → Grafana, and started with one `docker compose up`.

Stack: Docker Compose · Apache Airflow · PostgreSQL · StatsD · Prometheus · Grafana

<p align="center">
  <a href="https://raw.githubusercontent.com/aniket-devop/airflow-docker-grafana-monitoring/main/assets/architecture-diagram.png">
    <img src="https://raw.githubusercontent.com/aniket-devop/airflow-docker-grafana-monitoring/main/assets/architecture-diagram.png" alt="Airflow Observability Architecture" width="90%">
  </a>
</p>

- Dropped the message broker and worker fleet that add no value at single-node scale
- StatsD Exporter bridges Airflow metrics into Prometheus, scraped every 15 seconds

<sub>**Scope:** working single-node deployment with a verified metrics pipeline. No pre-provisioned dashboards or alerting.</sub>

**[Repository](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)**

---

## Tech Stack

<div align="center">

<img src="https://skillicons.dev/icons?i=azure,aws,terraform,kubernetes,docker,githubactions,prometheus,grafana,python,bash,linux,git&perline=6" alt="Tech stack" />

</div>

<br>

| | |
|---|---|
| **Cloud** | Microsoft Azure (primary) · AWS |
| **IaC** | Terraform |
| **CI/CD** | GitHub Actions · Azure DevOps Pipelines |
| **Containers** | Docker · Kubernetes · AKS · Helm |
| **GitOps** | ArgoCD |
| **Security** | Trivy · TFLint · TFSec · Checkov |
| **Monitoring** | Prometheus · Grafana |
| **Languages & OS** | Python · FastAPI · PostgreSQL · Bash · Linux |

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

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Message_me-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)

</div>
