# cheatsheets<!-- omit in toc -->
My second brain, to help me remember stuff

# Glossary <!-- omit in toc -->
- [A](#a)
  - [- [Definition [1]](/security.md#2-terminology)](#--definition-1)
- [B](#b)
- [C](#c)
- [D](#d)
- [G](#g)
- [K](#k)
- [M](#m)
- [O](#o)
- [P](#p)
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
- [Education](cpsa-f.md)
- [Q3 - Orchestrator](orchestrator.md)

### Byte+ <!-- omit in toc -->
- [notes](/byte%2B.md)

### Lightning Procedure Enablement <!-- omit in toc -->
- [Technical Reviews](/procedure-enablement.md)
- [Overview](proc-notif-apps.md)

### Cheats <!-- omit in toc -->
- [Cloud infrastructure](/cloud-infrastructure.md)
- [GCP, k8s, Istio](/gcp-k8s-istio.md)
- [Git](git.md)

---
---
# A
- **Authenthication**: Authenticate your user, see
  - [gcloud [1]](/gcp-k8s-istio.md#11-cheats)
  - [Overview [2]](/security.md#2-terminology)
  
---
- **Authorization**: Process of allowing an authenticated user to access his resources by checking whether the user has access rights to the system.
  - [Definition [1]](/security.md#2-terminology)
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
- **Cluster**:: Collection of services within in a specific topic, zone, region, others, see
  - [gcloud container clusters list [1]](/gcp-k8s-istio.md#11-cheats)<!-- omit in toc -->
---
- **curl**: Ping url, see
  - [Tools [1]](/gcp-k8s-istio.md#41-curl)

---
---
# D
- **Docker**: Container platform, see
  - [Cheats [1]](/cloud-infrastructure.md#31-cheats)

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
# K
- **k9s**: Tool to interact with Istio, Kubernetes, Configmaps, Secrets, Services, Pods and much more, see
  - [Tools [1]](/gcp-k8s-istio.md#431-cheats) <!-- omit in toc -->
---
- **kustomize**: Tool to handle manifests, see
  - [Tools [1]](/cloud-infrastructure.md#2-kustomize)

---
---
# M
- **Managed Instance Group**: a collection of Virtual Machine (VM) instances that can be managed as a single entity
  - [Definition](/gcp-k8s-istio.md#127-managed-instance-group-mig)

---
---
# O
- **OAuth**: not an API or a service: it’s an open standard for authorization and anyone can implement it
  - [Definition](/security.md#11-comparison-of-oauth2-and-jwt)

---
---
# P
- **PEM**: Privacy Enhanced Mail is a Base64 encoded DER certificate.  PEM certificates are frequently used for web servers as they can easily be translated into readable data using a simple text editor.

---
---
# R
- **Cloud Run**: basically a managed GKE
  - [Description](/gcp-k8s-istio.md#126-cloud-run)

---
---
# S
- **Service Account**:special types of accounts used by applications and services
  - [description [1]](/security.md)
- **Submodule**: child repository in parent repository, see 
  - [cheats [1]](/git.md#112-submodule)
  - [cheats [2]](/git.md#113-update-with-originmain)
  - [cheats [3]](/git.md#114-update-submodule-in-another-repo)

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

---
---
# W
- **Workflow**: is Google Cloud’s managed orchestration platform that executes services in an order that is defined as a workflow
  - [Description](/gcp-k8s-istio.md#128-workflow)

---
---
# Y
- **YAML**: Yet another markdown language; used for manifest, Google Workflow and others, see
  - [Example Kubernetes [1]](/gcp-k8s-istio.md#124-resource-management-for-pods-and-containers)
