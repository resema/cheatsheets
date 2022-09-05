# Localization <!-- omit in toc -->
- [1. Overview](#1-overview)
  - [1.1. Figma](#11-figma)
  - [1.2. Lokalise](#12-lokalise)
  - [1.3. Bitbucket](#13-bitbucket)
  - [1.4. Current Situation](#14-current-situation)
  - [1.5. Vision of Future](#15-vision-of-future)
- [2. Versioning](#2-versioning)
  - [2.1. Versioning Schemes](#21-versioning-schemes)
  - [2.2. Build Artifact Versioning](#22-build-artifact-versioning)
  - [2.3. Multi vs Single-Domain Repo](#23-multi-vs-single-domain-repo)
- [3. Discussions](#3-discussions)

# 1. Overview
Mentioned topics are **Figma**, **Lokalise** and **Bitbucket**.
Also the ISO 17100:2015(s) has been mentioned here.

## 1.1. Figma
- [ ] is a design tool?

---

## 1.2. Lokalise
- [ ] helps to coordinate translations?

---

## 1.3. Bitbucket
- [ ] lists all missing translations?

---

## 1.4. Current Situation
- Dev enters key and english text to the `app_de.arb`
- Trigger make target to build all necessary files
- Invite a translator to formulate other langugages
- Dev has to merge those changes to his branch
- Generator `DSAppLocalizations` uses per default 'en'

---

## 1.5. Vision of Future
- Dev/Figma enters key in Localize
- Lokalize generates `arb` and other files 
- Dev has to rebase with PR from Tool

---
---
# 2. Versioning
## 2.1. Versioning Schemes
Our versioning approach differentiates between three schemes for versioning:

- Build artifact versioning, including
  - Microservices
  - Frontends
  - Shared libraries and other distribution packages
- Microservice API versioning
- Software product versioning

## 2.2. Build Artifact Versioning
Any build artifact is versioned using a `MAJOR.MINOR.PATCH` semantic scheme.


## 2.3. Multi vs Single-Domain Repo
1. Single domain flutter apps are developed within the monorepo of the respective domain
2. Flutter apps with contributions from multiple domains are developed within the repository of the domain which is responsible for the main part of the app. Packages for the app from other domains are developed in that same repo. (I.e. we are choosing the Single-app monorepo approach from above)
3. We will have repositories with shared libraries which are used by several separate flutter apps. A current example for this is the Core UI widget library. These libraries are each maintained in a separate repository.

---
---
# 3. Discussions
### Florian Sobirey, Sept. 05 <!-- omit in toc -->
- pro product -> 1x Figma/Localize project
  - f.ex. UI for assistents and UI for service technician
- Redesign could lead to reuse of existing keys
- Version push to Bitbucket
  - [ ] keep same version possible with figma, localize and bitbucket?
- [ ] Naming convention for keys
  - [ ] prod_topic_frame_key

### Simon Egg, Sept. 05 <!-- omit in toc -->
- ![simplified graphic](/out/diags/l10n/simplification/simplification.svg)