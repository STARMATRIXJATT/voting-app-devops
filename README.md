# voting-app-devops
CI/CD pipeline implementation for a Kubernetes-based Voting App using Azure DevOps for Continuous Integration and ArgoCD for Continuous Deployment.
# Voting App DevOps Pipeline

This repository contains the CI/CD pipeline setup for a Kubernetes-based Voting App. The CI pipeline is managed using **Azure DevOps Pipelines**, and the CD is handled via **ArgoCD**.

## 🔧 Tools Used:
- Azure DevOps Pipelines
- Docker
- Azure Container Registry (ACR)
- Kubernetes (AKS or any k8s cluster)
- ArgoCD
- GitOps workflow

## 🧩 What does this repo include?
- `azure-pipelines.yml`: Defines the CI pipeline for building & pushing Docker images.
- `scripts/updateK8sManifests.sh`: Bash script to automate image tag updates in Kubernetes manifests.
- `k8s-specifications/`: Directory containing Kubernetes deployment YAML files.
- `.dockerignore` & `Dockerfile` (for the Voting App)

## ⚙️ CI/CD Workflow:
1. **CI**: Azure DevOps pipeline triggers on commits to build Docker images and push them to ACR.
2. **CD**: ArgoCD monitors the repo and auto-syncs Kubernetes manifests to deploy new versions automatically.

## 🚀 Benefits:
- Automated builds & deployments
- Seamless integration with ACR & Kubernetes
- GitOps-driven deployment model
- Auto rollback and sync using ArgoCD

## 📂 Folder Structure:
├── azure-pipelines.yml ├── k8s-specifications/ │ └── vote-deployment.yaml ├── scripts/ │ └── updateK8sManifests.sh ├── vote/ │ └── Dockerfile
