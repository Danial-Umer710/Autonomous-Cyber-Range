
# Phase 2: GitOps Cluster Setup (Kind & ArgoCD)

## 1. Architectural Concept: "GitOps & Self-Healing"
* **What is GitOps?** A practice where Git is the single source of truth for infrastructure. Automated software inside the cluster syncs the live environment to match the Git repository.
* **Why use it for security?** 
  1. Prevents manual tampering by eliminating direct human access to production clusters.
  2. Provides automatic **Self-Healing**: if an attacker modifies a running pod, ArgoCD detects the configuration drift and immediately restores it to match the safe Git state.

## 2. Tools Used in This Phase
| Tool | Purpose | How it Fits Our Architecture |
| :--- | :--- | :--- |
| **Kind** | Kubernetes in Docker | Runs our local multi-node Kubernetes cluster inside WSL Docker containers. |
| **ArgoCD** | GitOps Continuous Delivery | Sits inside the cluster, watches our GitHub `/k8s` directory, and deploys our target honeypot automatically. |

## 3. Step-by-Step Execution Log
### Step 2.1: Local Cluster Creation
* [x] Verified Docker and Kind installation
* [x] Created local Kubernetes cluster (`cyber-range-cluster`)

### Step 2.2: ArgoCD Installation
* [x] Created `argocd` namespace
* [x] Deployed ArgoCD controller manifests

ArgoCD passsword: M3gSTKtZZxOZ3usw

### Step 2.3: Accessing the UI & Credentials
* [x] Retrieved initial admin password
* [x] Port-forwarded ArgoCD UI to localhost:8080

### Step 2.4: Configuring the GitOps Application
* [x] Connected ArgoCD to our remote GitHub repository
* [x] Successfully synced `k8s/deployment.yaml` into the cluster

## 4. Errors & Troubleshooting Log
*(Record any port conflicts, Docker issues, or ArgoCD sync errors here)*