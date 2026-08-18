# End-to-End Kubernetes DevOps & Monitoring Setup

An end-to-end Kubernetes cluster deployment featuring full observability with **`kube-prometheus-stack`** (Prometheus, Grafana, Alertmanager, and Node Exporters) and **Flannel CNI** networking across a multi-node architecture.

---

## Architecture Overview

* **Control Plane (`master`):** Runs API Server, Controller Manager, Scheduler, and Cluster Management tools.
* **Worker Nodes (`worker1`, `worker2`):** Run workload pods, ingress controllers, and telemetry collectors.
* **Network CNI:** Flannel (`kube-flannel`) for pod-to-pod networking across nodes.
* **Observability Stack:** `kube-prometheus-stack` deployed via Helm.

---

## Infrastructure & Tech Stack

| Component | Technology / Tool | Version / Details |
| :--- | :--- | :--- |
| **Orchestration** | Kubernetes | `v1.30.14` |
| **Container Runtime** | `containerd` / `crictl` | Runtime endpoint socket management |
| **Networking** | Flannel CNI | Multi-node bridge & overlay network |
| **Monitoring** | Prometheus & Alertmanager | Prometheus Operator architecture |
| **Visualization** | Grafana | Exposed externally via `NodePort:32000` |
| **Metrics Collector** | Node Exporter & kube-state-metrics | Per-node host & Kubernetes state metrics |

---

## Phase-by-Phase Walkthrough

### Phase 1: Cluster & Node Initialization
1. Bootstrapped Kubernetes control plane on `master` node using `kubeadm`.
2. Joined `worker1` and `worker2` to the cluster.
3. Deployed Flannel CNI (`kube-flannel`) to establish pod network communication.

### Phase 2: Deploying the Observability Stack
1. Created dedicated namespace: `kubectl create namespace monitoring`.
2. Deployed `kube-prometheus-stack` using Helm:
   ```bash
   helm repo add prometheus-community [https://prometheus-community.github.io/helm-charts](https://prometheus-community.github.io/helm-charts)
   helm repo update
   helm install prometheus-stack prometheus-community/kube-prometheus-stack -n monitoring
