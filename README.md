<div align="center">

# Hi 👋, I'm Aniket Kumar
### DevOps Engineer | Cloud & Platform Infrastructure

*I build reproducible infrastructure in code — no manual clicks, no drift.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)

<br/>

![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)

</div>

---

> 🚀 **Open to DevOps & Cloud Engineer roles (Bengaluru / Remote).** If you're hiring or want to chat about IaC, AKS, or GitOps, my inbox is open!

---

## 🎬 Live Infrastructure Demo

Most portfolios show code. This one features a **live AKS cluster** processing real telemetry from 27 simulated industrial assets, streaming data to a real-time health dashboard with 3D digital twins.

https://github.com/aniket-devop/axion-cloud-infrastructure/raw/main/docs/demo/axion-deployment-demo.mp4

👉 **[Read Full Architecture & Setup: Axion Intelligence Platform](#1-axion-intelligence-platform)**

---

## 📌 About Me

DevOps Engineer with **2 years of hands-on experience** architecting Azure infrastructure, writing modular Terraform, building automated CI/CD pipelines, and driving DevSecOps practices.

* 💼 **Current Role:** DevOps Engineer @ **DevOps Insiders**
* ☁️ **Primary Cloud:** Microsoft Azure (AKS, VNets, App Gateway, ACR, Key Vault)
* 🛠️ **IaC & Automation:** Terraform (modular, remote state, locking) & Ansible
* ☸️ **Containers & GitOps:** Docker, Kubernetes, Helm, ArgoCD
* 🔐 **DevSecOps & Scan:** Trivy, Checkov, TFLint, tfsec
* 📊 **Observability:** Prometheus, Grafana
* 🎓 **Education:** BCA — Chandigarh Group of Colleges, Mohali
* 📍 **Location:** Bengaluru, Karnataka, India

---

## 💼 Professional Experience

### **DevOps Engineer** — *DevOps Insiders*
* **Infrastructure as Code:** Provision and manage multi-environment Azure infrastructure (VNets, Subnets, NSGs, AKS, ACR) using modular Terraform with S3/Azure Blob backends and state locking.
* **CI/CD Pipelines:** Design and maintain robust CI/CD automation workflows using **GitHub Actions** and **Azure DevOps**, reducing manual deployment effort.
* **Containerization & Kubernetes:** Package microservices with Docker and deploy workloads to AKS using Helm charts.
* **DevSecOps Integration:** Shift-left security by embedding Static Application Security Testing (SAST) and IaC scanners (`Trivy`, `Checkov`, `TFLint`) directly into pipeline gates.
* **Monitoring & Support:** Configure Prometheus scrapers and Grafana dashboards for proactive node/pod monitoring and quick root-cause troubleshooting.

---

## 🏗️ Featured Projects

| Project | Description | Stack |
| :--- | :--- | :--- |
| 🌟 **[Axion Platform](#1-axion-intelligence-platform)** | Industrial IoT telemetry platform — 27 assets streaming live data deployed end-to-end on AKS | `Terraform` `Azure (AKS)` `FastAPI` `PostgreSQL` |
| 🔄 **[GitOps CI/CD Pipeline](#2-gitops-cicd-deployment-pipeline-fastapi--argocd--kind)** | Two-repo GitOps pipeline: CI tests/scans/builds, ArgoCD handles automated cluster reconciliation | `FastAPI` `ArgoCD` `Trivy` `Helm` `Kind` |
| 🔒 **[Azure Network Foundation](#3-azure-terraform-network-foundation)** | Secure Hub-and-Spoke Azure architecture with Azure Firewall, Bastion, and strict NSG boundaries | `Terraform` `Azure Firewall` `Bastion` `Key Vault` |
| ☁️ **[AWS Landing Network](#4-aws-landing-network-hands-on-project)** | Multi-AZ AWS VPC network with ALB, private EC2 instances, and locked remote backend state | `Terraform` `AWS VPC` `ALB` `S3/DynamoDB` |
| 📊 **[Airflow Observability](#5-airflow--observability-pipeline-docker-compose--prometheus--grafana)** | Re-architected containerized Airflow to LocalExecutor with StatsD → Prometheus → Grafana metrics | `Docker Compose` `Airflow` `Prometheus` `Grafana` |

---

## 🔍 Detailed Project Breakdown

### 1. Axion Intelligence Platform
🔗 **Repo:** [`axion-cloud-infrastructure`](https://github.com/aniket-devop/axion-cloud-infrastructure)  
`Terraform` `Azure (AKS, ACR)` `Kubernetes` `GitHub Actions` `FastAPI` `React` `PostgreSQL`

Industrial IoT condition-monitoring platform featuring 27 simulated assets streaming telemetry every 5 seconds. Fully automated cloud-native stack.

![Axion Architecture](https://raw.githubusercontent.com/aniket-devop/axion-cloud-infrastructure/main/docs/architecture.png)

* **Key Decisions:** Decoupled ingestion and query services; dynamic Terraform `for_each` environment maps; strict identity-based ACR access (`admin_enabled = false`).
* **Honest Scope:** Portfolio project — database secrets are currently raw Kubernetes secrets (moving to Azure Key Vault backend in next iteration).

---

### 2. GitOps CI/CD Deployment Pipeline
🔗 **App Repo:** [`gitops-ci-pipeline`](https://github.com/aniket-devop/gitops-ci-pipeline) | **Config Repo:** [`gitops-kubernetes-config`](https://github.com/aniket-devop/gitops-kubernetes-config)  
`FastAPI` `Docker` `GitHub Actions` `Trivy` `GHCR` `Helm` `ArgoCD` `Kind`

Enforces strict separation of concerns between code integration and cluster deployment state using GitOps principles.

![GitOps Pipeline Architecture](https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png)

* **Security Gate:** Pipeline hard-fails on any Trivy `CRITICAL` vulnerability finding before pushing images to GHCR.
* **Git-Driven Rollback:** Rollbacks are triggered purely via `git revert` on the manifest repo, which ArgoCD automatically reconciles.

---

### 3. Azure Terraform Network Foundation
🔗 **Repo:** [`azure-network-foundation-terraform`](https://github.com/aniket-devop/azure-network-foundation-terraform)  
`Terraform` `Azure Firewall` `Azure Bastion` `Key Vault` `Azure RBAC`

A secure enterprise Azure hub-and-spoke networking base with forced egress control.

* **Key Architecture:** Zero public IPs on internal VMs (Azure Bastion access only); forced route table egress through Azure Firewall; RBAC assigned strictly at Resource Group scope.

---

### 4. AWS Landing Network
🔗 **Repo:** [`aws-terraform-landing-zone-project`](https://github.com/aniket-devop/aws-terraform-landing-zone-project)  
`Terraform` `AWS VPC` `EC2` `ALB` `IAM` `S3` `DynamoDB`

Multi-AZ private network setup implementing high availability and secure remote state management in AWS.

---

### 5. Airflow + Observability Pipeline
🔗 **Repo:** [`airflow-docker-grafana-monitoring`](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)  
`Docker Compose` `Apache Airflow` `PostgreSQL` `Prometheus` `Grafana` `StatsD`

Production-tuned single-node Airflow stack with end-to-end metrics collection and monitoring.

---

## 🧰 Tech Stack

<div align="center">

![Azure](https://skillicons.dev/icons?i=azure) ![AWS](https://skillicons.dev/icons?i=aws) ![Terraform](https://skillicons.dev/icons?i=terraform) ![Docker](https://skillicons.dev/icons?i=docker) ![Kubernetes](https://skillicons.dev/icons?i=kubernetes) ![GithubActions](https://skillicons.dev/icons?i=githubactions) ![Grafana](https://skillicons.dev/icons?i=grafana) ![Prometheus](https://skillicons.dev/icons?i=prometheus) ![Python](https://skillicons.dev/icons?i=python) ![Bash](https://skillicons.dev/icons?i=bash) ![Linux](https://skillicons.dev/icons?i=linux) ![Git](https://skillicons.dev/icons?i=git)

</div>

| Category | Tools / Technologies |
| :--- | :--- |
| **Cloud Platforms** | Microsoft Azure (Primary), AWS (Project-based) |
| **Infrastructure as Code** | Terraform, Azure RM Provider, AWS Provider |
| **CI/CD Automation** | GitHub Actions, Azure DevOps Pipelines |
| **Containers & Orchestration** | Docker, Kubernetes, Azure Kubernetes Service (AKS), Helm, ArgoCD |
| **DevSecOps & Scanning** | Trivy, Checkov, TFLint, tfsec |
| **Monitoring & Metrics** | Prometheus, Grafana, StatsD |
| **Languages & Scripting** | Python, Bash, YAML, HCL |

---

## 📊 GitHub Analytics

<div align="center">

<img src="https://streak-stats.demolab.com/?user=aniket-devop&hide_border=true&theme=dark&background=0D1117&ring=378ADD&fire=22C55E&currStreakLabel=378ADD" alt="GitHub Streak Stats"/>

<details>
<summary><b>📈 View Detailed Contribution Stats</b></summary>
<br/>
<img src="https://github-readme-stats.vercel.app/api?username=aniket-devop&show_icons=true&theme=dark&hide_border=true&count_private=true" alt="GitHub Stats" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aniket-devop&layout=compact&hide_border=true&theme=dark" alt="Top Languages" height="165"/>
</details>

</div>

---

## 📬 Let's Connect

I am actively exploring **DevOps Engineer / Cloud Engineer** roles (Bengaluru / Remote). 

Feel free to reach out via LinkedIn or Email if you want to collaborate or discuss cloud architecture!

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-Contact%20Me-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)

</div>
