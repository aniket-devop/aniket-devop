<div align="center">

# 👋 Hi, I'm Aniket Kumar

### ⚙️ DevOps Engineer &nbsp;|&nbsp; ☁️ Azure &nbsp;|&nbsp; 🏗️ Terraform &nbsp;|&nbsp; ☸️ Kubernetes &nbsp;|&nbsp; 🚀 CI/CD

**I make infrastructure boring in the right way.**
*No manual clicks. No "it works on my machine." Everything reproducible, everything in code.*

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-Say%20Hi-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![Projects](https://img.shields.io/badge/See-My%20Projects-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)](#-featured-projects)

<img src="https://komarev.com/ghpvc/?username=aniket-devop&label=Profile%20Views&color=0e75b6&style=flat" alt="profile views"/>

</div>

<br/>

> [!IMPORTANT]
> 🟢 **Open to DevOps / Cloud Engineer roles**: full-time, Bengaluru or remote. If you're hiring, jump to [Let's Connect](#-lets-connect).

<br/>

<div align="center">

| 🧑‍💻 Experience | ☁️ Primary Cloud | 🏗️ IaC | ☸️ Orchestration | 📍 Based in |
|:---:|:---:|:---:|:---:|:---:|
| **2 Years** | **Azure** | **Terraform** | **Kubernetes / AKS** | **Bengaluru, India** |

</div>

---

## 🧑‍💻 About Me

I'm a DevOps Engineer with **2 years of hands-on experience** across Azure infrastructure, Terraform, CI/CD automation, containerized deployments and DevSecOps. My day job is Azure and pipelines. My own time goes into projects I build to actually run, not just to demo.

- 🔭 **Currently building:** Azure/AKS platform projects and GitOps pipelines with ArgoCD
- ⚙️ **Day job:** DevOps Engineer @ **DevOps Insiders**, Terraform on Azure, AKS, Helm, GitHub Actions, Azure DevOps
- 🔐 **I care about:** security scanning in the pipeline (Trivy, TFLint, TFSec, Checkov), least-privilege RBAC, reproducible infra
- 💬 **Ask me about:** Terraform module design, AKS networking, GitOps patterns
- 🎓 **Education:** BCA, Chandigarh Group of Colleges, Mohali

<details>
<summary><b>💼 Professional experience (click to expand)</b></summary>
<br/>

**DevOps Engineer · DevOps Insiders**

- Provision and manage Azure infrastructure with Terraform: resource groups, virtual networks and AKS
- Build and maintain CI/CD pipelines in GitHub Actions and Azure DevOps to automate build, test and deployment
- Containerize applications with Docker and deploy to Kubernetes/AKS using Helm charts
- Integrate security and IaC scanning into the delivery lifecycle
- Set up monitoring and observability with Prometheus and Grafana
- Troubleshoot pipeline, infrastructure and deployment issues across environments
- Work with developers and QA to keep release cycles smooth and reliable

</details>

---

## 🛠️ Tech Stack

<table>
<tr>
<td width="190"><b>☁️ Cloud & IaC</b></td>
<td><img src="https://skillicons.dev/icons?i=azure,aws,terraform" alt="cloud"/></td>
</tr>
<tr>
<td><b>📦 Containers & GitOps</b></td>
<td>
<img src="https://skillicons.dev/icons?i=docker,kubernetes" alt="containers" align="top"/>
<img src="https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white" alt="Helm" align="top"/>
<img src="https://img.shields.io/badge/ArgoCD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white" alt="ArgoCD" align="top"/>
</td>
</tr>
<tr>
<td><b>🚀 CI/CD & Security</b></td>
<td>
<img src="https://skillicons.dev/icons?i=githubactions,git,github" alt="cicd" align="top"/>
<img src="https://img.shields.io/badge/Azure_DevOps-0078D7?style=for-the-badge&logo=azuredevops&logoColor=white" alt="Azure DevOps" align="top"/>
<img src="https://img.shields.io/badge/Trivy-1904DA?style=for-the-badge&logo=aqua&logoColor=white" alt="Trivy" align="top"/>
</td>
</tr>
<tr>
<td><b>📊 Monitoring</b></td>
<td><img src="https://skillicons.dev/icons?i=prometheus,grafana" alt="monitoring"/></td>
</tr>
<tr>
<td><b>💻 Languages & OS</b></td>
<td><img src="https://skillicons.dev/icons?i=python,bash,linux,fastapi,react,postgres" alt="languages"/></td>
</tr>
</table>

---

## 🏗️ Featured Projects

> [!TIP]
> Every project below has an **architecture diagram**, an **honest scope** section and a **roadmap** in its repo README.

### ⭐ Axion Intelligence Platform: live on AKS

27 simulated industrial assets stream telemetry every 5 seconds into a dashboard with 3D digital twins and real-time health scoring. Terraform provisions Azure, GitHub Actions pushes images to ACR, Kubernetes rolls them onto AKS.

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![AKS](https://img.shields.io/badge/AKS%20%2F%20ACR-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

**[→ View repo](https://github.com/aniket-devop/axion-cloud-infrastructure)**

https://github.com/aniket-devop/axion-cloud-infrastructure/raw/main/docs/demo/axion-deployment-demo.mp4

<br/>

<table>
<tr>
<td width="50%" valign="top">

#### 🔄 GitOps CI/CD Pipeline
CI builds, scans (Trivy) and publishes an image; ArgoCD deploys it. **CI never touches the cluster**, and rollback is a pure `git revert`.

![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=flat-square&logo=aqua&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)

**[App repo](https://github.com/aniket-devop/gitops-ci-pipeline) · [GitOps repo](https://github.com/aniket-devop/gitops-kubernetes-config)**

</td>
<td width="50%" valign="top">

#### 🔐 Azure Network Foundation
Hub-and-spoke network with Firewall, Bastion (no public IPs), deny-by-default NSGs and an RBAC-scoped Key Vault. One DRY config for `dev` and `prod`.

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Firewall](https://img.shields.io/badge/Azure%20Firewall-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Key Vault](https://img.shields.io/badge/Key%20Vault-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)

**[View repo](https://github.com/aniket-devop/azure-network-foundation-terraform)**

</td>
</tr>
<tr>
<td width="50%" valign="top">

#### 🌱 AWS Landing Network
Multi-AZ VPC with ALB in front of private EC2, outbound via NAT, and Terraform state locked in S3 + DynamoDB.

![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![AWS](https://img.shields.io/badge/VPC%20%2F%20ALB%20%2F%20EC2-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![S3](https://img.shields.io/badge/S3%20%2B%20DynamoDB-569A31?style=flat-square&logo=amazons3&logoColor=white)

**[View repo](https://github.com/aniket-devop/aws-terraform-landing-zone-project)**

</td>
<td width="50%" valign="top">

#### 📊 Airflow Observability Pipeline
Client project: Airflow re-architected to LocalExecutor + PostgreSQL, with a StatsD → Prometheus → Grafana metrics pipeline, started with one `docker compose up`.

![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=flat-square&logo=apacheairflow&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

**[View repo](https://github.com/aniket-devop/airflow-docker-grafana-monitoring)**

</td>
</tr>
</table>

---

## 🔥 GitHub Stats

<div align="center">

<img src="https://streak-stats.demolab.com/?user=aniket-devop&hide_border=true&theme=dark&background=0D1117&ring=38BDF8&fire=22D3A6&currStreakLabel=38BDF8" alt="streak"/>

<br/><br/>

<img height="170" src="https://github-readme-stats.vercel.app/api?username=aniket-devop&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" alt="stats"/>
<img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=aniket-devop&layout=compact&theme=tokyonight&hide_border=true" alt="languages"/>

</div>

---

## 📬 Let's Connect

Hiring for a DevOps / Cloud role, or want to talk Terraform, AKS or GitOps? I read every message.

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Message%20me-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-Send%20a%20note-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)

<br/>

⭐ *If something here helped you, a star on my repos means a lot.*

**Thanks for visiting 💙**

</div>
