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

### Structure
- LRO Facade
- Orchestrator
- Executor

---
## Use Cases
### CAM Production Item Service (PIS)

### Tooth Morphology

---
---
# 3. Open Questions
- [ ] How is it related to other treatments?
- [ ] What are the possible use cases for merging of procedures?
- [ ] What is the CAM solution?
  - [ ] Does this fit for other use cases?
- [ ] What is the core concept of workflows
  - [ ] Is it extendable to this use case?

# 4. Architectural Tasks
- [ ] Stakeholder meeting, gather use cases
- [ ] Architectural meeting
- [ ] Draft
  - [ ] Diagrams
  - [ ] Requirements