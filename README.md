# Kubernetes Microservice Deployment (Helm + ArgoCD)

This repository demonstrates how to deploy a sample Node.js app on **GKE** using:
- **Helm** for Kubernetes manifests
- **ArgoCD** for GitOps-based deployment automation

### 🚀 Deployment Flow
1. Build and push image to GCP Artifact Registry  
2. Sync ArgoCD Application to auto-deploy via Helm  
3. Access app through ingress (demo-app.example.com)

### 🧩 Highlights
✅ Declarative GitOps workflow  
✅ Environment-based Helm values  
✅ Integrated with GitLab CI or GitHub Actions  
✅ Perfect for cloud-native demo portfolios
