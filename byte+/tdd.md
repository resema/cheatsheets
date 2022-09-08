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
  - [Hybrid Model?](#hybrid-model)


# 1. High-Level Architecture
## 1.1. Context View
![context view](../diags/byte+/context-view.drawio.svg)

--- 
## Building Block View
![context view](../diags/byte+/building-block-view.drawio.svg)

### Questions
- [ ] What is stored in the `Storage Queue`?
  - `*.daproj`, `zip`'s, others?

---
---
# 2. Technology Stack
- [x] React (Smartphone app)
- [x] GraphQL (DB Protocol)
  - [x] Apollo client (state management library: client side and server side)
- [x] Azure Event Grid (Messaging)
  - `Patient DB` stores all messages
  - [ ] `Storage Queue` is part of this pattern?
- [ ] NoSQL COSMOS
  - DBs behind the scene
- [x] Salesforce
  - states (treatment states)
  - customer journey managed by it
  - lightning component framework
    - JavaScript based App building framework
    - No-code App builder included
- [x] NexHealth (connection to PMS)
  - Only US
  - [ ] Partnership in discussion
- [x] Shopify
  - no billing, but payment
- [x] Contentful (compose) in future
  - Shall replace the Salesforce Lightning App


<!-- # 3. Architecture Components -->

---
---

# Questions
## General
- [ ] Can you provide me access to BitBucket
  - Difficult, since they don't have access to our monorepos
  - And don't really want to give it to me...
- [ ] Is there the `Azure API Management` system used?
- [x] Must the `customers` and `patient` be keep synchronised in any way?
  - Future concept
  - Today it exists `customer` and `lead`
    - somebody who has ordered an impression kit (IK) is a `lead`
    - somebody with a treatment plan is a `customer`

---

## Data Models
- [ ] Is the data (patient data, images, project files, zips, others) stored in the `storage queue` or in the `patient DB`?
- [ ] What format is used for meshes?
- [ ] How is the rendering solved aka. which library is used?
- [ ] Structure of the patient data - is there a data model or specification?

---
  
## Messaging
- [ ] Message types & their descriptions - is there a specification, or links to code?
- [x] Is there something special about how GraphQL and Event Grid is connected?
  - [ ] Is here Apollo Client used?

---

## Hybrid Model?
![Hybrid Model](../diags/byte+/cv-byte%2B.drawio.svg)