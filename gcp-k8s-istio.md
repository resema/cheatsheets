# Cheetsheet for GCP, Kubernetes & Istio <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. GCP](#1-gcp)
  - [1.1. Cheats](#11-cheats)
  - [1.2. Infrastructure](#12-infrastructure)
    - [1.2.1. Virtual Machines](#121-virtual-machines)
    - [1.2.2. Containers](#122-containers)
    - [1.2.3. Pods](#123-pods)
    - [1.2.4. Resource Management for Pods and Containers](#124-resource-management-for-pods-and-containers)
    - [1.2.5. Nodes](#125-nodes)
    - [1.2.6. Setup](#126-setup)
  - [1.3. Components](#13-components)
    - [1.3.1. Services](#131-services)
    - [1.3.2. Load Balancers](#132-load-balancers)
    - [1.3.3. Deployments](#133-deployments)
- [2. Kubernetes](#2-kubernetes)
  - [2.1. Cheats](#21-cheats)
  - [2.2. Nice to know](#22-nice-to-know)
  - [2.3. Components](#23-components)
    - [2.3.1. Config Maps & Secrets](#231-config-maps--secrets)
      - [2.3.1.1. Secret](#2311-secret)
    - [2.3.2. Service](#232-service)
    - [2.3.3. Ingress/Egress](#233-ingressegress)
      - [2.3.3.1. Ingress Mappings](#2331-ingress-mappings)
      - [2.3.3.2. Terminating TLS at ingress](#2332-terminating-tls-at-ingress)
      - [2.3.3.3. Commands](#2333-commands)
  - [2.4. Configurations](#24-configurations)
    - [2.4.1. Config Maps](#241-config-maps)
- [3. Istio](#3-istio)
  - [3.1. Cheats](#31-cheats)
  - [3.2. Service Mesh](#32-service-mesh)
  - [3.3. Components](#33-components)
    - [3.3.1. VirtualServices](#331-virtualservices)
  - [3.4. Cheats](#34-cheats)
- [4. Tools](#4-tools)
  - [4.1. curl](#41-curl)
    - [4.1.1. Resolve local DNS for Docker use of Istio](#411-resolve-local-dns-for-docker-use-of-istio)
  - [4.2. grpcurl](#42-grpcurl)
  - [4.3. k9s](#43-k9s)
    - [4.3.1. Shortcuts](#431-shortcuts)

---
---
# 1. GCP
## 1.1. Cheats
## 1.2. Infrastructure
### 1.2.1. Virtual Machines
### 1.2.2. Containers
### 1.2.3. Pods
### 1.2.4. Resource Management for Pods and Containers

- If the node where a Pod is running has enough of a resource available, **it's possible (and allowed) for a container to use more resource than its request for that resource specifies**.
- However, a container is **not allowed to use more than its resource limit**.

``` yml
apiVersion: v1
kind: Pod
#...
spec:
  containers:
  - name: app
    image: images.my-company.example/app:v4
    resources:
      requests:
        memory: "64Mi"
        cpu: "250m"
      limits:
        memory: "128Mi"
        cpu: "500m"
```

### 1.2.5. Nodes

### 1.2.6. Setup
``` sh
# list projects
gcloud projects list

# set project
gcloud config set project prj-ligcore-eu-dev-wkuh
# get project
gcloud config get project

# auth
gcloud auth login
gcloud auth login --no-launch-browser

gcloud auth application-default login --no-launch-browser

# list clusters
gcloud container clusters list

# get credentials
gcloud container clusters get-credentials d-eu-west4 --zone=europe-west4

# use context
kubectl config use-context gke_prj-ene-dev-dlbm_europe-west4-b_dev-europe-west4-b
```
---
## 1.3. Components
### 1.3.1. Services
### 1.3.2. Load Balancers
### 1.3.3. Deployments

---
---
# 2. Kubernetes
## 2.1. Cheats

---
## 2.2. Nice to know
- use an ingress for forwarding all paths to `defaultBackend` instead of simply setting the service type to `LoadBalancer`
  - ingress can provide additional HTTP features
    - securing the communication
      - Kubernetes doesn't provide a standard way to configure TLS passthrough
      - terminating the TLS connection at the ingress proxy
    - ...
- TLS Passthrough := *TODO*
## 2.3. Components

### 2.3.1. Config Maps & Secrets
#### 2.3.1.1. Secret
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

### 2.3.2. Service
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
### 2.3.3. Ingress/Egress
- In/Output gateways (kindof)
- **exposes a single URL** and routes the paths to different internal services
  - *GCP LoadBalancers would expose an URL for every microservice*
- has a `default backend` for non matching route rules

#### 2.3.3.1. Ingress Mappings
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

#### 2.3.3.2. Terminating TLS at ingress
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
- by adding TLS secret to the ingress, all services from this Ingress object are secured

#### 2.3.3.3. Commands
- inspect a deployed ingress object
  - GCP already provides ingress and egress
  
  ``` sh
  kubectl get ing
  kubectl describe ing <INGRESS_NAME>
  ```
  - `describe` provides a view onto the **rules**
- get yaml file from deployed in/egress
  ``` sh
  kubectl get ing <INGRESS_NAME> -o yaml
  ```
- k9s shortcut for description or yaml
  ``` sh
  :ingress
  <d>
  <y>
  ```  
---
## 2.4. Configurations
### 2.4.1. Config Maps
- used to bring ENV variables to the pods


---
---
# 3. Istio
## 3.1. Cheats

---
## 3.2. Service Mesh
Like a distruted service bus.

---
## 3.3. Components
### 3.3.1. VirtualServices

---
## 3.4. Cheats

---
---
# 4. Tools
## 4.1. curl
### 4.1.1. Resolve local DNS for Docker use of Istio
``` sh
curl <HOST/PATH> --resolve <URL>:<PORT>:<IPAddress> -v  # v: verbose

# with TLS and TLS terminating at ingress
curl https://<HOST/PATH> --resolve <URL>:443:127.0.0.1 -v -k # k: insecure
```
- alternatively add following entry to `/etc/hosts`
  `<IPAddress> <URL>`

## 4.2. grpcurl
``` sh
## grpcurl
grpcurl -d '{"min": 10, "max":10}' -cacert /etc/ssl/cert.pem grpc.ene.dev.dscore.com:443 example.RandomGenerator/GetRandomNumber

### with port-forwarding
grpcurl -d '{"min": 10, "max":10}' -proto ../../../../services/random-generator/api.proto -plaintext 127.0.0.1:50051 example.RandomGenerator/GetRandomNumber
```

---
## 4.3. k9s
### 4.3.1. Shortcuts
``` sh
:= help
/ := filter
: := cmd

:context
:service
:pod
:ingress
:secret
:configmap

shift-f -> "port forwarding"
y -> yaml
d -> describe
```

