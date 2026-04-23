# 🚀 Andres Arias | SWE  → Platform / Cloud Infrastructure · DevOps
###  Full-Stack Cloud Engineer 

Full-stack cloud engineer focused on building observable, resilient systems using Node.js, Go, and Terraform across AWS/GCP. I specialize in asynchronous workflows, event-driven architecture, and production-grade monitoring with OpenTelemetry, Prometheus, and Grafana.
---
## 🛠 Technical Skills
**Languages:**  
Node.js, Go, Python, TypeScript

**Cloud & Infrastructure:**  
AWS, GCP, Terraform, Docker

**Architecture & Systems:**  
Microservices, Event-Driven Architecture, Async Systems, Distributed Systems Basics

**DevOps / DevSecOps:**  
CI/CD, Checkov, Observability, Infrastructure as Code

**Monitoring & Observability:**  
Prometheus, Grafana, OpenTelemetry

---
## 🏆 Certifications

- **[AWS Certified Solutions Architect – Associate](https://www.credly.com/badges/06095a2b-b56d-4876-8801-caa862bc4ad7)**  
- **[Terraform Associate (HashiCorp Certified)](https://www.credly.com/badges/2bd4abe7-1fbb-4ea2-a7a6-c609431acff3/public_url)**  
- **[AWS Certified Cloud Practitioner](https://www.credly.com/badges/d0cd5e66-64ea-4556-ae67-5b45073782a4/public_url)**
---
## 🛠 Technical Specialization

| Domain | Core Competencies |
|--------|-------------------|
| **Architecture** | Event-driven systems · Apache Kafka · Cloud-native design patterns · Asynchronous workflows |
| **Infrastructure** | GCP · AWS · Terraform (HashiCorp Certified) · Zero-Trust networking · Hub-and-Spoke topology |
| **Backend & Performance** | Go · Python (Django/FastAPI/Flask) · Node.js · Adaptive concurrency control |
| **DevSecOps** | Security-first CI/CD · Checkov · Automated SOC2 governance · Compliance-as-Code |

---
## 🚀 Currently Working On

### **[spoke-tool](https://github.com/Drecoder/spoke-tool)**

I am developing a local AI orchestration engine designed to automate the **Documentation as Infrastructure** lifecycle. It utilizes a Hub-and-Spoke architecture to ingest multi-language source code (Go, Python, Node.js) and generate high-fidelity unit tests and technical READMEs using local SLMs (Small Language Models).

#### **System Architecture**

The tool operates as a sovereign dispatcher, routing code through specialized spokes (Test & Readme) and an SLM pool (CodeLLama, Gemma) to produce verified, audited output without data leakage.

```mermaid
graph TD
    %% Top Level
    FS[("File System")]
    Git[("Git Repository")]
    
    %% Hub
    subgraph Hub[Orchestrator Hub]
        D[Dispatcher]
        M[Monitor]
        Q[Queue]
        A[Audit]
        S[Squeeze]
    end
    
    %% Spokes
    subgraph Test[Test Spoke]
        TA[Analyzer]
        TG[Generator]
        TR[Runner]
        TI[Interpreter]
    end
    
    subgraph Readme[Readme Spoke]
        RE[Extractor]
        RS[Summarizer]
        RF[Formatter]
        RM[Merger]
    end
    
    %% SLM
    subgraph SLM[SLM Pool]
        CL[CodeLLama]
        G[Gemma 2B]
        CL[CodeLLama]
        O[Ollama]
    end
    
    %% Connections
    FS --> D
    Git --> D
    D --> Q
    Q --> Test
    Q --> Readme
    
    TA --> CL
    TG --> DS
    TI --> DS
    
    RE --> CL
    RS --> G
    RS --> CL
    
    TR --> FS
    RM --> FS
    RM --> Git
    TI --> A
    
    classDef hub fill:#ff9f1c,stroke:#333,stroke-width:2px,color:#333
    classDef test fill:#2ec4b6,stroke:#333,stroke-width:2px,color:#333
    classDef doc fill:#e71d36,stroke:#333,stroke-width:2px,color:#fff
    classDef slm fill:#8338ec,stroke:#333,stroke-width:2px,color:#fff
    classDef external fill:#adb5bd,stroke:#333,stroke-width:2px,color:#333
    
    class D,M,Q,A,S hub
    class TA,TG,TR,TI test
    class RE,RS,RF,RM doc
    class CB,G,DS,O slm
    class FS,Git external
```

---

### **[Adaptive Concurrency Orchestrator](https://github.com/Drecoder/Adaptive-Concurrency-Orchestrator)**

I am architecting a high-throughput system to mitigate the "Thundering Herd" problem and resource exhaustion in distributed environments. This project implements a **Closed-Loop Control System** (relying on TCP-style congestion control) to throttle workloads based on real-time telemetry dynamically.

#### **System Architecture**

The orchestrator treats concurrency as a dynamic variable, adjusting the admission gate based on a continuous feedback loop of system health and execution latency.

```mermaid
graph LR
    subgraph "Ingress Layer"
        A[Workload Queue] --> B{Admission Controller}
    end

    subgraph "Adaptive Control Loop"
        B --> C[Worker Pool]
        C --> D[Execution Latency / Success Rate]
        D --> E[Congestion Controller]
        F[Prometheus / System Metrics] --> E
        E -->|Dynamic Concurrency Limit| B
    end

    subgraph "Sinks"
        C --> G[External APIs / DB]
    end

    style E fill:#2a60ff,stroke:#fff,stroke-width:2px,color:#fff
    style B fill:#f96,stroke:#333,stroke-width:2px
```
---
## 📂 Featured Systems

### [sovereign-vpc](https://github.com/Drecoder/sovereign-vpc)
A Google Cloud Platform (GCP) networking foundation built with HCL (Terraform) that implements Zero-Trust principles and Sovereignty-as-Code. It features a modular VPC architecture with Hub-and-Spoke peering and automated compliance controls.  
`HCL` · `Terraform` · `GCP` · `Zero-Trust`

### [data-net-vpc](https://github.com/Drecoder/data-net-vpc)
An observability-focused networking project demonstrating advanced VPC architecture in GCP. It integrates automated CI/CD pipelines with Checkov security scans to maintain a security-first posture.  
`HCL` · `Terraform` · `GCP` · `Checkov` · `CI/CD`

### [Adaptive-Concurrency-Orchestrator](https://github.com/Drecoder/Adaptive-Concurrency-Orchestrator)
A Node.js-based Proof of Work (PoW) for an adaptive concurrency controller that functions as an infrastructure shield for Headless WordPress & Next.js stacks. It utilizes Gradient-Based Orchestration for intelligent traffic management.  
`Node.js` · `Redis` · `Nginx` · `JavaScript`

### [HOTEL](https://github.com/Drecoder/HOTEL)
An event-driven Hotel Operations (HotelOps) platform utilizing a NestJS + GraphQL backend and a React (Vite) frontend. It features a scalable microservices-ready architecture, using Kafka for message brokering and event streaming.  
`NestJS` · `GraphQL` · `React` · `Kafka` · `TypeScript`

### [cyber](https://github.com/Drecoder/cyber)
A multi-service full-stack demonstration showcasing a Go backend and React frontend integrated with a robust observability stack. It features Prometheus, Grafana, and OpenTelemetry for advanced metrics collection and distributed tracing.  
`Go` · `React` · `OpenTelemetry` · `Prometheus` · `Grafana`

### [Engineering_Excellence_Playbook](https://github.com/Drecoder/Engineering_Excellence_Playbook)
A comprehensive Consultant-First Engineering Playbook and operational framework. It codifies repeatable standards for Frontend, Backend, and Infrastructure with a focus on Async Flows, Observability, and Platform Governance.  
`Markdown` · `ADRs` · `GitHub Actions` · `Documentation`

---

## 🧠 Engineering Philosophy

- Observability-first design: systems must be measurable to be operable
- Failure-aware architecture: systems should degrade gracefully under load
- Infrastructure as code mindset: everything is version-controlled and automated
- Signal-driven operations: decisions should be based on telemetry, not assumptions


