# Cheetsheet for CPSA-F <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. Basic Concepts](#1-basic-concepts)
  - [1.1. Definitions of software architecture (R1)](#11-definitions-of-software-architecture-r1)
    - [1.1.1 Key Terms](#111-key-terms)
  - [1.2. Goals and benefits of software architecture (R1)](#12-goals-and-benefits-of-software-architecture-r1)
  - [1.3 Software architecture in the software lifecycle (R2)](#13-software-architecture-in-the-software-lifecycle-r2)
    - [Software lifecycle (SLC)](#software-lifecycle-slc)
  - [1.4 Software architects' tasks and responsibilities (R1)](#14-software-architects-tasks-and-responsibilities-r1)
    - [Explanation](#explanation)
---
---
# 1. Basic Concepts
## 1.1. Definitions of software architecture (R1)
*Software architecture: the fundamental organization of a system embodied in its component, their relationships to each other and to the environment, and the principles guiding its design and evolution.*
### 1.1.1 Key Terms
- **Fundamental organization**: ordering and given designated place
- **Components (aka Building Blocks)**: strutctural elements: subsystems, modules, classes, functions
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
    - *conceptual integrity* means the design/architecture follows a consistent set of rules or decisions
      - necessary prerequiste for understandability and maintainability
- systematically **reduce complexity**
  - constructed in a way to facilitate development and maintenance
- specifiy **architectural relevant guidelines** for implementation and operation
  
---
## 1.3 Software architecture in the software lifecycle (R2)
SW architects can:
- **identify the consequences** of changes in requirements (functional, quality), technologies or the system environment in relation to software architecture
- **elaborate on relationships** between IT-systems and the supported business and operational processes

### Software lifecycle (SLC)
- describes all phases of a software product (planning, dev, use & retirement)
  - initial development:
    - designed and implemented from scratch
    - ADs are based on **initial requirements** and **influencing factors**
    - architecture established at this stage will have a **significat impact** on future evolution
  - evolution:
    - iterative changes that originat ein changing requirements, evolving technologies and lessons learned
  - servicing:
    - no turning back and it is considered legacy
    - changes are difficult and expensive
    - leaving most of underlying architectural problems **untouched**
  - phaseout:
    - no more changes to the software
  - closedown:
    - marks the **final end** of the line for a particular version of software
    - data migration still needed to be considered

---
## 1.4 Software architects' tasks and responsibilities (R1)
*Software architects are responsible for achieving the required or necessary quality and creating the architecture design for a solution.*
- **clarify and scrutinize requirements and constraints**, and refine them if necessary (functional & quality (non-functional) requirements)
- **decide how to decompose the system** into building blocks, while determining dependencies and interfaces
- **determine and decide on cross-cutting concepts**
- **communicate and document the software architecture** based on views, architectural patterns, cross-cutting and technical concepts
- **accompany the realization and implementation** of the architecture, integrate feedback, an ensure the consistency of src code
- **analyze and evaluate SW architecture** with respect to risks involving quality requirements
- **identify, highlight, and justify the consequences of ADs** to other stakeholders
  
### Explanation
- no algorithmic approach; iteration to the rescue
  - architecture needs feedback, therefore architecture work is inherently iterative

Software architects design and construct:
- building bloks
- interfaces between building blocks
- cooperation of building blocks
- cross-cutting concepts or rules
- selection of appropriate technologies
- adoption of suitable development and operation processes
  
Software architects need to fulfill 6 important tasks:
1. clarify requirements
   - who are the stakeholders?
   - context and external interfaces
   - quality requirements
   - functional requirements
     - frequent execution
     - most important for stakeholders
     - critical timing or performance constraints
     - CRUD large amounts of data
     - critical parts of infrastructure
   - constraints
   - stability, validity, and importance of all previous points
2. design cross-cutting concepts
   - designing belongs to the primary tasks
   - concepts from the basis for conceptual integrity
   - important contribution to achieve the intrinsic qualities of system
   - cannot be handled by individual building blocks
3. design structures
   - designing belongs to the primary tasks
   - structures are subsystems, components, packages, name spaces or classes
   - in both white box and black box manifestations
4. communicate architecture
5. shepherd implementations
   - identify parts that violate or endanger consistency or deviate from chosen architecture
   - identify potential design or implementation decisions which could improve overall architecture
6. evaluate architecture
   - find out if the system can fulfill or satisfy its quality requirments
   - in this context we mean *product quality*
     1. how well it complies with or conforms to a given design
        - how it compares to competitors
     2. **how it meets non-functional requirements that support the delivery of functional requirements**
        - qualitative evaluation
        - quantitative evaluation