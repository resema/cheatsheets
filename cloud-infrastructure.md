# Cheetsheet for Cloud Infrastructure <!-- omit in toc -->
- [1. Terraform](#1-terraform)
  - [1.1. Cheats](#11-cheats)
  - [1.2. Best Practices](#12-best-practices)
    - [1.2.1. Files in Folder](#121-files-in-folder)
    - [1.2.2. Bubbling Up & Trinkleing Down](#122-bubbling-up--trinkleing-down)
  - [1.3. Usage](#13-usage)
    - [1.3.1. Initilialization](#131-initilialization)
    - [1.3.2. Planning](#132-planning)
    - [1.3.3. Execution](#133-execution)
  - [1.4. Lifetime](#14-lifetime)
    - [1.4.1. Terraform's Initial Settings](#141-terraforms-initial-settings)
    - [1.4.2. Terraform's Current State](#142-terraforms-current-state)
    - [1.4.3. Destroying Resources](#143-destroying-resources)
    - [1.4.4. Reusing Configuration Code with Workspaces](#144-reusing-configuration-code-with-workspaces)
  - [1.5. Building Blocks](#15-building-blocks)
    - [1.5.1. Resources](#151-resources)
    - [1.5.2. Providers](#152-providers)
    - [1.5.3. Data Sources](#153-data-sources)
  - [1.6. Modules](#16-modules)
  - [1.7. Flat Modules](#17-flat-modules)
  - [1.8. Functional Programming Language](#18-functional-programming-language)
    - [1.8.1. Input Variables](#181-input-variables)
    - [1.8.2. Output Variables](#182-output-variables)
    - [1.8.3. for Expression](#183-for-expression)
    - [1.8.4. Local Values](#184-local-values)
    - [1.8.5. Conditional Expressions](#185-conditional-expressions)
    - [1.8.6. Local File](#186-local-file)
- [2. Kustomize](#2-kustomize)
  - [2.1. General](#21-general)
- [3. Docker](#3-docker)
  - [3.1. Cheats](#31-cheats)

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
terraform apply -target='<module.name>'

# refresh, like plan but does not modify managed existing infrastructure - just TF state
terraform refresh

# delete resources
terraform destroy -auto-approve
```

---
## 1.2. Best Practices
### 1.2.1. Files in Folder
- each module should contain
  - `variables.tf`
  - `main.tf`
  - `outputs.tf`

### 1.2.2. Bubbling Up & Trinkleing Down
#### Bubbling UP <!-- omit in toc -->
- `<ModuleName>.<VarName>`

#### Trinkleing Down <!-- omit in toc -->
- `var.<Name>`

---
## 1.3. Usage
### 1.3.1. Initilialization
- Terraform creates a hidden `.terraform` directory for installing plugins and modules

### 1.3.2. Planning
- 3 main stages of `terraform plan`
  1. read the configuration and state
     - reads main.tf
     - reads terraform.tfstate
  2. determine actions to take
  3. output the plan

### 1.3.3. Execution
- execute functions and their side effects

---
## 1.4. Lifetime
### 1.4.1. Terraform's Initial Settings
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

### 1.4.2. Terraform's Current State
- `terraform.tfstate` file used to keep track of the managed resources

### 1.4.3. Destroying Resources
- first generates an execution plan
  - as if there were no resources
  - marking all resources for deletion

### 1.4.4. Reusing Configuration Code with Workspaces
- allow to have more than one state file for the same configuration code
  - deploy to multiple environments
```terraform
# list workspaces
terraform workspace list

# 
```

---
## 1.5. Building Blocks
### 1.5.1. Resources
- most important elements in Terraform
- provision infrastructure, such as VMS, load balancers, gateways and so forth
```terraform
resource "<TYPE>" "<Name>" {
}
```

### 1.5.2. Providers
- responsible for understanding API interactions
- making authenticated requests
- exposing resources to Terraform
```terraform
provider "<Name>" {
}
```

### 1.5.3. Data Sources
```terraform
data "<TYPE>" "<Name>" {
}
```

---
## 1.6. Modules
```terraform
module "<Name>" {
  source    = "<MetaArguments>"
  namespace = var.namespace
  Version   = "SemVer"

  <Input-Var> = <Value>
}
```

- self-contained packages of code
  - reusable components
- every workspace has a **root module**
  - it's the directory where `terraform apply` is run
  - consists of
    - `variables.tf`
    - `terraform.tfvars`
    - `providers.tf`
    - `main.tf`
    - `outputs.tf`
    - `versions.tf`
- namespace variable is **project identifier**

---
## 1.7. Flat Modules
- reduces the nested modules in standard cascaded modules
- organize codebase as lots of little `.tf` files within a single monolithic module
- most effective in **small-to-medium** codebases

---
## 1.8. Functional Programming Language
- HCL modules are like un-pure functions
  1.3. - functions with side effects, like building infrastructure

### 1.8.1. Input Variables
```terraform
variable "<Name>" {
  description = "Contains some useful information"
  type = list(string)
}
```

- variable blocks accept four input arguments
  1. **default**: preselcted option to use when no alternative is available
  2. **description**: string value for documentation
  3. **type**: type constraint
  4. **validation**: enforce custom validation rules
- **type coercion** is the ability to convert any primitive type to its string representative

#### Assigning Values with a Variable Definition File  <!-- omit in toc -->
- set variable values with any files ending in either `.tfvars` or `.tfvars.json`

### 1.8.2. Output Variables
```terraform
output "<Name>" {
}
```

- used to do two things
  1. pass values between modules
  2. print to cli

### 1.8.3. for Expression
```terraform
# Output is defined as list '[ ... ]'
[ for s in [ <Sequence-to-iterate> ] : upper(s) ]

# Output is defined as map '{ ... }'
{ for k,v in var.<Name> : k => length(v) }
```

### 1.8.4. Local Values
``` terraform
locals { ... }
```

- assign a name to an expression
  - input variables analogous to function's arguments
  - output variables analogous to return values
  - local variables analogous to local temporary symbols

### 1.8.5. Conditional Expressions
```terraform
<Condition> ? <Value1> : <Value2>
```

### 1.8.6. Local File
```terraform
resource "local_file" "<Name>" {
}
```

---
---
# 2. Kustomize
## 2.1. General


---
---
# 3. Docker
## 3.1. Cheats
```sh
# accessing a crashing container
docker run -it --entrypoint /bin/bash eu.gcr.io/prj-ene-dev-dlbm/services/compute-close-trim-gingiva-service:v6885a626df
```