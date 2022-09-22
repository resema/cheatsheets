# Cheetsheet for CPSA-F <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [3. Specification and communication of software architectures](#3-specification-and-communication-of-software-architectures)
  - [3.1. Quality requirements for technical documentation (R1)](#31-quality-requirements-for-technical-documentation-r1)
  - [3.2. Describe and communicate software architectures (R1, R3)](#32-describe-and-communicate-software-architectures-r1-r3)
  - [3.3. Models and notations to describe (R2-R3)](#33-models-and-notations-to-describe-r2-r3)
  - [3.4. Architectural views (R1)](#34-architectural-views-r1)
  - [3.5. Context view (R1)](#35-context-view-r1)
  - [3.6. Document cross-cutting concepts (R2)](#36-document-cross-cutting-concepts-r2)
  - [3.7. Describe interfaces (R1)](#37-describe-interfaces-r1)
  - [3.8. Document architectural decisions (R1-R2)](#38-document-architectural-decisions-r1-r2)
  - [3.9. Documentation as written communication (R2)](#39-documentation-as-written-communication-r2)
  - [3.10. Resources and tools for documentation (R3)](#310-resources-and-tools-for-documentation-r3)
---
---

# 3. Specification and communication of software architectures
## 3.1. Quality requirements for technical documentation (R1)

> Software architects know the quality requirements of technical documentation and can consider and fulfil those when documenting systems:
> - **understandability**, **correctness**, **efficiency**, **appropriateness** and **maintainability**
> - **form**, **content** and **level of detail** tailored to the stakeholders

> Software architects know that only the target audiences can assess the understandability of technical documentation.

### Documentation requirement 1: Correct <!-- omit in toc -->
- incorrect information in technical documentation can be as bad as bugs
- correctness is the highest goal

### Documentation requirement 2: Current <!-- omit in toc -->
- documentation must be current

### Documentation requirement 3: Helpful <!-- omit in toc -->
- has to help all readers to perform their concrete task
- should ease of facilitate their work

### Documentation requirement 4: Easy to change <!-- omit in toc -->
- documentation must be easy to change, as implementation changes
- if costly or difficult to change, it will not be updated

### Documentation requirement 5: Easy to understand <!-- omit in toc -->
- fulfill their expectations: language, notation, form and tooling
- invest adequate effort to ensure understandability e.g. through reviews and incorporating reader feedback

### Documentation requirement 6: Ease to find <!-- omit in toc -->
- be able to find information easily and quickly
- fixed structures or template and convention help with that

### Documentation requirement 7: Adequate <!-- omit in toc -->
- stakeholders of system may have special requirements and wishes

---
## 3.2. Describe and communicate software architectures (R1, R3)

> Software architect are able to:
> - **documented and communicate architectures for corresponding stakeholders**, thereby addressing different target groups, e.g. management, development teams, QA, other architects, and additional stakeholders
> - **consolidate and harmonize the style and content of contributions** from differnet groups of authors
> - know the **benefits of template-based documentation**

> They know that various properties of documentation depend on specifics of the system, its requirements, risks, development process, organization or other factors.
> These factors have an impact:
> - whether **written** or **verbal communication** should be prioritized
> - **amount of level of detail** of documentation needed at each stage of development
> - **documentation format**
> - **accessibility to the documentation**
> - **formality of documentation**
> - **formal reviews and sign-off process** for documentation

> They are aware of these factors and can adjust the documentation characteristics according to the situation.

### Value of architecture documentation <!-- omit in toc -->
aspects that are not contained or not well-covered in source code:
  - **overall structure**
  - **architecture decisions**
  - **reasons** for decisions
  - technology **choices**
  - **cross-cutting** concepts

### Stakeholder-specific documentation <!-- omit in toc -->
- different stakeholders or target groups can have different documentation requirements
- fulfill the needs of stakeholders:
  - format (wiki, single document, multiple documents)
  - style (text, diagram or a mixture)
  - structure
  - notation (e.g. UML)
  - depth
  - representation (paper or online)

### Benefits of templates <!-- omit in toc -->
- template provides a fixed **structure**
- provide following advantages:
  - **understandability** is improved
  - **retrievability** enables to find easily desired information
  - feasible to **re-use**
  - **lower effort to maintain**

### Documentation depends on many factors <!-- omit in toc -->
- documentation is a great example of **appropriateness**
- various aspects of documentation depend on specifics of a system, its requirement, risks, development, organization and other factors
- aspects include at least:
  - written or verbal communication
  - amount of documentation
  - formats and accessibility
  - formality of documentation
  - formal reviews and sign-offs

---
## 3.3. Models and notations to describe (R2-R3)

> Software architects know at least the following UML diagrams to describe architectural views:
> - **class**, **package**, **component** and composite-structure diagrams (R2)
> - **deployment** diagrams (R2)
> - **sequence and activity** diagrams (R2)
> - **state machine** diagrams (R3)

> Software architects know alternative notations to UML diagrams, f.ex.
> - ArchiMate
> - **flow charts**, **numbered lists** or **business-process-modeling-notation (BPMN)**

---
## 3.4. Architectural views (R1)

> Software architects are able to use the architectural views:
> - **context view**
> - **building block** or **component view** (composition of software building blocks)
> - **run-time view** (dynamic view, interaction between bblocks, state machine)
> - **deployment view** (hardware and technical infrastructure, as well as the mapping of bblocks onto the infrastructure)

---
## 3.5. Context view (R1)

> Software architects can:
> - **depict the context systems**, e.g. in the form of context diagrams
> - represent **external interfaces** of systems in context view
> - **differentiate between business and technical context**

---
## 3.6. Document cross-cutting concepts (R2)

> Software architects are able to adequately document and communicate typical cross-cutting concepts, e.g.
> - `persistence`
> - `workflow management`
> - `UI`
> - `deployment/integration`
> - `logging`

---
## 3.7. Describe interfaces (R1)

> Software architects are able to describe and specify both internal and external interfaces.

---
## 3.8. Document architectural decisions (R1-R2)

> Software architects are able to:
> - **systematically** take, justify, communicate, and document **architectural decisions**
> - identify, communicate and document the **interdependencies between design decisions**

> Software architects know about Architecture Decision Records (ADR) and can apply these to document decisions

---
## 3.9. Documentation as written communication (R2)
Software architects use documentation to support the **design**, **implementation** and **further development (maintenance/evolution)** of systems

---
## 3.10. Resources and tools for documentation (R3)

> Software architects know:
> - basics of several published frameworkds for the description of software architectures
>   - **ISO/IEEE-42010**
>   - **arc42**
>   - **C4**
>   - **FMC** (Wendt-FMC)
> - ideas and examples of checklists for the creation, documentation and testing of software architectures
> - possible tools for creating and maintaining architectural documentation