# Byte+ <!-- omit in toc -->
## Table of Contents <!-- omit in toc -->
- [1. Introduction](#1-introduction)
- [2. Open Questions](#2-open-questions)
  - [2.1. General Concept](#21-general-concept)
  - [2.2. Integration / Connection to DSCore](#22-integration--connection-to-dscore)
  - [2.3. Data Model](#23-data-model)
  - [2.4. Components for Byte+](#24-components-for-byte)
  - [2.5. Architectural Tasks](#25-architectural-tasks)
- [3. Glossary](#3-glossary)

# 1. Introduction
![Overview](img/byte+/overview.png)
- Boundaries: Byte+ integrates the dentist into the process
  - Dentist should approve the treatment in B+
  - B+ shall become part of a dentist clinic
  - Differences: App is corrently consumer oriented and driven
    - Shall be an alternativ to SureSmile
  - Take TeleHealth Model into the market of SureSmile
    - cheaper opportunity for the same topic
    - make SureSmile a better product by having a cheaper starting point for patients
  - Step into the field between Byte and SureSmile
- Treatment handling, such as Crone, Abutment and others are similar to B+
  - Shall be extended and harmonised to fulfill different usecases
- Landing page
  ![Byte](img/byte+/Byte-LandingPage.png)
- DSCore is **NOT** an PMS system
  - shall be included
  - do not make the impression, it is a little bit
- B+ want to be fast
  - Dentist approves treatment plan
  - Data goes to B+ team and then to the patient
  - Treatment plans could be synchronised with other treatments (abutment, suresmile, aligner, others)
  ![gallery](img/byte+/media-gallery.png)

---
---
# 2. Open Questions
## 2.1. General Concept
- [ ] Hybrid Model mentioned in Marketing Pages?
  - Integrate platform topics into existing application
- [ ] Definitions of ByteApp, Byte+ and Hybrid **Model**?
- [ ] Is the app mainly consumer driven and oriented
- [ ] Treatment handling is something B+ is a head of DSCore
  - Take a look at kanban-ish notification board for example
  

## 2.2. Integration / Connection to DSCore
- [ ] Landing page specific for B+ or not?
  - [ ] Activity Page on Dashboard would be a possible extension for DSCore
  - [ ] Notification Board could be elaborated as well in DSCore
  ![NotifBoard](img/byte+/Byte-NotificationBoard.png)
- [ ] Find a Dentist matching algorithm?
- [ ] NexHealth only US?
- [ ] Patient Account within DSCore?
- [ ] Billing/Subscription Integration?
- [ ] Treatment plan for Provider Account: is this a procedure?
- [ ] Email to customers from DSCore?

## 2.3. Data Model
- [ ] What data model is used for the meshes?
- [ ] How is data exchange between App/Byte and DSCore?
- [ ] How is the dataflow between customer &harr; dentist &harr; DSCore &harr; Byte+?

---
---
## 2.4. Components for Byte+
- [ ] Upload patient data, such as pictures of patient (aka "smile selfies") in a separate app/url?
- [ ] 3D model view for the customer?

---
---
## 2.5. Architectural Tasks
- [ ] Different views for the complete situation
- [ ] Find overlaps, similar patterns, similar workflows, data representation, and more
- [ ] Definition & description for treatment planning within DSCore
- [ ] Separate topics/issues into UX, services, workflow, data model and others
- [ ] Having a running instance of Byte

---
---
# 3. Glossary
- [ ] Account CTR / Act CTR: <!-- TODO -->
- [x] referrals := *Empfehlung*
- [x] Byte+ will be scanner-agnostic := <!-- TODO -->
- [ ] App is focused on handled the treatment by the customer
- [ ] Byte+ shall step into the gap between Byte and SureSmile
  