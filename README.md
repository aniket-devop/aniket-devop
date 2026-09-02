# Hi, I'm Aniket Kumar 👋

**DevOps Engineer — Azure, Terraform, Kubernetes, CI/CD, GitOps**

I build and automate cloud infrastructure, containerized workloads, CI/CD pipelines, and monitoring solutions through hands-on projects and professional experience. Currently completing a DevOps internship, open to full-time DevOps / Cloud Engineering roles.

Core stack: **Azure · AWS · Terraform · Kubernetes (AKS) · Docker · Helm · ArgoCD · GitHub Actions · Trivy · Checkov · Prometheus · Grafana**

[LinkedIn](https://linkedin.com/in/aniket484) · [Email](mailto:aniketkmr484@gmail.com)

---

## About Me

BCA graduate currently working as a DevOps Intern at **DevOps Insiders**, where I write Terraform modules, build CI/CD pipelines, and help keep dev/QA/staging environments in sync.

Outside that role, I build Azure and AWS infrastructure projects on my own time — landing zone patterns, GitOps delivery pipelines, and observability stacks. None of this is production infrastructure carrying real traffic; it's self-built and sized for one person to run and re-run, but built with the patterns a real environment needs: scoped access, network segmentation, and gates before deploy.

---

## Featured Projects

### 1. GitOps CI/CD Pipeline
Automates the path from a Git push to a running pod, with a security gate in between — no manual `kubectl apply`, and drift is corrected automatically instead of discovered later.

- **Tech:** FastAPI, Docker, GitHub Actions, Trivy, GHCR, Helm, ArgoCD, Kubernetes (Kind)
- **Workflow:** Push → GitHub Actions (test, build, Trivy scan, CVE gate) → GHCR → config repo updated → ArgoCD syncs the cluster
- **Practices demonstrated:** GitOps delivery, container vulnerability scanning as a hard gate, automated sync/self-healing, Git-based rollback
- **Repos:** [gitops-demo-app](https://github.com/aniket-devop/gitops-demo-app) (application) · [gitops-k8s-config](https://github.com/aniket-devop/gitops-k8s-config) (cluster config)

### 2. Azure Landing Zone in Terraform
A hub-and-spoke Azure network built to replace copy-pasted networking modules with one parameterized setup — a second environment is a `tfvars` change, not a duplicated module.

- **Tech:** Terraform, Azure Firewall, Bastion, Key Vault, RBAC
- **Workflow:** Hub VNet (Firewall + Bastion) peered to a spoke VNet with an NSG-bounded AKS subnet; Key Vault locked to that subnet
- **Practices demonstrated:** Infrastructure as Code, network segmentation, least-privilege RBAC scoped per resource group, remote state
- **Repo:** [azure-landing-zone-terraform](https://github.com/aniket-devop/azure-landing-zone-terraform)

### 3. Airflow Observability Pipeline (Freelance)
Built for a freelance client: replaced Airflow's default CeleryExecutor + Redis setup with a simpler LocalExecutor + PostgreSQL architecture, then instrumented it end-to-end for monitoring.

- **Tech:** Docker Compose, Apache Airflow, PostgreSQL, StatsD, StatsD Exporter, Prometheus, Grafana
- **Workflow:** Airflow → StatsD Exporter → Prometheus (15s scrape) → Grafana
- **Practices demonstrated:** Observability instrumentation, Docker Compose orchestration with health checks, executor architecture trade-off decisions
- **Repo:** [airflow-docker-grafana-monitoring](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)

### 4. AWS Landing Zone in Terraform
A modular, multi-AZ AWS foundation: public/private subnet segmentation, an ALB fronting EC2 instances with no public IP, and IAM-governed access with no SSH keys.

- **Tech:** Terraform, VPC, ALB, EC2, IAM, Systems Manager, GitHub Actions
- **Workflow:** Internet → ALB (public subnets) → EC2 (private subnets); CI validates every PR via `fmt`/`validate`/`plan`, authenticated through GitHub OIDC (no long-lived AWS keys)
- **Practices demonstrated:** Least-privilege IAM, SSM Session Manager instead of SSH, OIDC-based CI authentication, modular Terraform design
- **Repo:** [aws-terraform-landing-zone-project](https://github.com/aniket-devop/aws-terraform-landing-zone-project)

---

## Experience

**Professional — DevOps Intern, DevOps Insiders** *(Aug 2025 – present)*
Provision Azure infrastructure using reusable Terraform modules; maintain CI/CD pipelines across GitHub Actions and Azure DevOps; deploy containerized applications on AKS with Docker and Helm; configure Prometheus/Grafana monitoring; troubleshoot pod failures in production-style environments.

**Freelance — Airflow Observability Pipeline**
Built and delivered a monitoring pipeline for a client's Apache Airflow deployment (see Featured Projects above).

**Personal / Portfolio — Landing Zones & GitOps**
Azure and AWS Terraform landing zones, and a GitOps CI/CD pipeline with ArgoCD — built independently to go deeper on infrastructure and delivery patterns beyond day-to-day internship work.

---

## Technical Stack

**Cloud:** Azure, AWS
**Infrastructure as Code:** Terraform
**Containers & Orchestration:** Docker, Kubernetes (AKS), Helm, ArgoCD / GitOps
**CI/CD:** GitHub Actions, Azure DevOps Pipelines
**Security:** Trivy, Checkov, tfsec, TFLint
**Monitoring:** Prometheus, Grafana
**Languages & Tools:** Python, Bash, Linux, Git

---

## Open to Work

Open to full-time **DevOps Engineer / Cloud Engineer** roles — immediate joiner, based in Noida, open to remote.

[LinkedIn](https://linkedin.com/in/aniket484) · [Email](mailto:aniketkmr484@gmail.com) · [GitHub](https://github.com/aniket-devop)
