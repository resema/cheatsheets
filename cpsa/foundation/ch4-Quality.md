# Cheetsheet for CPSA-F <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [4. Software architecture and quality](#4-software-architecture-and-quality)
  - [4.1. Quality models and quality characteristics (R1)](#41-quality-models-and-quality-characteristics-r1)
  - [4.2. Clarify quality requirements (R1)](#42-clarify-quality-requirements-r1)
  - [4.3. Qualitative analysis (R2-R3)](#43-qualitative-analysis-r2-r3)
  - [4.4. Quantitative evaluation (R2)](#44-quantitative-evaluation-r2)
---
---

# 4. Software architecture and quality
## 4.1. Quality models and quality characteristics (R1)

> Software architects can explain:
> - **concept of quality** (DIN/ISO 25010) and **quality characteristics**
> - **generic quality models**
> - **correlation** and **trade-offs** of quality characteristics, f.ex.
>   - **configurability** versus **reliability**
>   - **memory requirements** versus **performance efficiency**
>   - **security** versus **usability**
>   - **runtime flexibility** versus **maintainability**

### **Quality** <!-- omit in toc -->
- more than a single property or attribute
- **needs to be specified or described**
- set of desired, required or given properties of a system

### Quality attributes <!-- omit in toc -->
- quality attributes == quality properties == quality characteristics
#### functional suitability <!-- omit in toc -->
  - correctness
  - appropriateness
  - completeness
#### reliability <!-- omit in toc -->
  - availability
  - fault tolerance
  - recoverability
  - maturity
#### performance efficiency <!-- omit in toc -->
  - time behavior
  - resource utilization
  - capacity
#### usability <!-- omit in toc -->
  - appropriateness
  - recognizability
  - learnability
  - operability
  - user error protection
  - UI asthetics
  - accessibility
#### security <!-- omit in toc -->
  - confidentality
  - integrity
  - non-reputation
  - accountability
  - authenticity
#### compatibility <!-- omit in toc -->
  - co-existence
  - interoperability
#### maintainability <!-- omit in toc -->
  - modularity
  - reusability
  - analyzability
  - modifiability
  - testability
#### portability <!-- omit in toc -->
  - adaptability
  - installatbility
  - replaceability

### **Quality model** <!-- omit in toc -->
- a **collection of attributes** a system might have or need to have
- **hierarchical** quality models **break down their top-level properties into finer grained properties** 

### ISO 25010 <!-- omit in toc -->
![ISO-25010](out/diags/cpsa-f/iso-25010/iso-25010.svg)

### Typical conflicts between quality requirements <!-- omit in toc -->
- robustness versus runtime flexibility
- memory requirements versus performance efficiency
- IT-security versus usability
- runtime performance versus understandability or simplicity

### Trade-offs or compromises between quality attributes <!-- omit in toc -->
- several quality attributes influence each other
- nealy every quality property requires more time and/or money to implement

---
## 4.2. Clarify quality requirements (R1)

> Software architects can
> - clarify and formulate **specific quality requirements**, f.ex. in the form of scenarios and quality trees
> - explain and apply **scenarios** and **quality trees**

### Quality scenarios <!-- omit in toc -->
- document and clarify the required quality attributes
- describe in pragmatic and informal manner aka. making the abstract term "quality" more concrete, specific and tangible
- three different types of scenarios
  1. **usage scenarios** describe how the system behaves in different cases in terms of runtime performance, memory consumption, throughput or similar
  2. **change scenarios** describe the situation that any component, its environment or its operational infrastructure changes or is being changed
  3. **failure scenarios** describe the situation that some part of the system, its infrastructure or neighbors fail

### Quality tree <!-- omit in toc -->
- On the root of this tree usually quality is kept.
- The top branches break quality down into several quality attributes and the attributes into sub-attributes.
- At the leaves you find scenarios.

---
## 4.3. Qualitative analysis (R2-R3)

> Software architects:
> - know **methodical approaches** for the qualitative analysis and assessment of software architectures (R2), f.ex. as specified by ATAM (R3)
> - can **qualitatively analyze and assess** smaller systems (R2)
> - know the following **sources of information** can help in the qualitative analysis and assessment of architectures (R2)
>   - quality requirements (quality trees and scenarios)
>   - architecture documentation
>   - architecture and design models
>   - source code
>   - metrics
>   - requirements, operational or test documentation

---
## 4.4. Quantitative evaluation (R2)

> Software architects know approaches for the quantitative analysis and evaluation
> - quantitative evaluation can help to **identify critical parts** within systems
> - further information
>   - **requirements and architectural documentation**
>   - source code and **related metrics** such as lines of of code, complexity, inbound and outbound dependencies
>   - **known errors** in source code, especially error clusters
> **test cases** and **test results**
