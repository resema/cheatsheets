# cheatsheets<!-- omit in toc -->
My second brain, to help me remember stuff

# Glossary <!-- omit in toc -->
- [A](#a)
- [B](#b)
- [C](#c)
- [D](#d)
- [G](#g)
- [L](#l)
- [K](#k)
- [M](#m)
- [O](#o)
- [P](#p)
- [Q](#q)
- [R](#r)
- [S](#s)
- [T](#t)
- [V](#v)
- [W](#w)
- [Y](#y)

# Topics <!-- omit in toc -->
## DP&S <!-- omit in toc -->
### Architecture <!-- omit in toc -->
- [Notes](/architectural-notes.md)
- [iSAQB](cpsa-f.md)


### Lightning Procedure Enablement <!-- omit in toc -->
- [Technical Reviews](/procedure-enablement.md)
- [Overview](proc-notif-apps.md)

### Cheats <!-- omit in toc -->
- [Cloud infrastructure](/cloud-infrastructure.md)
- [GCP, k8s, Istio](/gcp-k8s-istio.md)
- [Git](git.md)
- [Flutter](flutter.md)

---
---
# A
- **Abstraction**: Design principle for handling complexity, see <!-- omit in toc -->
  - [Concepts [1]](/cpsa-f.md#26-design-principles-r1-r3) <!-- omit in toc -->

---
- **Authenthication**: Authenticate your user, see <!-- omit in toc -->
  - [gcloud [1]](/gcp-k8s-istio.md#11-cheats)
  - [Overview [2]](/security.md#2-terminology)
  
---
- **Authorization**: Process of allowing an authenticated user to access his resources by checking whether the user has access rights to the system.
  - [Definition [1]](/security.md#2-terminology) <!-- omit in toc -->
---
---
# B
- **Box**: Black, grey and white boxes; possible concepts to look at software components/building blocks, see
  - [Task & Responsibilities [1]](/cpsa-f.md#14-software-architects-tasks-and-responsibilities-r1)
  - [Design [2]](/cpsa-f.md#22-design-software-architectures-r1)

---
- **building blocks**: unit of software architecture, see
  - [Key terms [1]](/cpsa-f.md#11-definitions-of-software-architecture-r1)
  - [Tasks & Responsibilities [2]](/cpsa-f.md#14-software-architects-tasks-and-responsibilities-r1)
  - [Design & Development [3]](/cpsa-f.md#21-approaches-and-heuristics-for-architecture-development-r1-r3)

---
---
# C
- **Conceptional integrity**: Design principle for similar tasks are handle in similar manner, including KISS and YAGNI, see <!-- omit in toc -->
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats) <!-- omit in toc -->
---
- **Cross-cutting concepts**: Concepts which span over multiple areas, see
  - [cross-cutting concepts [1]](/cpsa-f.md#24-cross-cutting-concepts-r1)
  - [document cross-cutting concepts [2]](/cpsa-f.md#36-document-cross-cutting-concepts-r2)
- **Cluster**: Collection of services within in a specific topic, zone, region, others, see
  - [gcloud container clusters list [1]](/gcp-k8s-istio.md#11-cheats)<!-- omit in toc -->
---
- **curl**: Ping url, see
  - [Tools [1]](/gcp-k8s-istio.md#41-curl)

---
---
# D
- **Design Principles**: F.ex. abstraction, modularization, conceptual integrity, simplicity, expect errors
  - [Concepts [1]](/cpsa-f.md#26-design-principles-r1-r3) <!-- omit in toc -->
---
- **Docker**: Container platform, see
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats) <!-- omit in toc -->
---
- **DRY**: Design principle for introducing abstractions, see
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats) <!-- omit in toc -->

---
---
# G
- **GCP**: Google Cloud Project, see
  - [cheats [1]](/gcp-k8s-istio.md#11-cheats) <!-- omit in toc -->
---
- **git-crypt**: lock/unlock repositories, see
  - [cheats [1]](/git.md#2-gpg--git-crypt) <!-- omit in toc -->
---
- **gpg**: create private/public keys, see
  - [cheats [1]](/git.md#2-gpg--git-crypt) <!-- omit in toc -->
---
- **grpcurl**: like curl but with grpc payload, see
  - [Tools [1]](/gcp-k8s-istio.md#42-grpcurl)

---
---
# L
- **Long Running Operations**: defines a standard interface to work with Long Running Operations so the client can use it to track the progress and receive the result
  - [Description [1]](/gcp-k8s-istio.md#129-long-running-operations)  <!-- omit in toc -->

---
---
# K
- **k9s**: Tool to interact with Istio, Kubernetes, Configmaps, Secrets, Services, Pods and much more, see
  - [Tools [1]](/gcp-k8s-istio.md#431-cheats) <!-- omit in toc -->
---
- **KISS**: *Keep it simple, stupid* - Design principle for similar tasks are handle in similar manner (part of conceptional integrity), see <!-- omit in toc -->
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats)  <!-- omit in toc -->
---
- **kustomize**: Tool to handle manifests, see
  - [Tools [1]](/cloud-infrastructure.md#2-kustomize)

---
---
# M
- **Managed Instance Group**: a collection of Virtual Machine (VM) instances that can be managed as a single entity
  - [Definition [1]](/gcp-k8s-istio.md#127-managed-instance-group-mig)  <!-- omit in toc -->
---
- **Modularization**: Design principle for information hiding and encapsulation; contains SOC, SOLID, see <!-- omit in toc -->
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats)  <!-- omit in toc -->
---
# O
- **OAuth**: not an API or a service: it’s an open standard for authorization and anyone can implement it
  - [Definition](/security.md#11-comparison-of-oauth2-and-jwt)

---
---
# P
- **Patterns**: F.ex. layers, pipe-and-filters, microservices, dependency injection
  - [Concepts [1]](/cpsa-f.md#25-patterns-r1-r3) <!-- omit in toc -->
---
- **PEM**: Privacy Enhanced Mail is a Base64 encoded DER certificate.  PEM certificates are frequently used for web servers as they can easily be translated into readable data using a simple text editor.

---
---
# Q
- **Quality models and characteristics**: such as configurability, reliability, memory requirements, performance efficiency, securit, usability, runtime flexibility or maintainability, see
  - [Examples [1]](/cpsa-f.md#41-quality-models-and-quality-characteristics-r1)

---
---
# R
- **Cloud Run**: basically a managed GKE
  - [Description [1] ](/gcp-k8s-istio.md#126-cloud-run)  <!-- omit in toc -->

---
---
# S
- **Service Account**: special types of accounts used by applications and services
  - [Description [1]](/security.md) <!-- omit in toc -->
---
- **SLA**: service level agreement; the agreement made with clients or users <!-- omit in toc -->
---
- **SLI**: service level indicator; the real number on performance <!-- omit in toc -->
---
- **SLO**: service level objective; the objectives the team must hit to meet the agreement. <!-- omit in toc -->
---
- **Separation of concerns (SoC)**: Design principle for destructing a problem into sub-problems, see <!-- omit in toc -->
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats)  <!-- omit in toc -->
---
- **SOLID**: Design principle for single reponsibility principle, open-closed principle, Liskov substitution principle, interface segregation principle and dependency inversion principle, see <!-- omit in toc -->
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats)  <!-- omit in toc -->
---
- **Submodule**: child repository in parent repository, see 
  - [Cheats [1]](/git.md#112-submodule)
  - [Cheats [2]](/git.md#113-update-with-originmain)
  - [Cheats [3]](/git.md#114-update-submodule-in-another-repo)

---
---
# T
- **Terraform**: Infrastructure-as-Code (IAC) Tool, see
  - [IAC [1]](/cloud-infrastructure.md#11-cheats) <!-- omit in toc -->
---
---
# V
- **Views**: Different abstraction levels for SW architecture (arc42), see
  - [Key terms [1]](/cpsa-f.md#11-definitions-of-software-architecture-r1)
  - [Task & Reponsibilities [2]](/cpsa-f.md#14-software-architects-tasks-and-responsibilities-r1)
  - [Design & Development [3]](/cpsa-f.md#21-approaches-and-heuristics-for-architecture-development-r1-r3)
  - [Design [4]](/cpsa-f.md#22-design-software-architectures-r1)
  - [Concepts [5]](/cpsa-f.md#34-architectural-views-r1)

---
---
# W
- **Workflow**: is Google Cloud’s managed orchestration platform that executes services in an order that is defined as a workflow
  - [Description [1]](/gcp-k8s-istio.md#128-workflow) <!-- omit in toc -->

---
---
# Y
- **YAGNI**: *You Ain't Gonna Need It* - Design principle for similar tasks are handle in similar manner (part of conceptional integrity), see <!-- omit in toc -->
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats) <!-- omit in toc -->
---
- **YAML**: Yet another markdown language; used for manifest, Google Workflow and others, see
  - [Example Kubernetes [1]](/gcp-k8s-istio.md#124-resource-management-for-pods-and-containers)
