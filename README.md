<div align="center">

# Aniket Kumar

### Cloud & DevOps Engineer
**Azure · Terraform · Kubernetes · GitOps**

Infrastructure reproducible from code, pipelines that gate on security,<br>and clusters that reconcile from Git.

<br>

![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)

[Featured projects](#featured-projects) · [Toolkit](#technical-toolkit) · [LinkedIn](https://linkedin.com/in/aniket484)

</div>

> **Open to DevOps / Cloud Engineer roles** · Bengaluru or remote

I'm a DevOps Engineer at **DevOps Insiders** with 2 years of hands-on experience. My day-to-day is Azure infrastructure with Terraform, CI/CD in GitHub Actions and Azure DevOps, and containerised deployments to AKS.

Outside work I build projects to find out where a design breaks. The four below are public, documented with architecture diagrams and evidence, and each one states plainly what it does *not* do.

---

## Engineering focus

| Area | What I build | See it in |
|---|---|---|
| **Infrastructure as Code** | Modular Terraform, remote state, one configuration rendering multiple environments | [Axion](https://github.com/aniket-devop/axion-cloud-infrastructure) · [Azure Network](https://github.com/aniket-devop/azure-network-foundation-terraform) |
| **Secure networking** | Hub-and-spoke, deny-by-default NSGs, forced firewall egress, Bastion instead of public jump hosts, resource-group-scoped RBAC | [Azure Network](https://github.com/aniket-devop/azure-network-foundation-terraform) |
| **CI/CD & GitOps** | Test → scan → publish pipelines; Argo CD reconciles desired state; rollback via `git revert` | [GitOps pipeline](https://github.com/aniket-devop/gitops-kubernetes-config) |
| **Containers & Kubernetes** | Non-root and multi-stage Docker images, AKS, Helm | [Axion](https://github.com/aniket-devop/axion-cloud-infrastructure) · [GitOps pipeline](https://github.com/aniket-devop/gitops-kubernetes-config) |
| **Observability** | StatsD → Prometheus → Grafana metrics pipeline | [Airflow monitoring](https://github.com/aniket-devop/airflow-docker-grafana-monitoring) |

---

## Featured projects

### Axion Intelligence Platform
**Azure · Terraform · AKS · GitHub Actions** — [`axion-cloud-infrastructure`](https://github.com/aniket-devop/axion-cloud-infrastructure)

```text
Terraform ▸ Azure (RG · ACR · AKS)  ▸  GitHub Actions ▸ build + push to ACR  ▸  Kubernetes manifests ▸ AKS
```

An industrial IoT telemetry platform (27 simulated assets) built to show the full path from an empty Azure subscription to a running system. Terraform provisions the Azure footprint, GitHub Actions builds images into ACR, and Kubernetes manifests roll five workloads (ingestion API, query API, simulator, PostgreSQL, React UI) onto AKS. Documented with screenshots and a [deployment walkthrough video](https://github.com/aniket-devop/axion-cloud-infrastructure/blob/main/docs/demo/axion-deployment-demo.mp4).

- Terraform `for_each` over an `environments` map: one module tree renders dev, staging and prod
- Remote state bootstrapped by a separate stack, which solves the chicken-and-egg backend problem
- ACR with `admin_enabled = false`; path-filtered image builds; infrastructure workflow is plan-only by design

**Demonstrates:** end-to-end Azure delivery with modular Terraform, container builds, and Kubernetes rollout.
**Implemented:** all of the above, as documented in the repo. **Not yet:** Key Vault-backed secrets (DB credentials are inline), persistent volumes (`emptyDir`), Ingress/TLS, autoscaling, probes and resource limits. These are listed in the repo's roadmap.

<details>
<summary>Architecture diagram</summary>
<br>
<img src="https://github.com/aniket-devop/axion-cloud-infrastructure/raw/main/docs/architecture.png" alt="Axion architecture: Terraform provisions Azure, GitHub Actions pushes images to ACR, AKS runs the workloads" width="100%">
</details>

---

### GitOps CI/CD Pipeline: FastAPI → Argo CD → Kubernetes
**GitHub Actions · Trivy · Helm · Argo CD** — [`gitops-ci-pipeline`](https://github.com/aniket-devop/gitops-ci-pipeline) (app + CI) · [`gitops-kubernetes-config`](https://github.com/aniket-devop/gitops-kubernetes-config) (desired state)

```text
push ▸ pytest ▸ build ▸ Trivy CRITICAL gate ▸ GHCR ▸ git commit (image tag) ▸ Argo CD ▸ Kind cluster
```

A two-repository GitOps setup. CI builds, tests, scans and publishes an image, then stops at a Git commit. Argo CD, the only component with cluster access, reconciles the cluster from that commit.

- Trivy gate fails the build on any CRITICAL finding *before* the image reaches GHCR
- Two separately scoped credentials: `GITHUB_TOKEN` for the registry, `GITOPS_REPO_TOKEN` for the config repo; neither can touch the cluster
- Rollback is a pure Git operation: reverting the image-tag commit was enough for Argo CD's `selfHeal` to restore the previous version

**Demonstrates:** GitOps boundaries, supply-chain scanning in CI, Helm packaging, and reconciliation-based rollback.
**Implemented:** the full dev flow on a local Kind cluster. **Not yet:** staging promotion (staging needs a manual sync), Ingress/TLS, autoscaling, NetworkPolicy/RBAC, monitoring, a managed cloud cluster.

<details>
<summary>Architecture diagram</summary>
<br>
<img src="https://github.com/aniket-devop/gitops-kubernetes-config/raw/main/screenshots/architecture-diagram.png" alt="GitOps pipeline architecture: GitHub Actions publishes to GHCR and commits the tag; Argo CD reconciles the Kind cluster" width="100%">
</details>

---

### Azure Hub-and-Spoke Network Foundation
**Terraform · Azure Firewall · Bastion · Key Vault · RBAC** — [`azure-network-foundation-terraform`](https://github.com/aniket-devop/azure-network-foundation-terraform)

```text
Hub VNet (Firewall · Bastion) ◂▸ peering ◂▸ Spoke VNet (deny-by-default NSG · AKS subnet) ▸ egress via Firewall
```

A Terraform-built networking and security foundation: seven reusable modules, composed identically for `dev` and `prod` (only `.tfvars` differ).

- All spoke egress forced through the Firewall by a route table, so its allow-rules are actually enforced
- Explicit `DenyAllInbound` NSG rule and Bastion instead of public jump hosts; no VM needs a public IP
- RBAC scoped to the resource group, not the subscription, to limit blast radius

**Demonstrates:** secure network design and least-privilege IAM expressed as reusable Terraform.
**Implemented:** network, Firewall, Bastion, Key Vault (RBAC + network ACL), role assignments; CI runs `fmt` and `validate`. **Not yet:** compute (no AKS cluster deployed), `plan`/`apply` automation, security scanning, automated tests. It is also not a Cloud Adoption Framework landing zone.

<details>
<summary>Architecture diagram</summary>
<br>
<img src="https://github.com/aniket-devop/azure-network-foundation-terraform/raw/main/diagrams/architecture.png" alt="Azure hub-and-spoke architecture with Firewall, Bastion, spoke NSG and Key Vault" width="100%">
</details>

---

### Airflow Observability Pipeline
**Docker Compose · Airflow · Prometheus · Grafana** — [`airflow-docker-grafana-monitoring`](https://github.com/aniket-devop/airflow-docker-grafana-monitoring) · *freelance client project*

```text
Airflow (StatsD) ▸ StatsD Exporter ▸ Prometheus (15s scrape) ▸ Grafana
```

A containerised Apache Airflow deployment, re-architected from the official CeleryExecutor/Redis template to a single-node LocalExecutor + PostgreSQL stack, then instrumented end to end. Eight services start with one `docker compose up`.

- Removed the broker and worker fleet that add no value at single-node scale, while keeping health checks, dependency ordering and persistent metadata
- Bridged metrics with the StatsD Exporter, since Airflow exposes no native Prometheus endpoint in this configuration

**Demonstrates:** Compose orchestration, metrics instrumentation, and sensible simplification.
**Implemented:** a verified metrics pipeline (Prometheus target up; Grafana querying 129 `airflow_*` metrics). **Not yet:** provisioned dashboards, alerting, persistent storage for Prometheus/Grafana, pinned image versions.

<details>
<summary>Architecture diagram</summary>
<br>
<img src="https://github.com/aniket-devop/airflow-docker-grafana-monitoring/raw/main/assets/architecture-diagram.png" alt="Airflow observability architecture: Airflow services emit StatsD to an exporter, scraped by Prometheus and visualised in Grafana" width="100%">
</details>

**Also:** [`aws-terraform-landing-zone-project`](https://github.com/aniket-devop/aws-terraform-landing-zone-project) is an independent AWS project: multi-AZ VPC, ALB, private EC2 reached via SSM, remote state in S3 with DynamoDB locking, and plan-on-PR CI. Azure is my primary cloud; AWS is portfolio-level.

---

## Technical toolkit

| Category | Demonstrated in public repos | Used professionally† |
|---|---|---|
| **Cloud** | Azure (AKS, ACR, VNet, Firewall, Bastion, Key Vault, RBAC) · AWS (VPC, ALB, EC2, IAM, S3, DynamoDB), portfolio only | Azure |
| **IaC** | Terraform (modules, remote state, multi-environment tfvars) | Terraform |
| **CI/CD** | GitHub Actions | Azure DevOps Pipelines |
| **Containers & orchestration** | Docker, Docker Compose, Kubernetes, AKS, Helm | Helm on AKS |
| **GitOps** | Argo CD (local Kind cluster) | — |
| **Security** | Trivy | Checkov, TFLint, tfsec |
| **Monitoring** | Prometheus, Grafana, StatsD Exporter | Prometheus, Grafana |
| **Scripting & OS** | Python (FastAPI, pytest) | Bash, Linux |

<sub>† Used in my professional work; not demonstrated in my public repositories.</sub>

---

## Engineering principles

- **Everything in code.** Even the Terraform state backend is created by code ([Axion](https://github.com/aniket-devop/axion-cloud-infrastructure)).
- **Least privilege.** Resource-group-scoped RBAC, ACR admin disabled, separate tokens per task.
- **Private by default.** Deny-by-default NSGs, Bastion instead of public jump hosts, instances without public IPs.
- **Gate before publish.** A failed scan stops an image before it reaches the registry.
- **Git as the source of truth.** Deploys and rollbacks go through the same reconciliation path.
- **State the scope.** Every project lists what is not built.

---

## Next on my roadmap

Taken from my own repo roadmaps. **None of this is implemented yet.**

- Key Vault-backed secrets, Ingress with TLS, and autoscaling for Axion
- `plan` on pull requests plus IaC security scanning for the Azure foundation
- A dev → staging promotion path, and moving the GitOps demo to AKS
- Provisioned Grafana dashboards and Alertmanager for the Airflow stack

---

## Connect

I'm looking for DevOps / Cloud Engineer roles. If a project here is relevant to what you're hiring for, or you'd like to talk Terraform, AKS or GitOps, message me on [LinkedIn](https://linkedin.com/in/aniket-devop-placeholder).

<sub>BCA, Chandigarh Group of Colleges, Mohali</sub>
