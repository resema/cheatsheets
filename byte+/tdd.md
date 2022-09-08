# Technical Design Description <!-- omit in toc -->
- [1. High-Level Architecture](#1-high-level-architecture)
  - [1.1. Context View](#11-context-view)
  - [Building Block View](#building-block-view)
    - [Questions](#questions)
- [2. Technology Stack](#2-technology-stack)
- [Questions](#questions-1)
  - [General](#general)
  - [Data Models](#data-models)
  - [Messaging](#messaging)


# 1. High-Level Architecture
## 1.1. Context View
![context view](../diags/byte+/context-view.drawio.svg)

--- 
## Building Block View
![context view](../diags/byte+/building-block-view.drawio.svg)

### Questions
- [ ] What stored in the `Storage Queue`?
  - `*.daproj`, `zip`'s, others?
- [ ] How is the **customer** different from the **patient**?
  - is a dentist a customer?

---
---

# 2. Technology Stack
- [ ] React (Smartphone app)
- [ ] GraphQL (DB Protocol)
- [ ] Apollo client (state management library: client side and server side)
- [ ] Azure Event Grid (Messaging)
- [ ] Salesforce
  - states (treatment states)
  - customer journey managed by it
  - lightning component framework
    - JavaScript based App building framework
    - No-code App builder included
- [ ] NexHealth (connection to PMS)
- [ ] Shopify
- [ ] NoSQL COSMOS
  - DB behind the scene


<!-- # 3. Architecture Components -->

---
---

# Questions
## General
- [ ] Can you provide me access to BitBucket
- [ ] Is there the `Azure API Management` system used?
- [ ] Must the `customers` and `patient` be keep synchronised in any way?

---

## Data Models
- [ ] Is the data (patient data, images, project files, zips, others) stored in the `storage queue` or in the `patient DB`?
- [ ] What format is used for meshes?
- [ ] How is the rendering solved aka. which library is used?
- [ ] Structure of the patient data - is there a data model or specification?

---
  
## Messaging
- [ ] Message types & their descriptions - is there a specification, or links to code?
- [ ] Is there something special about how GraphQL and Event Grid is connected?