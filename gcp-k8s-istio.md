# Cheetsheet for GCP, Kubernetes & Istio <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. GCP](#1-gcp)
  - [1.1. Infrastructure](#11-infrastructure)
    - [1.1.1. Virtual Machines](#111-virtual-machines)
    - [1.1.2. Containers](#112-containers)
    - [1.1.3. Pods](#113-pods)
    - [1.1.4. Nodes](#114-nodes)
  - [1.2. Components](#12-components)
    - [1.2.1. Services](#121-services)
    - [1.2.2. Load Balancers](#122-load-balancers)
    - [1.2.3. Deployments](#123-deployments)
  - [1.3. Cheats](#13-cheats)
- [2. Kubernetes](#2-kubernetes)
  - [2.1. Nice to know](#21-nice-to-know)
  - [2.2. Components](#22-components)
    - [Config Maps & Secrets](#config-maps--secrets)
      - [Secret](#secret)
    - [2.2.1. Service](#221-service)
    - [2.2.2. Ingress/Egress](#222-ingressegress)
      - [2.2.2.1. Ingress Mappings](#2221-ingress-mappings)
      - [Terminating TLS at ingress](#terminating-tls-at-ingress)
      - [2.2.2.2. Commands](#2222-commands)
  - [2.3. Configurations](#23-configurations)
    - [2.3.1. Config Maps](#231-config-maps)
  - [2.4. Cheats](#24-cheats)
- [3. Istio](#3-istio)
  - [3.1. Service Mesh](#31-service-mesh)
  - [3.2. Components](#32-components)
    - [3.2.1. VirtualServices](#321-virtualservices)
  - [3.3. Cheats](#33-cheats)
- [4. curl](#4-curl)
  - [4.1. Resolve local DNS for Docker use of Istio](#41-resolve-local-dns-for-docker-use-of-istio)

---
---
# 1. GCP
## 1.1. Infrastructure
### 1.1.1. Virtual Machines
### 1.1.2. Containers
### 1.1.3. Pods
### 1.1.4. Nodes

---
## 1.2. Components
### 1.2.1. Services
### 1.2.2. Load Balancers
### 1.2.3. Deployments

---
## 1.3. Cheats

---
---
# 2. Kubernetes
## 2.1. Nice to know
- use an ingress for forwarding all paths to `defaultBackend` instead of simply setting the service type to `LoadBalancer`
  - ingress can provide additional HTTP features
    - securing the communication
      - Kubernetes doesn't provide a standard way to configure TLS passthrough
      - terminating the TLS connection at the ingress proxy
    - ...
- TLS Passthrough := *TODO*
## 2.2. Components

### Config Maps & Secrets
#### Secret
- defined as kind of secret
  ``` yml
  apiVersion: v1
  kind: Secret
  metadata:
    name: <NAME>
  type: kubernetes.io/tls
  data:
    tls.crt: <TOKEN>
    tls.key: <PWD>
  ```

### 2.2.1. Service
- the label selector defines the pod that belong to this service
  ``` yaml
  apiVersion: v1
  kind: Service
  # ...
  spec:
    selector:
        app: fun404
  # ...
  ```
### 2.2.2. Ingress/Egress
- In/Output gateways (kindof)
- **exposes a single URL** and routes the paths to different internal services
  - *GCP LoadBalancers would expose an URL for every microservice*
- has a `default backend` for non matching route rules

#### 2.2.2.1. Ingress Mappings
- request to path to different services
  - done with rules in the `Ingress.spec`
  ``` yaml
  kind: Ingress
  #...
  spec:
    ingressClassName: nginx     # needed for DockerDesktop and nginx-ingress-controller
    rules:
    - host: <URL>
      http:
        paths:
        - path: </path>
          pathType: [Exact/Prefix/ImplementationSpecific]
          backend:
            service:
                name: <NAME>
                port:
                  name: http
  ```
    - **Exact**: must match *exactly*
    - **Prefix**: must begin with path specified 
    - **ImplementationSpecific**: depends on the controller impl
- **wildcard** can be used within host field matchings
  - `*.example.com`

#### Terminating TLS at ingress
- ingress controlloer impls support **TLS termination at the ingress proxy**
  - forwards the HTTP request unencrypted
  - to terminate the proxy needs TLS certificate and private key
- add TLS secret
  ``` yml
  tls:
  - secretName: <SECRET_NAME>
    hosts:
    - "*.address.com"
  ```

#### 2.2.2.2. Commands
- inspect a deployed ingress object
  - GCP already provides ingress and egress
  
  ``` s
  kubectl get ing
  kubectl describe ing <INGRESS_NAME>
  ```
  - `describe` provides a view onto the **rules**
- get yaml file from deployed in/egress
  ``` s
  kubectl get ing <INGRESS_NAME> -o yaml
  ```
- k9s shortcut for description or yaml
  ``` s
  :ingress
  <d>
  <y>
  ```  
---
## 2.3. Configurations
### 2.3.1. Config Maps
- used to bring ENV variables to the pods

---
## 2.4. Cheats

---
---
# 3. Istio
## 3.1. Service Mesh
Like a distruted service bus.
## 3.2. Components
### 3.2.1. VirtualServices

---
## 3.3. Cheats

---
---
# 4. curl
## 4.1. Resolve local DNS for Docker use of Istio
```
curl <HOST/PATH> --resolve <URL>:<PORT>:<IPAddress>
```
- alternatively add following entry to `/etc/hosts`
  `<IPAddress> <URL>`