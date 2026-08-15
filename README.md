# 🚖 Uber Ride-Matching Kubernetes Autoscaling Case Study (VPA)

A production-grade Kubernetes architecture case study implementing **Vertical Pod Autoscaling (VPA)** for high-throughput, microservice-based workloads like **Uber's Ride-Matching Service**. 

This repository demonstrates how to dynamically adjust CPU and memory reservations for containerized workloads using custom controllers, TLS-secured admission webhooks, and Kubernetes CRDs.

---

## 🏗️ Architecture & Components

The VPA architecture consists of three main components running alongside the core **Ride-Matching Service**:

1. **VPA Recommender**: Monitors historical resource utilization and computes recommended CPU/Memory limits.
2. **VPA Updater**: Evicts pods that need resource adjustments so they can be recreated with updated specs.
3. **VPA Admission Controller**: Intercepts pod creation requests to mutate and inject updated resource requests automatically.

---

## 📁 Repository Structure

```text
.
├── admission-controller-deployment.yaml   # Deployment for VPA admission webhook
├── recommender-deployment.yaml            # Deployment for VPA recommendation engine
├── updater-deployment.yaml                # Deployment for VPA pod evictor/updater
├── ride-matching-deployment.yaml          # Sample core service deployment
├── ride-matching-service.yaml             # Kubernetes service for ride-matching
├── ride-matching-vpa.yaml                 # VPA resource configuration manifest
├── vpa-crd.yaml                           # Custom Resource Definitions (CRDs)
├── vpa-v1-crd-gen.yaml                    # Generated v1 CRD definitions
├── vpa-rbac.yaml                          # Role-Based Access Control policies
└── vpa-tls/                               # TLS certificates & keys for Admission Controller
    ├── serverCert.pem
    ├── serverKey.pem
    ├── tls.csr
    ├── vpa.crt
    └── vpa.key
