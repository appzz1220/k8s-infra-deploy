# k8s-infra-deploy

This repository contains Kubernetes manifests and CI/CD pipeline definitions used to deploy and manage infrastructure using a GitOps-driven workflow. It integrates with Jenkins to automatically apply changes to different environments based on branch promotion.

---

## 📁 Project Structure

```bash
.
├── Jenkinsfile          # Jenkins pipeline for CI/CD
├── deployment.yaml      # Kubernetes Deployment manifest
├── service.yaml         # Kubernetes Service manifest
├── ingress.yaml         # Ingress rule for app exposure
└── README.md            # Documentation

# Trigge