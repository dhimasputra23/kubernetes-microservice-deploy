# 🚀 Kubernetes Microservices Deployment on GKE (Helm + ArgoCD + GitHub Actions)

A production-grade **DevOps portfolio project** showcasing a fully automated **GitOps workflow** with **Google Kubernetes Engine (GKE)**, **Helm**, **ArgoCD**, and **GitHub Actions**.  
This project demonstrates how to build, package, and continuously deliver containerized microservices with enterprise-level scalability, observability, and maintainability.

---

## 🧠 Overview

This repository is designed as a **real-world DevOps case study** for deploying multiple microservices to a Kubernetes cluster using **GitOps principles**.

Key Highlights:
- ✅ Microservices architecture on **Google Kubernetes Engine (GKE)**
- ✅ Declarative deployments using **Helm Charts**
- ✅ Continuous Deployment (CD) via **ArgoCD GitOps synchronization**
- ✅ CI pipeline with **GitHub Actions** (build, test, push, deploy)
- ✅ Integrated observability stack (Prometheus, Grafana)
- ✅ Modular, environment-specific configuration (`dev`, `staging`, `prod`)

---

## 🏗️ Architecture Diagram

![Architecture Diagram](docs/diagram.png)

### Flow Summary
1. **Developer Pushes Code** → GitHub repository triggers CI pipeline.
2. **GitHub Actions** → Builds Docker images, pushes to Artifact Registry.
3. **Helm Charts Updated** → Helm templates define Kubernetes manifests.
4. **ArgoCD Syncs Automatically** → ArgoCD detects changes and applies them to GKE.
5. **Microservices Deployed** → Application runs with full observability and auto-scaling.

---

## ⚙️ Tech Stack

| Layer | Tools |
|-------|--------|
| Cloud Platform | Google Cloud Platform (GKE, Artifact Registry, Cloud Monitoring) |
| CI/CD | GitHub Actions + ArgoCD |
| Infrastructure as Code | Terraform (for cluster provisioning), Helm (for deployment) |
| Containerization | Docker |
| Observability | Prometheus, Grafana |
| Databases | PostgreSQL, MongoDB, MySQL |
| Gateway | NGINX Ingress Controller |

---

## 🧩 Repository Structure

```bash
kubernetes-microservices-deploy/
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml                # GitHub Actions pipeline
│
├── helm/
│   ├── Chart.yaml                   # Helm chart metadata
│   ├── values-dev.yaml              # Dev environment configuration
│   ├── values-prod.yaml             # Prod environment configuration
│   └── templates/
│       ├── deployment.yaml
│       ├── service.yaml
│       ├── ingress.yaml
│       └── configmap.yaml
│
├── infra/
│   ├── terraform/                   # Optional: GKE cluster provisioning
│   └── argocd/
│       ├── application.yaml         # ArgoCD application definition
│       └── project.yaml             # ArgoCD project scope
│
├── services/
│   ├── auth-service/
│   │   ├── Dockerfile
│   │   └── src/
│   ├── product-service/
│   │   ├── Dockerfile
│   │   └── src/
│   └── order-service/
│       ├── Dockerfile
│       └── src/
│
├── docs/
│   └── diagram.png                  # Architecture diagram
│
└── README.md
