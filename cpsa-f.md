# Cheetsheet for CPSA-F <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. Basic Concepts](#1-basic-concepts)
  - [1.1. Definitions of software architecture (R1)](#11-definitions-of-software-architecture-r1)
  - [1.2. Goals and benefits of software architecture (R1)](#12-goals-and-benefits-of-software-architecture-r1)
  - [1.3. Software architecture in the software lifecycle (R2)](#13-software-architecture-in-the-software-lifecycle-r2)
  - [1.4. Software architects' tasks and responsibilities (R1)](#14-software-architects-tasks-and-responsibilities-r1)
  - [1.5. Software architects and other stakeholders (R1)](#15-software-architects-and-other-stakeholders-r1)
  - [1.6. Development approach and software architecture (R1)](#16-development-approach-and-software-architecture-r1)
  - [1.7. Short- and long-term goals (R1)](#17-short--and-long-term-goals-r1)
  - [1.8. Explicit statement versus implicit assumptions](#18-explicit-statement-versus-implicit-assumptions)
  - [1.9. Responsibilities of SW architects in the greater architectural context (R3)](#19-responsibilities-of-sw-architects-in-the-greater-architectural-context-r3)
  - [1.10. Types of IT systems (R3)](#110-types-of-it-systems-r3)
  - [1.11. Challenges of distributed systems (R3)](#111-challenges-of-distributed-systems-r3)
---
---
# 1. Basic Concepts

## 1.1. Definitions of software architecture (R1)

*Software architecture: the fundamental organization of a system embodied in its component, their relationships to each other and to the environment, and the principles guiding its design and evolution.*
### 1.1.1 Key Terms <!-- omit in toc -->
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
## 1.3. Software architecture in the software lifecycle (R2)
SW architects can:
- **identify the consequences** of changes in requirements (functional, quality), technologies or the system environment in relation to software architecture
- **elaborate on relationships** between IT-systems and the supported business and operational processes

### Software lifecycle (SLC) <!-- omit in toc -->
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
## 1.4. Software architects' tasks and responsibilities (R1)

*Software architects are responsible for achieving the required or necessary quality and creating the architecture design for a solution.*
- **clarify and scrutinize requirements and constraints**, and refine them if necessary (functional & quality (non-functional) requirements)
- **decide how to decompose the system** into building blocks, while determining dependencies and interfaces
- **determine and decide on cross-cutting concepts**
- **communicate and document the software architecture** based on views, architectural patterns, cross-cutting and technical concepts
- **accompany the realization and implementation** of the architecture, integrate feedback, and ensure the consistency of src code
- **analyze and evaluate SW architecture** with respect to risks involving quality requirements
- **identify, highlight, and justify the consequences of ADs** to other stakeholders
  
### Explanation <!-- omit in toc -->
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
   - concepts form the basis for conceptual integrity
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

---
## 1.5. Software architects and other stakeholders (R1)

Software architects are able to explain their role. 

*Many problems in software development cannot be solved by good programming alone, but need communication between stakeholders.*

Software Architects will have at least the following four different categories of stakeholder:
1. **stakeholders with a business-, product- or domain focus**, e.g.PO, RE, business analyst.
   - communicate on requirements and/or their feasibility
     - clarify requirements
     - help identify conflicting requirements
     - support finding trade-offs between conflicting goals and requirements
     - explain the impact of requirements and constraints
     - support in prioritiying requirements and their development
2. **management stakeholders**, like PM or SM
   - communicate over organizational constraints, resources, schedules, etc.
     - technical consultancy
     - risk management
     - support in staffing
     - support in defining and sizing work packages
3. **technical stakeholders**, like SW devs, HW devs or IT operations
   - communicate on a detailed and specific technical level
     - communicate and explain AD
     - enable and prepare technical decisions
     - coach or help-to-coach
     - moderate in the discussion and design of interfaces
4. **stakeholders focused on specific quality attributes**, like IT security or QA

---
## 1.6. Development approach and software architecture (R1)

*Architecture work needs feedback, which is an inherent feature of iterative development approaches. Architects have to systematically optain feedback from other stakeholders.*

Benefits of iterative approach:
- early feedback
- early risk identification
- more time to fix problems
- better changes to adapt to changes in requirements, constraints, technology, team, etc.
- opportunities to practice every activity in dev process, especially deploy- and release-related

### Deming-Cycle or Plan-Do-Check-Adjust <!-- omit in toc -->
- **plan**: make architectural decisions to meet the known/given requirements
- **do**: exectue plan, implement decisions
- **check**: get feedback and evaluate
- **adjust**: improve or refine decisions

---
## 1.7. Short- and long-term goals (R1)

*Usually project goals tend to be more short-term, whereas architecture goals tend to be long-term.*

Short-term and long-term:
- projects (sprints) typically last for a couple of weeks up to one or two years
- systems often remains in use for several years.

---
## 1.8. Explicit statement versus implicit assumptions

*Very often things go wrong due to different people having different implicit assumptions about something. Software architects should be explicit in their decisions.*

Ensure explicitness in your work by:
- **explicitly documenting** quality requirements, e.g in form of quality scenarios
- **explicitly documenting** ADs
- **using clear and unambiguous terminology**, especially domain/business terminology
- **explicitly defining technical or cross-cutting concepts**
- **explicitly considering different perspectives**, f.ex. quality requirements, domain struture, interfaces, building blocks structure, technical infrastructure, etc.
- **explicitly devoloping cross-cutting concepts** to improve conceptual integrity (consistency)
- **explicitly analyzing and evaluating** your system, its architecture and code
- **explicitly asking stakeholders for feedback**

---
## 1.9. Responsibilities of SW architects in the greater architectural context (R3)

Software architects are familiear with other architectural domains, f.ex.:
- enterprise IT architecture
- business and process architecture
- information architecture
- infrastructure and process architecture
- hardware and processor architecture

---
## 1.10. Types of IT systems (R3)

Software architects know different types of IT systems, f.ex.:
- information systems
- decision support, data warehouse or business intelligence systems
- mobile systems
- batch processing or systems
- hardware-related systems

---
## 1.11. Challenges of distributed systems (R3)

Software architects are able to:
- identify distribution in a given SW architecture
- analyze consistency criteria for a given business problem
- explain the causality of events in a distributed system

Software architects know:
- communication may fail in a distributed system
- there are limitations regarding consistency in real-world databases
- what the "split-brain" problem is and why it is difficult
- that it is impossible to determine the temporal order of events in a distributed system