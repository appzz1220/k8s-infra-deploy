# k8s-infra-deploy

This repository contains the infrastructure-as-code (IaC) manifests for deploying and managing Kubernetes workloads using a GitOps-style CI/CD pipeline. It integrates with Jenkins to automatically apply changes to a Kubernetes cluster based on updates pushed to this repository.

---

## 📁 Project Structure

```bash
.
├── Jenkinsfile          # CI/CD pipeline definition for Jenkins
├── deployment.yaml      # Kubernetes Deployment manifest
├── service.yaml         # Kubernetes Service manifest
├── ingress.yaml         # Ingress resource for external access
└── README.md            # This documentation
