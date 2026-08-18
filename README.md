# Kubernetes DevOps & Infrastructure Automation Lab

A complete DevOps lab demonstrating automated multi-node Kubernetes cluster configuration, package management, persistent storage, and continuous delivery pipelines.

## 🏗️ Architecture Overview

- **Control Plane:** 1x Master Node
- **Worker Nodes:** 2x Workers
- **Networking & CNI:** Flannel / Calico CNI with NodePort & Ingress routing
- **Package Management:** Helm v3
- **Infrastructure Automation:** Ansible playbooks
- **CI/CD Pipeline:** GitHub Actions with a local Self-Hosted Runner on the master node
