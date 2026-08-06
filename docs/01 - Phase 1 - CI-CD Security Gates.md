
# Phase 1: CI/CD Security Gates (Shift-Left Pipeline)

## 1. Architectural Concept: "Shift-Left"
* **What is it?** Moving security checks to the earliest possible stage in the software development lifecycle (during the commit/build phase, before deployment).
* **Why do we do it?** Fixing a vulnerability in a Git repository costs almost nothing. Fixing a breached running container in production is expensive and dangerous.

## 2. Tools Used in This Phase
| Tool | Purpose | What it Scans |
| :--- | :--- | :--- |
| **Checkov** | Infrastructure as Code (IaC) Scanner | Terraform files & Kubernetes YAML manifests for misconfigurations. |
| **Trivy** | Container Vulnerability Scanner | Docker images & OS-level packages for known CVEs (Common Vulnerabilities and Exposures). |
| **GitHub Actions** | CI/CD Automation Engine | Automates running Checkov and Trivy on every Git push. |

## 3. Step-by-Step Execution Log
### Step 1.1: Local Repository Initialization
* [x] Initialized local Git repository
* [x] Created base project structure
* [x] Set up permanent SSH authentication (`ed25519` key) for passwordless `git push`.

### Step 1.2: Creating the Target Files to Scan
* [x] Added Dockerfile
* [x] Added Kubernetes Deployment YAML

### Step 1.3: Creating the GitHub Actions Workflow
* [x] Created `.github/workflows/security-pipeline.yml`
* [x] Verified Checkov and Trivy scan execution

## 4. Errors & Troubleshooting Log
*(Record any pipeline failures or syntax errors here along with how we fixed them)*