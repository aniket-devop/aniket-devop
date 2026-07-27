<div align="center">

# Aniket Kumar

### DevOps Engineer · Azure · AWS · Terraform · Kubernetes · CI/CD

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/aniket-devop)

</div>

---

## About Me

DevOps Engineer with 1 year of hands-on experience automating cloud infrastructure and CI/CD pipelines on Microsoft Azure. I work primarily with Terraform for infrastructure as code, Azure Kubernetes Service (AKS) for container orchestration, and GitHub Actions / Azure DevOps Pipelines for automating build, test, and deployment workflows. I also build in security scanning (Trivy, SonarQube) and monitoring (Prometheus, Grafana) as part of the pipeline rather than as an afterthought.

I'm currently extending this into AWS through a self-driven personal project, and I'm looking for a full-time DevOps or Cloud Engineering role where I can keep building on this foundation.

- 🔧 Currently working as a **DevOps Intern at DevOps Insiders**, provisioning and maintaining Azure infrastructure across dev, QA, and staging environments
- 🌱 Currently deepening my AWS skills (VPC, EC2, ALB, IAM) through a personal infrastructure project
- 🎓 BCA graduate, Chandigarh Group of Colleges, Mohali
- 📍 Based in Noida, India

---

## Core Skills

**Infrastructure as Code** — Terraform (reusable modules, remote state, plan/apply workflows)
**Cloud Platforms** — Microsoft Azure (VNets, Load Balancer, Firewall, Bastion, Key Vault, AKS), AWS (EC2, VPC, IAM, S3, ALB)
**CI/CD & Automation** — GitHub Actions, Azure DevOps Pipelines
**Containers & Orchestration** — Docker, Kubernetes (AKS), Helm
**Monitoring & Security** — Prometheus, Grafana, Trivy, SonarQube
**Scripting & Version Control** — Python, Bash, Linux, Git, GitHub

---

## Technology Stack

<div align="center">

![Azure](https://skillicons.dev/icons?i=azure) ![AWS](https://skillicons.dev/icons?i=aws) ![Terraform](https://skillicons.dev/icons?i=terraform) ![Docker](https://skillicons.dev/icons?i=docker) ![Kubernetes](https://skillicons.dev/icons?i=kubernetes) ![GithubActions](https://skillicons.dev/icons?i=githubactions) ![Grafana](https://skillicons.dev/icons?i=grafana) ![Prometheus](https://skillicons.dev/icons?i=prometheus) ![Python](https://skillicons.dev/icons?i=python) ![Bash](https://skillicons.dev/icons?i=bash) ![Linux](https://skillicons.dev/icons?i=linux) ![Git](https://skillicons.dev/icons?i=git)

</div>

---

## Featured Projects

### [Azure Landing Zone with Hub-and-Spoke Network](https://github.com/aniket-devop/azure-landing-zone-terraform)
`Terraform` `Azure Firewall` `Bastion` `Key Vault` `Private DNS` `GitHub Actions`

Hub-and-spoke network built with Azure Firewall and Bastion, peering the hub VNet to 2+ spoke VNets through 5 purpose-built Terraform modules (networking, firewall, bastion, Key Vault, storage). Brought new environment setup down from days to under 15 minutes. Hardened with deny-by-default NSGs and a Key Vault behind a private endpoint, with a GitHub Actions pipeline running `terraform plan`/`validate` on every pull request and manual approval required before apply.

### DevSecOps Pipeline for Microservices on AKS
`AKS` `Docker` `Kubernetes` `Helm` `Trivy` `SonarQube` `Prometheus` `Grafana` `GitHub Actions`

Containerized a 4-service application and deployed it to AKS using Helm charts for pod scaling, service configuration, and ingress. Integrated Trivy and SonarQube scanning into the pipeline to block builds with critical CVEs or failed quality gates, and set up Prometheus and Grafana dashboards to monitor pod health and resource usage. Commit-to-deploy automated end to end, taking a merged pull request to AKS in under 10 minutes.
*Repository not yet public — available on request.*

### AWS Landing Network (Personal Project)
`Terraform` `VPC` `EC2` `ALB` `IAM` `S3` `DynamoDB`

Multi-AZ VPC with public and private subnets, an ALB routing traffic to EC2 instances in private subnets, and a NAT Gateway for outbound-only internet access. Security groups restrict EC2 traffic to the ALB only, with scoped IAM instance roles in place of managed admin policies. Terraform remote state configured with S3 and DynamoDB locking, plus a GitHub Actions workflow running `fmt`/`validate`/`plan` on every pull request.

<div align="center">
<img src="./assets/aws-landing-network-diagram.png" alt="AWS Landing Network Architecture Diagram" width="800"/>
</div>

*Repository not yet public — available on request.*

---

## Current Learning

- Extending Terraform work on AWS to build cross-cloud infrastructure experience
- Deepening Kubernetes and Helm practices around security and observability

---

## GitHub Stats

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=aniket-devop&show_icons=true&theme=default&hide_border=true&count_private=true" alt="GitHub Stats" height="165"/>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=aniket-devop&layout=compact&hide_border=true&theme=default" alt="Top Languages" height="165"/>

<img src="https://github-readme-streak-stats.herokuapp.com/?user=aniket-devop&hide_border=true&theme=default" alt="GitHub Streak Stats"/>

</div>

---

## Contact

**Email:** [aniketkmr484@gmail.com](mailto:aniketkmr484@gmail.com)
**LinkedIn:** [linkedin.com/in/aniket484](https://linkedin.com/in/aniket484)
**GitHub:** [github.com/aniket-devop](https://github.com/aniket-devop)

I'm actively looking for full-time DevOps / Cloud Engineering opportunities. Feel free to reach out — happy to walk through any of the projects above in more depth.

<div align="center">

![Profile Views](https://komarev.com/ghpvc/?username=aniket-devop&style=flat-square&color=blue)

</div>

