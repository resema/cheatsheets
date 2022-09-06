# Orchestrator <!-- omit in toc -->
## Table of Contents <!-- omit in toc -->
- [1. Introduction](#1-introduction)

# 1. Introduction

---
---

# 2. Analysis
## 2.1. Google Solution for ATM

### 2.1.1. Lessons Learned
- signed URL are not *that* save
- request ID from server to upload it in their bucket
  - allows all debugging
  - client has to keep ID as long as he need it
- ***Sidenote ONLY***: Use service accounts for all computation services
  - do not use passing JWT tokens
    - compromised service could allow attacker to use other services
  - service accounts are 1-to-1 mapping

### 2.1.2. Technical Design Document (TDD)
- link: https://docs.google.com/document/d/1DwU8djdHaVAeO_jxNWhejRVov5Q8rb83Ouac7HhzGOY/edit#**

---
## 2.2. Use Cases
### 2.2.1. CAM Production Item Service (PIS)

### 2.2.2. Tooth Morphology
- backend service want the callers to know of each others
  - [x] What should they know from each other
    - antagonisten
    - neighbors
    - contacts
    - stepwise computation
    - **create new restoration (new second crown)**
    - crowns as neighbors will be calculated differently as two crowns not as neighbors
  - [x] Context passing
    - https://wiki.dentsplysirona.com/pages/viewpage.action?pageId=48439111
    - every service has its own context (serialised)
- orchestration of services
  - [x] services contain internally a DAG
  - [x] use of google workflow possible
    - [x] composer?
- [x] biofit manager could retrigger part of DAG based on input context
  - abstraction level is changing the output quality & performance
  - `computation-strategy` could be an approach
  - https://wiki.dentsplysirona.com/display/ONCTMA/Architecture+overview
- [x] User interaction: when where how?
  - callbacks in Google Workflow?
- [x] Need for `tasksched` and `subproc` or `Google workflow`?
  - Moloch: stakeholder of corelib or direct
- [x] second solution for China in case of composer
  - abstractions layer for Google Workflow
- [x] optimization of computation
  - Context contains intermediate data
    - Graph node will be excluded
    - [x] where to store?
      - [x] binary blob for caller
      - [x] passes location for storage context or ID for storage
        - service would need some cached context
          - [x] Redis?

## Workflow
- postpone/wait for somebody call callback
- no grpc -> authentication with token or pub/sub
- Workflow has conditional steps
  - pass a pipeline as argument to another graph
- Google Composer -> take a look

- AliCloud -> Serverless Workflow

---
---
# 3. Open Questions
- [ ] How is it related to other treatments?
- [ ] What are the possible use cases for merging of procedures?
- [ ] What is the CAM solution?
  - [ ] Does this fit for other use cases?
- [ ] What is the core concept of workflows
  - [ ] Is it extendable to this use case?
- [ ] What's Vertex AI? -> Will most probably not fit here.

# 4. Architectural Tasks
- [ ] Stakeholder meeting, gather use cases
- [ ] Architectural meeting
- [ ] Draft
  - [ ] Diagrams
  - [ ] Requirements