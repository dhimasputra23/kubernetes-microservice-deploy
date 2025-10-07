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




## 🔄 CI/CD Workflow (GitHub Actions + ArgoCD)
GitHub Actions (CI)
Triggered on every push or PR:
Build & tag Docker images
Push to Google Artifact Registry
Update Helm values.yaml image tag
Commit back changes to main branch
ArgoCD (CD)
Watches Git repo for Helm chart changes
Automatically syncs updates to GKE cluster
Provides rollback, health checks, and visual dashboards


## 🧰 Helm Deployment Commands (Manual Mode)
# Create namespace
kubectl create namespace dev

# Install Helm chart
helm install microservices ./helm -n dev -f helm/values-dev.yaml

# Upgrade deployment
helm upgrade microservices ./helm -n dev -f helm/values-dev.yaml

# Rollback if needed
helm rollback microservices <revision-number>

## 🧩 ArgoCD Application Example
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: microservices-app
  namespace: argocd
spec:
  project: default
  source:
    repoURL: 'https://github.com/<your-username>/kubernetes-microservices-deploy.git'
    targetRevision: main
    path: helm
  destination:
    server: 'https://kubernetes.default.svc'
    namespace: dev
  syncPolicy:
    automated:
      prune: true
      selfHeal: true



📊 Observability
Integrated monitoring stack:
Prometheus – Metrics collection from services
Grafana – Dashboard for visualization
Cloud Monitoring (GCP) – Logs and alerts





