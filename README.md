<div align="center">

# Hi, I'm Aniket Kumar 👋

### DevOps Engineer • Azure • AWS • Terraform • Kubernetes • CI/CD

<p>
Building secure cloud infrastructure, production-ready CI/CD pipelines, and Infrastructure as Code using Terraform, Azure, and AWS.
</p>

<p>
Focused on designing scalable cloud platforms, automating deployments, and implementing DevSecOps best practices.
</p>

<br>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/aniket484)
[![Email](https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:aniketkmr484@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/aniket-devop)

<img src="https://komarev.com/ghpvc/?username=aniket-devop&label=Profile%20Views&color=0e75b6&style=flat" alt="Profile Views"/>

</div>

---

# 👨‍💻 About Me

I'm a **DevOps Engineer** with hands-on experience designing cloud infrastructure, automating deployments, and building production-ready CI/CD pipelines.

My focus is on building secure, scalable, and maintainable cloud platforms using **Infrastructure as Code** and modern DevOps practices.

Currently, I'm expanding my expertise across both **Microsoft Azure** and **Amazon Web Services (AWS)** while building enterprise-style infrastructure projects that closely resemble real production environments.

---

## 🚀 What I Do

- ☁️ Design Cloud Infrastructure on **Azure** and **AWS**
- 🏗️ Build reusable **Terraform Modules**
- ⚙️ Create Production CI/CD Pipelines
- ☸️ Deploy Applications on Kubernetes (AKS)
- 🐳 Containerize Applications using Docker
- 🔐 Implement DevSecOps with Trivy & SonarQube
- 📈 Monitor Infrastructure using Prometheus & Grafana
- 🔄 Automate everything possible

---

# 💼 Current Role

### DevOps Intern — DevOps Insiders

Working on production Azure infrastructure and DevOps automation.

### Responsibilities

- Azure Infrastructure Automation
- Terraform Module Development
- Azure Kubernetes Service (AKS)
- GitHub Actions
- Azure DevOps Pipelines
- Infrastructure Monitoring
- Security Hardening
- CI/CD Automation

---

# 🎯 Career Objective

I'm actively looking for a **Junior DevOps Engineer** or **Cloud Engineer** role where I can contribute to production cloud platforms, infrastructure automation, Kubernetes deployments, and DevSecOps initiatives.

---

# 🛠 Tech Stack

## ☁️ Cloud

<p>
<img src="https://skillicons.dev/icons?i=azure" />
<img src="https://skillicons.dev/icons?i=aws" />
</p>

---

## 🏗 Infrastructure as Code

<p>
<img src="https://skillicons.dev/icons?i=terraform" />
</p>

---

## ☸️ Containers & Orchestration

<p>
<img src="https://skillicons.dev/icons?i=docker" />
<img src="https://skillicons.dev/icons?i=kubernetes" />
<img src="https://skillicons.dev/icons?i=helm" />
</p>

---

## ⚙️ CI/CD

<p>
<img src="https://skillicons.dev/icons?i=githubactions" />
<img src="https://skillicons.dev/icons?i=azuredevops" />
</p>

---

## 📊 Monitoring

<p>
<img src="https://skillicons.dev/icons?i=prometheus" />
<img src="https://skillicons.dev/icons?i=grafana" />
</p>

---

## 🔐 Security

- Trivy
- SonarQube
- Azure NSGs
- Azure Firewall
- IAM Roles
- Security Groups
- Private Endpoints

---

## 💻 Languages

<p>
<img src="https://skillicons.dev/icons?i=python" />
<img src="https://skillicons.dev/icons?i=bash" />
</p>

---

## 🖥 Operating Systems

<p>
<img src="https://skillicons.dev/icons?i=linux" />
</p>

---

## 📌 Featured Projects

The following projects demonstrate production-style cloud architecture, Infrastructure as Code, DevSecOps, Kubernetes, monitoring, and cloud security best practices.

# 🏗 Featured Project 01

# Azure Landing Zone — Enterprise Hub & Spoke Architecture

<p align="center">
<img src="diagrams/azure-landing-zone.png" width="100%">
</p>

<p align="center">
<b>Production-style Azure Landing Zone built using modular Terraform with Hub & Spoke networking, Azure Firewall, Bastion, Private Endpoints and GitHub Actions.</b>
</p>

---

## 🔗 Repository

**Repository:** https://github.com/aniket-devop/azure-landing-zone-terraform

---

## 📌 Overview

This project demonstrates how enterprise Azure environments are commonly designed using a **Hub-and-Spoke Landing Zone Architecture**.

Instead of deploying resources directly into one virtual network, the infrastructure separates shared services from application workloads, allowing centralized security, easier management, and scalable expansion.

Everything is provisioned using reusable Terraform modules and automated through GitHub Actions.

---

# 🏛 Architecture Highlights

✔ Hub & Spoke Network

✔ Azure Firewall

✔ Azure Bastion

✔ Private Endpoints

✔ Azure Key Vault

✔ Virtual Network Peering

✔ GitHub Actions CI/CD

✔ Infrastructure as Code

✔ Zero Public VM Access

✔ Environment Isolation

---

# 🛠 Technologies Used

| Category | Technology |
|----------|------------|
| Cloud | Microsoft Azure |
| IaC | Terraform |
| CI/CD | GitHub Actions |
| Security | Azure Firewall |
| Remote Access | Azure Bastion |
| Secrets | Azure Key Vault |
| Networking | VNet Peering |
| OS | Linux |
| Version Control | Git |

---

# 🏗 Infrastructure Components

### Networking

- Hub Virtual Network
- Dev Spoke VNet
- QA Spoke VNet
- Staging Spoke VNet
- VNet Peering

---

### Security

- Azure Firewall
- Azure Bastion
- NSGs
- Private Endpoints
- Private DNS
- Zero Public IP Strategy

---

### Compute

- Linux Virtual Machines

---

### Secrets

- Azure Key Vault

---

### Automation

- GitHub Actions
- Terraform

---

# 🔄 Architecture Flow

1. Developer pushes code to GitHub.

2. GitHub Actions automatically runs:

- Terraform Format

- Terraform Validate

- Terraform Plan

3. Infrastructure changes require approval.

4. Terraform provisions Azure resources.

5. Shared services are deployed into the Hub Network.

6. Application workloads are deployed into Spoke Networks.

7. Azure Firewall inspects inbound and outbound traffic.

8. Azure Bastion provides secure RDP/SSH without exposing public IP addresses.

9. Key Vault securely stores application secrets.

10. Applications communicate privately using VNet Peering.

---

# 🔐 Security Features

✅ Zero Public IPs

✅ Bastion-only Administration

✅ Deny by Default NSGs

✅ Centralized Firewall

✅ Private Endpoint Access

✅ Private DNS Resolution

✅ Least Privilege Access

✅ Infrastructure as Code

---

# ⚙ CI/CD Pipeline

GitHub Push

↓

Terraform Format

↓

Terraform Validate

↓

Terraform Plan

↓

Manual Approval

↓

Terraform Apply

↓

Azure Infrastructure Updated

---

# 📁 Folder Structure

```text
azure-landing-zone-terraform/

├── modules/
│
├── networking/
│
├── firewall/
│
├── bastion/
│
├── key-vault/
│
├── storage/
│
├── environments/
│
├── dev/
│
├── qa/
│
├── staging/
│
├── .github/
│
├── workflows/
│
└── terraform.yml
```

---

# 💻 Common Commands

```bash
terraform init

terraform fmt

terraform validate

terraform plan

terraform apply
```

---

# 📈 Key Achievements

✔ Modular Terraform Architecture

✔ Enterprise Hub & Spoke Design

✔ Secure Remote Administration

✔ Zero Public Workload Exposure

✔ Reusable Infrastructure Modules

✔ Automated Infrastructure Provisioning

✔ GitHub Actions Integration

✔ Infrastructure Version Control

---

# 📚 What I Learned

During this project I gained practical experience with enterprise Azure networking concepts including Hub-and-Spoke topology, centralized security, virtual network peering, private endpoints, Infrastructure as Code, and production-style deployment workflows.

More importantly, I learned how production environments prioritize security, scalability, and maintainability over simply deploying virtual machines.

---

# 🚀 Future Improvements

- Azure Policy

- Azure Monitor

- Log Analytics

- Azure Sentinel

- Multi-Region Disaster Recovery

- Landing Zone Governance

---
# 🚀 Featured Project 02

# DevSecOps Pipeline for Microservices on Azure Kubernetes Service (AKS)

<p align="center">
<img src="diagrams/aks-devsecops.png" width="100%">
</p>

<p align="center">
<b>Production-ready DevSecOps pipeline built with GitHub Actions, Docker, Kubernetes, Helm, Trivy, SonarQube, Prometheus and Grafana.</b>
</p>

---

## 🔗 Repository

**Repository:** Available on Request

---

# 📌 Overview

This project demonstrates a complete **Commit-to-Production DevSecOps workflow** for a microservices application deployed on **Azure Kubernetes Service (AKS)**.

Instead of treating security as an afterthought, vulnerability scanning and code quality validation are integrated directly into the CI/CD pipeline.

Every deployment passes multiple automated quality gates before reaching the Kubernetes cluster.

---

# 🎯 Project Goals

✔ Automate Application Delivery

✔ Secure CI/CD Pipeline

✔ Container Security

✔ Infrastructure Automation

✔ Kubernetes Deployment

✔ Monitoring & Observability

✔ Zero Manual Production Deployments

---

# 🛠 Technologies

| Category | Technology |
|-----------|------------|
| Cloud | Microsoft Azure |
| Containerization | Docker |
| Orchestration | Kubernetes (AKS) |
| Package Manager | Helm |
| CI/CD | GitHub Actions |
| Security | Trivy |
| Code Quality | SonarQube |
| Monitoring | Prometheus |
| Dashboards | Grafana |
| Version Control | Git |

---

# 🏗 Architecture Components

## Source Control

- GitHub

---

## Continuous Integration

- GitHub Actions

- Docker Build

- Docker Image Creation

- Image Tagging

---

## Security

- Trivy Image Scan

- SonarQube Code Analysis

- Security Gates

---

## Deployment

- Helm Charts

- Kubernetes Deployments

- Services

- Ingress Controller

---

## Monitoring

- Prometheus

- Grafana

- Metrics Collection

- Dashboard Visualization

---

# 🔄 Pipeline Workflow

Developer Push

↓

GitHub Actions Trigger

↓

Docker Build

↓

Docker Image Scan (Trivy)

↓

Code Quality Check (SonarQube)

↓

Security Gate Validation

↓

Docker Image Push

↓

Helm Deployment

↓

Azure Kubernetes Service

↓

Prometheus Metrics

↓

Grafana Dashboard

---

# 🔐 Security Controls

✅ Trivy Vulnerability Scanning

✅ SonarQube Quality Gates

✅ Secure Container Images

✅ Automated Pipeline Validation

✅ Kubernetes RBAC

✅ Least Privilege Principle

✅ No Manual Production Deployments

---

# ☸ Kubernetes Architecture

Application

↓

Ingress Controller

↓

Kubernetes Services

↓

Pods

↓

Container Images

↓

Azure Kubernetes Nodes

---

# 📊 Monitoring Stack

Prometheus continuously collects:

- CPU Usage

- Memory Usage

- Pod Health

- Restart Count

- Node Metrics

- Kubernetes Events

- Cluster Health

Grafana visualizes:

- Application Health

- Infrastructure Metrics

- Cluster Performance

- Resource Utilization

- Pod Availability

---

# ⚙ CI/CD Pipeline

Git Push

↓

GitHub Actions

↓

Docker Build

↓

Trivy Scan

↓

SonarQube Scan

↓

Quality Gate

↓

Helm Upgrade

↓

AKS Deployment

↓

Production

---

# 📁 Folder Structure

```text
aks-devsecops/

├── services/
│
├── api/
│
├── auth/
│
├── frontend/
│
├── worker/
│
├── helm/
│
├── templates/
│
├── monitoring/
│
├── prometheus/
│
├── grafana/
│
├── .github/
│
├── workflows/
│
└── ci-cd.yml
```

---

# 💻 Common Commands

```bash
docker build .

docker push

helm upgrade --install

kubectl get pods

kubectl get svc

kubectl get ingress

kubectl logs

kubectl describe pod
```

---

# 📈 Key Achievements

✔ Complete CI/CD Automation

✔ Production Kubernetes Deployment

✔ Container Security Automation

✔ Infrastructure Monitoring

✔ Zero Manual Deployment

✔ Security-first Pipeline

✔ Infrastructure as Code

✔ Cloud Native Deployment

---

# 📚 What I Learned

This project helped me understand how modern DevSecOps pipelines are designed in production environments.

I gained practical experience with Kubernetes deployments, Helm packaging, container image management, GitHub Actions automation, vulnerability scanning, code quality enforcement, monitoring, and production release workflows.

More importantly, I learned that automation alone is not enough—successful production pipelines also require strong security controls, observability, and reliable deployment strategies.

---

# 🚀 Future Improvements

- ArgoCD (GitOps)

- Argo Rollouts

- Blue-Green Deployment

- Canary Deployment

- OpenTelemetry

- Azure Key Vault CSI Driver

- External Secrets Operator

- Horizontal Pod Autoscaler

- Vertical Pod Autoscaler

- KEDA Event-driven Autoscaling

---

# ☁️ Featured Project 03

# AWS Landing Network — Enterprise Multi-AZ Infrastructure

<p align="center">
<img src="diagrams/aws-landing-network.png" width="100%" alt="AWS Landing Network Architecture">
</p>

<p align="center">
<b>Production-style AWS Landing Network built using Terraform across multiple Availability Zones with private compute, ALB, IAM, S3 Remote State and DynamoDB State Locking.</b>
</p>

---

## 🔗 Repository

**Repository:** Available on Request

---

# 📌 Overview

This project demonstrates how production AWS environments are commonly designed using Infrastructure as Code.

The architecture follows AWS best practices by separating public and private resources, protecting compute instances from direct internet exposure, implementing remote Terraform state management, and deploying workloads across multiple Availability Zones for high availability.

---

# 🎯 Project Objectives

✔ Enterprise VPC Architecture

✔ Multi Availability Zone Design

✔ Infrastructure as Code

✔ Secure Networking

✔ Private Compute Layer

✔ Remote Terraform State

✔ CI/CD Ready Infrastructure

✔ Least Privilege IAM

---

# 🛠 Technologies

| Category | Technology |
|-----------|------------|
| Cloud | Amazon Web Services |
| IaC | Terraform |
| Compute | EC2 |
| Networking | VPC |
| Load Balancing | ALB |
| Identity | IAM |
| Storage | Amazon S3 |
| State Locking | DynamoDB |
| Automation | GitHub Actions |
| Version Control | Git |

---

# 🏗 Infrastructure Components

## Networking

- Amazon VPC

- Public Subnets

- Private Subnets

- Internet Gateway

- NAT Gateway

- Route Tables

- Security Groups

---

## Compute

- EC2 Instances

- IAM Instance Roles

---

## Load Balancing

- Application Load Balancer

- Target Groups

- Health Checks

---

## Terraform Backend

- Amazon S3

- DynamoDB Lock Table

---

## Automation

- GitHub Actions

- Terraform

---

# 🔄 Infrastructure Workflow

Developer Push

↓

GitHub Actions

↓

Terraform Validate

↓

Terraform Plan

↓

Approval

↓

Terraform Apply

↓

AWS Infrastructure Provisioned

↓

Application Deployment

---

# 🌐 Network Flow

Internet

↓

Internet Gateway

↓

Application Load Balancer

↓

Private EC2 Instances

↓

IAM Roles

↓

Application Services

↓

Outbound Internet through NAT Gateway

---

# 🔐 Security Architecture

✅ No Public EC2 Instances

✅ Private Subnets

✅ Security Group Isolation

✅ IAM Least Privilege

✅ ALB-only Public Access

✅ Remote Terraform State

✅ DynamoDB State Locking

✅ Infrastructure as Code

---

# 🏗 High Availability Design

The infrastructure is distributed across multiple Availability Zones.

This provides:

- High Availability

- Fault Isolation

- Improved Reliability

- Better Scalability

- Production-ready Architecture

---

# ⚙ CI/CD Pipeline

Git Push

↓

GitHub Actions

↓

Terraform Format

↓

Terraform Validate

↓

Terraform Plan

↓

Approval

↓

Terraform Apply

↓

AWS Infrastructure

---

# 📁 Folder Structure

```text
aws-landing-network/

├── diagrams/
│   ├── aws-landing-network.png
│   └── aws-landing-network.drawio
│
├── modules/
│   ├── vpc/
│   ├── alb/
│   ├── ec2/
│   └── state-backend/
│
├── environments/
│   └── dev/
│
├── .github/
│   └── workflows/
│
└── terraform.yml
```

---

# 💻 Common Commands

```bash
terraform init

terraform fmt

terraform validate

terraform plan

terraform apply
```

---

# 📈 Key Achievements

✔ Enterprise VPC Design

✔ Multi-AZ Architecture

✔ Infrastructure as Code

✔ Secure Private Networking

✔ Production-ready Terraform Modules

✔ Remote State Management

✔ Automated Deployment Workflow

✔ AWS Best Practices

---

# 📚 What I Learned

This project strengthened my understanding of AWS networking fundamentals and production infrastructure design.

I gained hands-on experience with VPC architecture, subnet planning, routing, Application Load Balancers, IAM Roles, EC2 provisioning, remote Terraform state management, and Infrastructure as Code.

One of the most valuable lessons was understanding why **remote state locking with S3 and DynamoDB** is essential for collaborative infrastructure management and how **private networking** significantly improves cloud security.

---

# 🚀 Future Improvements

- Auto Scaling Groups

- AWS WAF

- Amazon ECS

- EKS

- CloudWatch Monitoring

- AWS Systems Manager

- VPC Flow Logs

- AWS Config

- AWS GuardDuty

- Multi-Region Disaster Recovery

---
