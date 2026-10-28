<div align="center">

<img src="assets/banner.svg" alt="Aniket Kumar — DevOps Engineer | Cloud Infrastructure | Automation" width="100%"/>

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-aniket484-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![GitHub](https://img.shields.io/badge/GitHub-aniket--devop-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)
![Open to roles](https://img.shields.io/badge/Open_to-DevOps_/_Cloud_roles-2ea043?style=for-the-badge)

**[Featured projects](#-featured-projects)** · **[Tech stack](#-tech-stack)** · **[Live demo](https://github.com/aniket-devop/axion-cloud-infrastructure/blob/main/docs/demo/axion-deployment-demo.mp4)** · **[Contact](#-lets-talk)**

</div>

<br/>

## 👋 About

DevOps Engineer with 2 years of hands-on experience in Azure infrastructure, Terraform, CI/CD, Kubernetes, and DevSecOps. At **DevOps Insiders** I work on Azure provisioning and pipeline automation.

On my own time I build things that actually run: a live AKS platform, a GitOps pipeline with Git-only rollback, a hub-and-spoke Azure network. I'd rather find where a design breaks on my own dime than on a client's. Every project below documents its limits and roadmap openly.

📍 Bengaluru, India &nbsp;·&nbsp; 🎓 BCA, Chandigarh Group of Colleges

<br/>

<img src="assets/pipeline.svg" alt="Delivery flow: commit, validate and scan, build, reconcile, observe" width="100%"/>

<br/>

## 🧰 Tech Stack

<table>
<tr>
<td width="170"><b>☁️ Cloud</b></td>
<td>
<img src="https://img.shields.io/badge/Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white" alt="Azure"/>
<img src="https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white" alt="AWS"/>
<sub>&nbsp;Azure is primary; AWS is project-level</sub>
</td>
</tr>
<tr>
<td><b>🏗️ Infrastructure as Code</b></td>
<td>
<img src="https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white" alt="Terraform"/>
</td>
</tr>
<tr>
<td><b>📦 Containers &amp; Orchestration</b></td>
<td>
<img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker"/>
<img src="https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white" alt="Kubernetes"/>
<img src="https://img.shields.io/badge/AKS-0078D4?style=flat-square&logo=microsoftazure&logoColor=white" alt="AKS"/>
<img src="https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white" alt="Helm"/>
</td>
</tr>
<tr>
<td><b>🔁 CI/CD &amp; GitOps</b></td>
<td>
<img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" alt="GitHub Actions"/>
<img src="https://img.shields.io/badge/Azure_DevOps-0078D7?style=flat-square&logo=azuredevops&logoColor=white" alt="Azure DevOps"/>
<img src="https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white" alt="Argo CD"/>
</td>
</tr>
<tr>
<td><b>🔐 DevSecOps</b></td>
<td>
<img src="https://img.shields.io/badge/Trivy-1904DA?style=flat-square&logoColor=white" alt="Trivy"/>
<img src="https://img.shields.io/badge/TFLint-5C4EE5?style=flat-square" alt="TFLint"/>
<img src="https://img.shields.io/badge/tfsec-0B3D91?style=flat-square" alt="tfsec"/>
<img src="https://img.shields.io/badge/Checkov-1F6FEB?style=flat-square" alt="Checkov"/>
<sub>&nbsp;Trivy in my GitOps project; the rest from professional work</sub>
</td>
</tr>
<tr>
<td><b>📊 Observability</b></td>
<td>
<img src="https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white" alt="Prometheus"/>
<img src="https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white" alt="Grafana"/>
<img src="https://img.shields.io/badge/StatsD-6E7681?style=flat-square" alt="StatsD"/>
</td>
</tr>
<tr>
<td><b>🐧 Systems &amp; Code</b></td>
<td>
<img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Linux"/>
<img src="https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white" alt="Bash"/>
<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"/>
<img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI"/>
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
<img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white" alt="Git"/>
</td>
</tr>
</table>

<br/>

## 🏗️ Featured Projects

### 1 &nbsp;Axion Intelligence Platform &nbsp;⭐
<sub>Terraform → ACR → AKS, end to end, serving real traffic</sub>

<table>
<tr>
<td width="48%" valign="top">
<a href="https://github.com/aniket-devop/axion-cloud-infrastructure/blob/main/docs/demo/axion-deployment-demo.mp4">
<img src="https://github.com/aniket-devop/axion-cloud-infrastructure/raw/main/docs/screenshots/02-fleet-summary.png" alt="Axion fleet dashboard running on AKS. Click to watch the deployment demo" width="100%"/>
</a>
<br/><sub>▶ Click to watch the deployment walkthrough</sub>
</td>
<td valign="top">
27 simulated industrial assets stream telemetry every 5 seconds into a live dashboard with 3D digital twins and real-time health scoring. Terraform provisions Azure, GitHub Actions builds images into ACR, and Kubernetes manifests roll the workloads onto AKS.
<br/><br/>
<b>Key decisions</b><br/>
• Terraform <code>for_each</code> over an <code>environments</code> map: one module tree renders dev, staging, and prod<br/>
• Remote state bootstrapped from a separate <code>state-infrastructure/</code> stack<br/>
• ACR <code>admin_enabled = false</code>: identity-based auth only<br/>
• Ingestion and query split into separate services so each scales on its own<br/>
• Path-filtered image builds: a frontend commit doesn't rebuild the backend
<br/><br/>
<sub><b>Honest scope:</b> Terraform workflow is plan-only; DB credentials are inline (Key Vault, PVC, and Ingress/TLS are on the roadmap).</sub>
<br/><br/>
<code>Terraform</code> <code>AKS</code> <code>ACR</code> <code>GitHub Actions</code> <code>FastAPI</code> <code>React</code> <code>PostgreSQL</code>
<br/><br/>
<b><a href="https://github.com/aniket-devop/axion-cloud-infrastructure">View repository →</a></b>
</td>
</tr>
</table>

<br/>

### 2 &nbsp;GitOps CI/CD Pipeline
<sub>CI builds and scans. Argo CD deploys. CI never touches the cluster.</sub>

<table>
<tr>
<td width="48%" valign="top">
<a href="https://github.com/aniket-devop/gitops-kubernetes-config">
<img src="https://raw.githubusercontent.com/aniket-devop/gitops-kubernetes-config/main/screenshots/architecture-diagram.png" alt="GitOps pipeline architecture" width="100%"/>
</a>
</td>
<td valign="top">
A two-repo GitOps setup. One repo owns the FastAPI app and its pipeline; the other owns the desired cluster state that Argo CD reconciles.
<br/><br/>
<b>Key decisions</b><br/>
• Trivy <code>CRITICAL</code> gate hard-fails the build before an image reaches GHCR<br/>
• Two separately scoped tokens, so GitHub Actions never holds cluster credentials<br/>
• Argo CD with <code>automated</code>, <code>prune</code>, and <code>selfHeal</code><br/>
• <b>Rollback is a <code>git revert</code></b>: no <code>kubectl rollout undo</code>, no Argo CD CLI<br/>
• Non-root container on <code>python:3.12-alpine</code>
<br/><br/>
<sub><b>Honest scope:</b> runs on a local Kind cluster; only <code>dev</code> is fully automated.</sub>
<br/><br/>
<code>GitHub Actions</code> <code>Docker</code> <code>Trivy</code> <code>GHCR</code> <code>Helm</code> <code>Argo CD</code> <code>Kind</code>
<br/><br/>
<b><a href="https://github.com/aniket-devop/gitops-ci-pipeline">App repo →</a></b> &nbsp;·&nbsp; <b><a href="https://github.com/aniket-devop/gitops-kubernetes-config">GitOps repo →</a></b>
</td>
</tr>
</table>

<br/>

### 3 &nbsp;Azure Terraform Network Foundation
<sub>Hub-and-spoke, deny-by-default, no public IPs on compute</sub>

<table>
<tr>
<td width="48%" valign="top">
<a href="https://github.com/aniket-devop/azure-network-foundation-terraform">
<img src="https://raw.githubusercontent.com/aniket-devop/azure-network-foundation-terraform/main/diagrams/architecture.png" alt="Azure network foundation architecture" width="100%"/>
</a>
</td>
<td valign="top">
A hub VNet (Firewall and Bastion), a spoke VNet with a deny-by-default NSG and an AKS-ready subnet, and an RBAC-authorized Key Vault. Deployable to <code>dev</code> and <code>prod</code> from one Terraform configuration.
<br/><br/>
<b>Key decisions</b><br/>
• Route table forces AKS egress through the Firewall, so its rules are actually enforced<br/>
• RBAC scoped to the resource group, not the subscription, to limit blast radius<br/>
• Explicit <code>DenyAllInbound</code> instead of relying on platform defaults<br/>
• Azure Bastion instead of a jump box<br/>
• Key Vault via RBAC and network ACL: a documented trade-off against Private Endpoint
<br/><br/>
<sub><b>Honest scope:</b> sandbox-scale, not a full landing zone. CI runs <code>fmt</code>, <code>init</code>, and <code>validate</code> only.</sub>
<br/><br/>
<code>Terraform</code> <code>Azure Firewall</code> <code>Bastion</code> <code>Key Vault</code> <code>Azure RBAC</code> <code>GitHub Actions</code>
<br/><br/>
<b><a href="https://github.com/aniket-devop/azure-network-foundation-terraform">View repository →</a></b>
</td>
</tr>
</table>

<br/>

### 4 &nbsp;More builds

<table>
<tr>
<td width="50%" valign="top">
<b>AWS Landing Network</b><br/>
<sub>Terraform · VPC · ALB · EC2 · S3 · DynamoDB</sub>
<br/><br/>
<a href="https://github.com/aniket-devop/aws-terraform-landing-zone-project">
<img src="https://raw.githubusercontent.com/aniket-devop/aws-terraform-landing-zone-project/main/diagrams/architecture.png" alt="AWS landing zone architecture" width="100%"/>
</a>
<br/><br/>
The Azure private-compute pattern, rebuilt on AWS. Multi-AZ VPC with ALB-fronted EC2 in private subnets, outbound via NAT, and remote Terraform state in S3 with DynamoDB locking. Every PR runs <code>fmt</code>, <code>validate</code>, and <code>plan</code>.
<br/><br/>
<b><a href="https://github.com/aniket-devop/aws-terraform-landing-zone-project">View repository →</a></b>
</td>
<td width="50%" valign="top">
<b>Airflow Observability Pipeline</b><br/>
<sub>Docker Compose · Airflow · StatsD · Prometheus · Grafana</sub>
<br/><br/>
<a href="https://github.com/aniket-devop/airflow-docker-grafana-monitoring">
<img src="https://raw.githubusercontent.com/aniket-devop/airflow-docker-grafana-monitoring/main/assets/architecture-diagram.png" alt="Airflow observability architecture" width="100%"/>
</a>
<br/><br/>
Client project. I re-architected Airflow's Celery/Redis reference setup into a single-node <code>LocalExecutor</code> deployment, dropping a broker and worker fleet that added nothing at that scale, then wired a StatsD → Prometheus → Grafana metrics pipeline. One <code>docker compose up</code>.
<br/><br/>
<b><a href="https://github.com/aniket-devop/airflow-docker-grafana-monitoring">View repository →</a></b>
</td>
</tr>
</table>

<br/>

## 📬 Let's Talk

I'm open to **DevOps / Cloud Engineer** roles, full-time, in Bengaluru or remote. If something here matches what you're hiring for, or you want to compare notes on Terraform module design, AKS networking, or GitOps patterns, message me.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Message_me-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)

<!-- Optional: add your email as a clickable badge
[![Email](https://img.shields.io/badge/Email-Write_to_me-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:YOUR_EMAIL_HERE)
-->
