# Cheetsheet for Cloud Infrastructure <!-- omit in toc -->
- [1. Terraform](#1-terraform)
  - [1.1. Cheats](#11-cheats)
  - [1.2. Building Blocks](#12-building-blocks)
    - [1.2.1. Terraform Initial Settings](#121-terraform-initial-settings)
    - [1.2.2. Resources](#122-resources)
    - [1.2.3. Providers](#123-providers)
    - [1.2.4. Data Sources](#124-data-sources)
  - [1.3. Functional Programming Language](#13-functional-programming-language)
  - [1.4. Usage](#14-usage)
    - [1.4.1. Initilialization](#141-initilialization)
    - [1.4.2. Planning](#142-planning)
    - [1.4.3. Execution](#143-execution)
  - [1.5. Best Practices](#15-best-practices)
- [2. Kustomize](#2-kustomize)
  - [2.1. General](#21-general)

---
---
# 1. Terraform
## 1.1. Cheats
```sh
# initialize
terraform init

# plan
terraform plan
terraform plan -out <file> 

# apply
terraform apply
```

---
## 1.2. Building Blocks
### 1.2.1. Terraform Initial Settings
```terraform
terraform {
  required_bersion = ">= 0.15"
  required_providers {
    local = {
      source = "hashicorp/local"
      version = "~> 2.0"
    }
  }
}
```

### 1.2.2. Resources
- most important elements in Terraform
- provision infrastructure, such as VMS, load balancers, gateways and so forth
```terraform
resource "<TYPE>" "<Name>" {
}
```

### 1.2.3. Providers
- responsible for understanding API interactions
- making authenticated requests
- exposing resources to Terraform
```terraform
provider "<Name>" {
}
```

### 1.2.4. Data Sources
```terraform
data "<TYPE>" "<Name>" {
}
```

---
## 1.3. Functional Programming Language
- HCL modules are like un-pure functions
  1.3. - functions with side effects, like building infrastructure

---
## 1.4. Usage
### 1.4.1. Initilialization
- Terraform creates a hidden `.terraform` directory for installing plugins and modules

### 1.4.2. Planning
- 3 main stages of `terraform plan`
  1. read the configuration and state
     - reads main.tf
     - reads terraform.tfstate
  2. determine actions to take
  3. output the plan

### 1.4.3. Execution
- execute functions and their side effects

---
## 1.5. Best Practices


---
---
# 2. Kustomize
## 2.1. General
