<h1 align="center">Aniket Kumar</h1>

<p align="center">
  <strong>DevOps Engineer</strong> · Azure · Terraform · Kubernetes · GitOps · DevSecOps
</p>

<p align="center">
  <em>Infrastructure reproducible from code, pipelines that gate on security, and clusters that reconcile from Git.</em>
</p>

<p align="center">
  <img alt="Azure" src="https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white">
  <img alt="Terraform" src="https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white">
  <img alt="Kubernetes" src="https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white">
  <img alt="Argo CD" src="https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white">
  <img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white">
  <img alt="Docker" src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white">
</p>

<p align="center">
  <a href="#featured-projects">Projects</a> ·
  <a href="#technical-skills">Skills</a> ·
  <a href="https://www.linkedin.com/in/aniket484">LinkedIn</a>
</p>

> **Open to full-time DevOps / Cloud Engineer roles.**

## About

I work mainly on Azure. My focus is infrastructure as code with Terraform, CI/CD pipelines, containerised deployments on Kubernetes, and building security checks into the delivery process. The projects below are personal builds, and each README states what is and is not implemented.

- **Cloud and automation:** Azure (primary), AWS (project-level)
- **Infrastructure as Code:** Terraform modules, remote state, multi-environment configuration
- **CI/CD:** GitHub Actions, Azure DevOps Pipelines
- **Containers and Kubernetes:** Docker, AKS, Helm
- **GitOps:** Argo CD
- **Security and monitoring:** Trivy scanning gates, Prometheus, Grafana

## Experience

<!-- CONFIRM: exact job title and dates as shown on LinkedIn, and add them here -->
**DevOps Insiders**

- Provisioned Azure infrastructure with Terraform (resource groups, virtual networks, AKS)
- Built and maintained CI/CD pipelines in GitHub Actions and Azure DevOps
- Deployed containerised workloads to AKS with Helm
- Added IaC and security scanning to delivery pipelines
- Set up monitoring with Prometheus and Grafana

## Featured projects

### [Axion Intelligence Platform](https://github.com/aniket-devop/axion-cloud-infrastructure)

`Personal project` · Terraform · Azure (AKS, ACR) · Kubernetes · GitHub Actions · FastAPI · React · PostgreSQL

An industrial IoT telemetry platform with 27 simulated assets, built to show the full path from an empty Azure subscription to a running system. Terraform provisions the Azure footprint, GitHub Actions builds and pushes images to ACR, and Kubernetes manifests deploy five workloads to AKS.

- Terraform `for_each` over an `environments` map renders multiple environments from one module tree
- Remote state is bootstrapped by a separate stack, which solves the backend chicken-and-egg problem
- ACR runs with `admin_enabled = false`, and image builds are path-filtered

**Scope:** database credentials are inline, storage is `emptyDir`, and there is no Ingress/TLS or autoscaling yet. These are listed in the repo roadmap.

