# Cheetsheet for CPSA-F <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. Basic Concepts](#1-basic-concepts)
  - [1.1. Definitions of software architecture (R1)](#11-definitions-of-software-architecture-r1)
    - [1.1.1 Key Terms](#111-key-terms)
  - [1.2. Goals and benefits of software architecture (R1)](#12-goals-and-benefits-of-software-architecture-r1)
  - [1.3 Software architectue in the software lifecycle (R2)](#13-software-architectue-in-the-software-lifecycle-r2)
---
---
# 1. Basic Concepts
## 1.1. Definitions of software architecture (R1)
*Software architecture: the fundamental organization of a system embodied in its component, their relationships to each other and to the environment, and the principles guiding its design and evolution.*
### 1.1.1 Key Terms
- **Fundamental organization**: ordering and given designated place
- **Components (aka Building Blocks)**: strutctural elements: subsystems, modules, classes functions
- **Relationships**: interfaces, dependencies, associations
- **Environment**: data, control flow, events are transferred to and from possible different kinds of neighbors (--> context view)
- **Principles (aka Concept)**: rule that holds for the whole system or several parts of it
- **Design and evolution**: cross-cutting and system-wide decisions might become necessary during both initial design and ongoing evolution and maintenance of systems

---
## 1.2. Goals and benefits of software architecture (R1)
Essential goals and benefits:
- support the **design, implementation, maintenance, and operation** of systems
- achieve **quality requirements** (reliability, maintainability, changeability, security, etc.)
- achieve **functional requirements** or ensure that they can be met
  - taking global decision decisions, spanning the context of several components
- ensure that the **system's structure and concepts are understood** by all relevant stakeholders
    - *conceptual integrity* means the design/architeture follows a consistent set of rules or decisions
      - necessary prerequiste for understandability and maintainability
- systematically **reduce complexity**
  - constructed in a way to facilitate development and maintenance
- specifiy **architectural relevant guidelines** for implementation and operation
  
---
## 1.3 Software architectue in the software lifecycle (R2)
SW architects can:
- **identify the consequences** of changes in requirements (functional, quality), technologies or the system environment in relation to software architecture
- **elaborate on relationships** between IT-systems and the supported business and operational processes