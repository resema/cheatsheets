# Orchestrator <!-- omit in toc -->
## Table of Contents <!-- omit in toc -->
- [1. Introduction](#1-introduction)

# 1. Introduction

---
---

# 2. Analysis
## 2.1. Google Solution

### 2.1.1. Lessons Learned
- signed URL are not *that* save
- request ID from server to upload it in their bucket
  - allows all debugging
  - client has to keep ID as long as he need it
- ***Sidenote ONLY***: Use service accounts for all computation services
  - do not use passing JWT tokens
    - compromised service could allow attacker to use other services
  - service accounts are 1-to-1 mapping

### 2.1.2. LRO Facade

### 2.1.3. Orchestrator

### 2.1.4. Executor

# 3. Open Questions
- [ ] How is it related to other treatments?
- [ ] What are the possible use cases for merging of procedures?
- [ ] What is the CAM solution?
  - [ ] Does this fit for other use cases?
- [ ] 

# 4. Architectural Tasks
- [ ] Stakeholder meeting, gather use cases