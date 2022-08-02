# Cheetsheet for Cloud Infrastructure <!-- omit in toc -->
- [1. Terraform](#1-terraform)
  - [1.1. Cheats](#11-cheats)
  - [1.2. Best Practices](#12-best-practices)
    - [1.2.1. Files in Folder](#121-files-in-folder)
    - [1.2.2. Bubbling Up & Trinkleing Down](#122-bubbling-up--trinkleing-down)
  - [1.3. Lifetime](#13-lifetime)
    - [1.3.1. Terraform's Initial Settings](#131-terraforms-initial-settings)
    - [1.3.2. Terraform's Current State](#132-terraforms-current-state)
    - [1.3.3. Destroying Resources](#133-destroying-resources)
  - [1.4. Building Blocks](#14-building-blocks)
    - [1.4.1. Resources](#141-resources)
    - [1.4.2. Providers](#142-providers)
    - [1.4.3. Data Sources](#143-data-sources)
  - [1.5. Modules](#15-modules)
  - [1.6. Flat Modules](#16-flat-modules)
  - [1.7. Functional Programming Language](#17-functional-programming-language)
    - [1.7.1. Input Variables](#171-input-variables)
    - [1.7.2. Output Variables](#172-output-variables)
    - [1.7.3. for Expression](#173-for-expression)
    - [1.7.4. Local Values](#174-local-values)
    - [1.7.5. Conditional Expressions](#175-conditional-expressions)
    - [1.7.6. Local File](#176-local-file)
  - [1.8. Usage](#18-usage)
    - [1.8.1. Initilialization](#181-initilialization)
    - [1.8.2. Planning](#182-planning)
    - [1.8.3. Execution](#183-execution)
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
## 1.3. Lifetime
### 1.3.1. Terraform's Initial Settings
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

### 1.3.2. Terraform's Current State
- `terraform.tfstate` file used to keep track of the managed resources

### 1.3.3. Destroying Resources
- first generates an execution plan
  - as if there were no resources
  - marking all resources for deletion

---
## 1.4. Building Blocks
### 1.4.1. Resources
- most important elements in Terraform
- provision infrastructure, such as VMS, load balancers, gateways and so forth
```terraform
resource "<TYPE>" "<Name>" {
}
```

### 1.4.2. Providers
- responsible for understanding API interactions
- making authenticated requests
- exposing resources to Terraform
```terraform
provider "<Name>" {
}
```

### 1.4.3. Data Sources
```terraform
data "<TYPE>" "<Name>" {
}
```

---
## 1.5. Modules
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
## 1.6. Flat Modules
- reduces the nested modules in standard cascaded modules

---
## 1.7. Functional Programming Language
- HCL modules are like un-pure functions
  1.3. - functions with side effects, like building infrastructure

### 1.7.1. Input Variables
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

### 1.7.2. Output Variables
```terraform
output "<Name>" {
}
```

- used to do two things
  1. pass values between modules
  2. print to cli

### 1.7.3. for Expression
```terraform
# Output is defined as list '[ ... ]'
[ for s in [ <Sequence-to-iterate> ] : upper(s) ]

# Output is defined as map '{ ... }'
{ for k,v in var.<Name> : k => length(v) }
```

### 1.7.4. Local Values
``` terraform
locals { ... }
```

- assign a name to an expression
  - input variables analogous to function's arguments
  - output variables analogous to return values
  - local variables analogous to local temporary symbols

### 1.7.5. Conditional Expressions
```terraform
<Condition> ? <Value1> : <Value2>
```

### 1.7.6. Local File
```terraform
resource "local_file" "<Name>" {
}
```

---
## 1.8. Usage
### 1.8.1. Initilialization
- Terraform creates a hidden `.terraform` directory for installing plugins and modules

### 1.8.2. Planning
- 3 main stages of `terraform plan`
  1. read the configuration and state
     - reads main.tf
     - reads terraform.tfstate
  2. determine actions to take
  3. output the plan

### 1.8.3. Execution
- execute functions and their side effects


---
---
# 2. Kustomize
## 2.1. General
