```mermaid

flowchart TD
    subgraph Step1 ["1. CI/CD & Security Gates"]
        Code[GitHub Repository] -->|Git Push| Scanner[Trivy & Checkov Scanners]
    end

    subgraph Step2 ["2. Target Infrastructure"]
        Scanner -->|Deploy via IaC| Argo[ArgoCD GitOps]
        Argo -->|Deploys| Honeypot[Vulnerable App / Honeypot]
    end

    subgraph Step3 ["3. Offense (Red Team)"]
        Caldera[MITRE Caldera Bot] -->|Attacks| Honeypot
    end

    subgraph Step4 ["4. Defense (Blue Team)"]
        Honeypot -->|Kernel Activity| Falco[Falco eBPF Detector]
        Falco -->|Alerts| Wazuh[Wazuh SIEM / SOC]
    end

    subgraph Step5 ["5. AI & Attack Graph Engine"]
        Wazuh -->|Raw Logs| Python[Custom Python Agent]
        Python -->|Analyze Logs| Ollama[Local AI: Ollama]
        Python -->|Map Attack Path| Neo4j[(Neo4j Graph Database)]
        Python -.->|Quarantine Pod| Honeypot
    end