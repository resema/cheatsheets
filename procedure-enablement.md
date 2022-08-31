# Procedure Enablement <!-- omit in toc -->
## Table of Contents <!-- omit in toc -->
- [1. Introduction](#1-introduction)
  
# 1. Introduction

---
# 2. Technical Reviews
## 2.1. Order Form
- [x] LigPen-1377 - Integrate Order Form with Suresmile Backend
  - Working, Bug on Suresmile side
- [x] LigPen-1353 - Enabling outcome simulation integration
  - use `prefillOrderData` & `OrderDefinitions`
- [x] LigPen-1455: Add Mapping for Teeth Status in Start Order API
  - `prefillOrderData` single method for Outsim
- [x] LigPen-1459 cleanup order form
  - `OrderDefinitions` optional content to be filled by Outsim
- [x] LigPen-1456 DS World Demo: Design Order
  - mocked data for payment and taxes


---
## 2.2. Procedures/Steps
- [x] LigPen-1313 - Provide Steps in Breadcrumbs to Procedures
  - already discussed <!-- TODO: rensem -->

---
## 2.3. Zuora
- [x] LigPen-1065 - Download Invoice using data stream
  - just streaming, nothing fancy

---
## 2.4. Development
- [x] LigPen-1463 Feature Flags
  - Current concept using IaC
    - terraform apply and restart (kill) pod (*instead* of using k8s manifests)