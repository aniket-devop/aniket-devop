<div align="center">

# Aniket Kumar

**Azure DevOps Engineer · DevSecOps · Platform Automation**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)

![Profile Views](https://komarev.com/ghpvc/?username=aniket-devop&style=flat-square&color=blue)

</div>

<br>

## About

I build Azure infrastructure with Terraform, and wire DevSecOps controls (scanning, policy checks, quality gates) directly into the CI/CD pipelines that deploy it. My work centers on treating infrastructure the same way application code is treated: version-controlled, reviewed, and reproducible rather than hand-configured.

I'm not claiming production-scale enterprise experience — the projects below are infrastructure I designed and built myself to work the way real production systems do, and that's the level I'm operating at right now.

<br>

## Stack

<table>
<tr>
<td valign="top" width="50%">

**Cloud**
<br>
<img src="https://skillicons.dev/icons?i=azure" height="32"/>

Azure · Azure DevOps · Azure Entra ID

**Infrastructure as Code**
<br>
<img src="https://skillicons.dev/icons?i=terraform" height="32"/>

Terraform · Bicep · Ansible

**Containers & Orchestration**
<br>
<img src="https://skillicons.dev/icons?i=docker,kubernetes" height="32"/>

Docker · Kubernetes · Helm · ArgoCD

</td>
<td valign="top" width="50%">

**CI/CD**
<br>
<img src="https://skillicons.dev/icons?i=githubactions,jenkins" height="32"/>

Azure Pipelines · GitHub Actions · Jenkins

**DevSecOps**

Trivy · Checkov · SonarQube · Azure Key Vault · HashiCorp Vault (basics)

**Monitoring**
<br>
<img src="https://skillicons.dev/icons?i=prometheus,grafana" height="32"/>

Prometheus · Grafana

**Languages & VCS**
<br>
<img src="https://skillicons.dev/icons?i=python,bash,git,github" height="32"/>

</td>
</tr>
</table>

<br>

## Projects

### Azure Landing Zone — Terraform

A reusable landing zone built against Microsoft's Cloud Adoption Framework, structured as composable Terraform modules rather than one-off scripts.

| Component | Implementation |
|---|---|
| Networking | Hub-and-spoke topology, NSGs, Azure Bastion for private access |
| Identity & Access | RBAC role assignments, least-privilege scoping |
| Secrets | Azure Key Vault integration |
| Structure | Resource organization by environment/subscription boundary |
| Reusability | Modularized Terraform, parameterized for reuse across environments |

### AKS Production Infrastructure — Terraform

An AKS environment provisioned to reflect production patterns — private networking and managed identity rather than default/public configurations.

- Azure Kubernetes Service + Azure Container Registry, provisioned together
- Managed Identity for cluster-to-registry auth (no stored credentials)
- Private networking for the cluster control plane
- Monitoring wired in at provision time, not bolted on after

### Azure DevOps CI/CD Pipeline

A pipeline that treats security scanning as a gate, not an afterthought.

```
Terraform Validate → Terraform Plan → Manual Approval → Terraform Apply
                              ↓
                    Trivy Scan · Checkov Scan · SonarQube Quality Gate
```

Infrastructure changes don't reach `apply` without passing static analysis and a human sign-off.

### GitOps Deployment — ArgoCD + Helm

Kubernetes application state is defined in Git and reconciled by ArgoCD, not applied manually via `kubectl`. Helm charts define the desired state; Git is the single source of truth; drift gets corrected automatically rather than silently accumulating.

### Monitoring Stack — Prometheus + Grafana

Metrics collection and dashboards provisioned alongside the infrastructure they observe, so observability isn't a separate manual step after deployment.

<br>

## GitHub Activity

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=aniket-devop&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aniket-devop&layout=compact&theme=tokyonight&hide_border=true" height="165"/>

<img src="https://github-readme-streak-stats.herokuapp.com/?user=aniket-devop&theme=tokyonight&hide_border=true"/>

</div>

<br>

## Currently Working On

- Azure Policy and governance at the landing-zone level
- Kubernetes security hardening (OPA, Kyverno)
- Terraform module testing
- Crossplane as an alternative control-plane model

<br>

## Contact

**Email** — [aniketkmr484@gmail.com](mailto:aniketkmr484@gmail.com)
**LinkedIn** — [linkedin.com/in/aniket484](https://linkedin.com/in/aniket484)
**GitHub** — [github.com/aniket-devop](https://github.com/aniket-devop)