[README](https://github.com/aniket-devop/axion-cloud-infrastructure) · [Deployment walkthrough video](https://github.com/aniket-devop/axion-cloud-infrastructure/blob/main/docs/demo/axion-deployment-demo.mp4)

![Axion architecture: Terraform provisions Azure, GitHub Actions pushes images to ACR, AKS runs the workloads](https://raw.githubusercontent.com/aniket-devop/axion-cloud-infrastructure/main/docs/architecture.png)

---

### GitOps CI/CD Pipeline: FastAPI → Argo CD → Kubernetes

`Personal project` · GitHub Actions · Trivy · GHCR · Helm · Argo CD · Kind

A two-repository GitOps setup. CI tests, builds, scans and publishes an image, then stops at a Git commit. Argo CD is the only component with cluster access and reconciles the cluster from that commit.

- A Trivy gate fails the build on any CRITICAL finding before the image reaches the registry
- Two separately scoped tokens, so neither can touch the cluster
- Rollback is a `git revert` of the image-tag commit, with no `kubectl` involved

**Scope:** local Kind cluster only. Only `dev` is automated. No Ingress/TLS, autoscaling, NetworkPolicy or monitoring yet.

[App and CI repo](https://github.com/aniket-devop/gitops-ci-pipeline) · [GitOps config repo](https://github.com/aniket-devop/gitops-kubernetes-config)

<details>
<summary>Architecture diagram</summary>

![GitOps pipeline architecture: GitHub Actions publishes to GHCR and commits the tag; Argo CD reconciles the Kind cluster](https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png)

</details>

---

### [Azure Hub-and-Spoke Network Foundation](https://github.com/aniket-devop/azure-network-foundation-terraform)

`Personal project` · Terraform · Azure Firewall · Bastion · Key Vault · Azure RBAC · GitHub Actions

A Terraform networking and security foundation built from seven reusable modules, composed identically for `dev` and `prod` (only `.tfvars` differ).

- All spoke egress is forced through the Firewall by a route table, so its rules are actually enforced
- Deny-by-default NSG, and Bastion instead of public jump hosts
- RBAC scoped to the resource group, not the subscription

**Scope:** no compute is deployed. CI runs `fmt` and `validate` only. It is not a Cloud Adoption Framework landing zone.

<details>
<summary>Architecture diagram</summary>

![Azure hub-and-spoke architecture with Firewall, Bastion, spoke NSG and Key Vault](https://raw.githubusercontent.com/aniket-devop/azure-network-foundation-terraform/main/diagrams/architecture.png)

</details>

---

### [AWS Multi-AZ Network with Terraform](https://github.com/aniket-devop/aws-terraform-landing-zone-project)

`Personal project` · Terraform · VPC · ALB · EC2 · IAM · S3 · DynamoDB

A two-AZ VPC with public and private subnets, an ALB in front of EC2 instances in private subnets, shell access through SSM instead of SSH keys, and remote state in S3 with DynamoDB locking. CI runs `fmt`, `validate` and `plan` on pull requests. Azure is my primary cloud, and this is my AWS hands-on project.

<details>
<summary>Architecture diagram</summary>

![AWS architecture: multi-AZ VPC with ALB and private EC2 instances](https://raw.githubusercontent.com/aniket-devop/aws-terraform-landing-zone-project/main/diagrams/architecture.png)

</details>

---

### [Airflow Observability Pipeline](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)

`Freelance client project` · Docker Compose · Apache Airflow · PostgreSQL · Prometheus · Grafana · StatsD

Re-architected Airflow's official CeleryExecutor/Redis template into a single-node LocalExecutor + PostgreSQL stack, then added a StatsD → Prometheus → Grafana metrics pipeline. Eight services start with one `docker compose up`.

- Removed the broker and worker fleet, which add nothing at single-node scale
- Bridged metrics with the StatsD Exporter, since Airflow exposes no native Prometheus endpoint here

**Scope:** the metrics pipeline is verified, but no dashboards or alerting are provisioned.

<details>
<summary>Architecture diagram</summary>

![Airflow observability architecture: Airflow emits StatsD metrics to an exporter, scraped by Prometheus and visualised in Grafana](https://raw.githubusercontent.com/aniket-devop/airflow-docker-grafana-monitoring/main/assets/architecture-diagram.png)

</details>

## Technical skills

| Area | Shown in public repos | Used at work† |
|---|---|---|
| Cloud | Azure, AWS | Azure |
| IaC | Terraform | Terraform |
| CI/CD | GitHub Actions | Azure DevOps Pipelines |
| Containers | Docker, Compose, Kubernetes, AKS, Helm | Helm on AKS |
| GitOps | Argo CD | – |
| Security | Trivy | Checkov, TFLint, tfsec |
| Monitoring | Prometheus, Grafana | Prometheus, Grafana |
| Languages and OS | Python (FastAPI, pytest) | Bash, Linux |

<sub>† Used in my professional work, not demonstrated in my public repositories.</sub>

## Planned next

From my own repo roadmaps. None of this is implemented yet.

- Key Vault-backed secrets, Ingress with TLS and autoscaling for Axion
- `plan` on pull requests and IaC security scanning for the Azure foundation
- A dev → staging promotion path, and moving the GitOps demo to AKS
- Provisioned Grafana dashboards and Alertmanager for the Airflow stack

## Education

BCA, Chandigarh Group of Colleges, Mohali

## Contact

Looking for DevOps / Cloud Engineer roles? Message me on [LinkedIn](https://www.linkedin.com/in/aniket484).
