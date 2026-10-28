<div align="center">

# 👋 Hi, I'm Aniket Kumar

### ⚙️ DevOps Engineer &nbsp;|&nbsp; ☁️ Azure &nbsp;|&nbsp; 🏗️ Terraform &nbsp;|&nbsp; ☸️ Kubernetes &nbsp;|&nbsp; 🚀 CI/CD

**I build infrastructure that stays up and deployments that don't break production.**  
*Zero manual tweaks. Zero snowflake environments. Infrastructure fully codified & reproducible.*

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-Say%20Hi-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![Projects](https://img.shields.io/badge/See-My%20Projects-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](#-featured-projects)
[![Hiring](https://img.shields.io/badge/Status-Open%20to%20Work-22C55E?style=for-the-badge&logo=checkmarx&logoColor=white)](#-lets-connect)

<img src="https://komarev.com/ghpvc/?username=aniket-devop&label=Profile%20Views&color=0e75b6&style=flat" alt="profile views"/>

<br/>

| 🧑‍💻 Experience | ☁️ Primary Cloud | 🏗️ IaC | ☸️ Orchestration | 📍 Location |
|:---:|:---:|:---:|:---:|:---:|
| **2+ Years** | **Azure (AWS hands-on)** | **Terraform** | **Kubernetes / AKS** | **Bengaluru, India** |

</div>

<br/>

> [!IMPORTANT]
> ### ⚡ Recruiter TL;DR
> 🟢 **Target Roles:** DevOps Engineer / Cloud Engineer / Platform Engineer · Full-time (Hybrid/Remote)
>
> - 🎬 **Live Production Demo:** AKS-based multi-tier platform provisioned via Terraform ([Watch Demo](#-featured-projects))
> - 🔄 **Zero-Trust GitOps:** ArgoCD & GitHub Actions pipelines where CI never touches cluster secrets
> - 🔐 **Shift-Left Security:** Automated Trivy, Checkov & TFLint gates integrated directly into PR workflows
> - 🛠️ **Practical Engineering:** Clean documentation detailing exact scope, architectural tradeoffs, and post-mortems

---

## 🧑‍💻 Engineering Profile

I'm a **DevOps Engineer with 2+ years of experience** specializing in Azure infrastructure automation, Kubernetes orchestration, and DevSecOps pipelines. 

My daily focus centers on replacing brittle manual operations with modular Terraform stacks, zero-touch GitOps deployments, and end-to-end observability setups. I spend my personal time building real-world platform projects—testing edge cases, breaking failovers, and optimizing pipeline runs on my own environment before putting them into production.

- 🔭 **Focus Areas:** AKS cluster hardening, Terraform module abstraction, GitOps patterns (ArgoCD)
- ⚙️ **Current Role:** DevOps Engineer @ **DevOps Insiders**
- 💬 **Ask me about:** Private AKS networking, Trivy security gates, Terraform remote state locking
- 🎓 **Education:** BCA, Chandigarh Group of Colleges, Mohali

---

## 🛤️ Experience & Execution

| Period | Role | Focus & Deliverables |
|:---:|---|---|
| **Nov 2024 → Present** | **DevOps Engineer** · *DevOps Insiders* | Multi-environment Azure infrastructure via Terraform (VNets, AKS, Key Vault), end-to-end CI/CD in Azure DevOps & GitHub Actions, Helm/ArgoCD releases, Prometheus/Grafana monitoring, security gates. |
| **Aug 2023 → Oct 2024** | **DevOps & Cloud Engineer** · *Freelance / Client Projects* | Dockerized container workflows, Airflow data pipelines with StatsD/Prometheus telemetry, shell automation, and AWS infrastructure setups. |

<details>
<summary><b>💼 Core Work Responsibilities at DevOps Insiders (Click to Expand)</b></summary>
<br/>

- **IaC Automation:** Provision and maintain modular Azure architecture (VNets, Subnets, AKS, ACR, Azure SQL) using Terraform `for_each` and environment mapping.
- **CI/CD Engineering:** Author and optimize GitHub Actions & Azure DevOps pipelines for multi-branch environments with automated linting and containerization.
- **Security Integration:** Implement Trivy image vulnerability gates and IaC security checks (Checkov, TFSec, TFLint) directly into pull requests.
- **GitOps & Helm:** Package containerized workloads into custom Helm charts and synchronize deployments via ArgoCD for zero-downtime releases.
- **Observability:** Configure Prometheus metrics scraping, Grafana dashboards, and OpenTelemetry/Jaeger tracing for distributed microservices.

</details>

---

## 🧭 Production Principles

<table>
<tr>
<td width="33%" valign="top" align="center">

### 🔁 Clean Reproducibility
If it’s created in the GUI, it’s technical debt. Every resource must exist as Version-Controlled Code (Terraform/YAML).

</td>
<td width="33%" valign="top" align="center">

### 🔐 Secure by Default
Deny-by-default Network Security Groups, Managed Identities over hardcoded secrets, and build gates that block bad images.

</td>
<td width="33%" valign="top" align="center">

### 📐 Pragmatic Design
Simple architectures beat over-engineered setups. Clear docs, realistic trade-offs, and clear rollback steps.

</td>
</tr>
</table>

---

## 🔄 Delivery Workflow (GitOps Architecture)

End-to-end pipeline implementation from the [GitOps Engine Repository](https://github.com/aniket-devop/gitops-kubernetes-config):

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#0B3A6F','primaryTextColor':'#ffffff','primaryBorderColor':'#38BDF8','lineColor':'#38BDF8','secondaryColor':'#0F1A2E','tertiaryColor':'#0F1A2E','fontSize':'14px'}}}%%
flowchart LR
    A([👨‍💻 Git Push]) --> B[⚙️ GitHub Actions<br/>Build & Test]
    B --> C[🔐 Trivy Gate<br/>Fail on CRITICAL]
    C --> D[(📦 GHCR Registry)]
    D --> E[📝 GitOps Manifest<br/>Update Image Tag]
    E --> F[🔄 ArgoCD<br/>Auto-Reconcile]
    F --> G([☸️ AKS Cluster])
