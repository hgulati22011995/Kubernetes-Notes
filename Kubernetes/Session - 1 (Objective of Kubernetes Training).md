# What is Kubernetes?
### **Kubernetes:**
Kubernetes (often called **K8s**) is an open-source tool (platform) for **Orchestrating**(managing and automating) **containers**
- Containers are small,portable packages of software that include everything needed to run an app(code,libraries and settings).
- Kubernetes helps you **deploy**, **scale**, **move** and **monitor** all these containers across a group of computers, automatically.

It handles things like:
- **Starting**/**Stopping** **containers** when needed.
- **Balancing Load** (so no machine is overloaded)
- **Self-healing** (restarting containers if they crash).
- **Scaling-up/down** (adding more containers if traffic increases).

### **Orchestra and Orchestration:**

**Orchestra =** A group of musicians with different instruments (vilions, drums,trumpets etc). They each play their part - **but without coordination, it would sounds like chaos.**

**Orchestration =** The **act of organizing and directing** the orchestra so all instruments play in harmony at the right time.

![Alt text](Images/1.png)

Orchestra = all the apps, containers, pods, networks, storage.

Orchestration = Kubernetes controlling and coordinating all of it.

![Alt text](/images/2.png)

**Imagine a Shipping Company (like FedEX)**

**Containers =** Packages (your apps).

**Trucks =** Servers (machines that run apps).

**Kubernetes =** Dispatch manager (who decides which truck carries which package, reroutes if a truck breaks down and adds more trucks if there are too many packages).

The manager (kubernetes) makes sure:
- Packages are loaded onto the right trucks.
- Trucks don't get overloaded .
- If a trucks breaks, the packages are quickly moved to another one.
- If lots of packages arrives suddenly more trucks are sent out.
- If no packages are left, some trucks are sent home to save fuel.

# Objective of Kubernetes Traning

![Alt text](/images/3.png)

The main goals of kubernetes training are to:
- **Understand Container Orcestration:** Learn how kubernetes automates deployment, scaling and management of containerized applications.

- **Master Kubernetes Architecture:** Understand the roles of components like kube-apiserver, etcd, kubelet, kube-proxy, contoller manager and scheduler

![Alt text](/images/4.png)

- **Deploy and manage applications:** Create and manage Pods, Deployments, ReplicaSets, Services, Configmaps, Secrets and more.

- **Explore Networking, Storage and Security:** Configure persistent Storage, cluster networking, ingress contollers and secure workloads using RBAC, TLS and Secrets.

- **Use Helm & CI/CD Integrations:** Automate app deployment using Helm charts and integrate kubernetes with CI/CD pipelines (like jenkins, GitLab CI, ArgoCD)

![Alt text](/images/5.png)

- **Prepare for Certifications:** Build hands-on skills required to pass kubernetes certifications like CKA, CKAD and CKS.

# Prerequisites for Kubernetes Training:

To make the most of kubernetes training, You should be familiar with:

- **Linux Basics:** Commands, file system, networking, permissions, etc

- **Containers & Docker:** How containers works, docker run, images, volumes, networking, etc

- **Basic networking concepts:** IP, DNS, Port forwarding, Firewall Rules.

- **YAML Syntax:** Since most k8s configs are written in YAML.

- **Optional but Helpful:**
  - Cloud Platform basics(AWS,GCP, Azure) 
  - Git and version control 
  - Bash Scripting.

# Kubernetes Certifications:
Here are the main Kubernetes Certifications offered by the **Cloud Native Computing Foundation (CNCF)** in collaboration with **The Linux Foundation:**

## **CKA - Certified Kubernetes Administration**

- Focus: Cluster Administration, node management, networking, storage, security.
- Audience: system administrators, DevOps engineers.
- Duration: 2 hours (hands-on lab exam).
- Exam Fee: ~$400 USD.

![Alt text](/images/6.png)

## **CKAD - Certified Kubernetes Application Developer**

- Focus: Desiging and deploying apps in kubernetes, using core primitives
- Audience: Developers working with containerized applications
- Duration: 2 hours (hands-on lab exam).
- Exam Fee: ~$400 USD.

![Alt text](/images/7.png)

## **CKS - Certified Kubernetes Security Specialist**

- Focus: Securing container-based applications and kubernetes platforms.
- Prerequisites: You **must have a valid CKA certifications before attempting CKS.
- Audience: Security professionals, DevSecOps
- Duration: 2 hours (hands-on lab exam).
- Exam Fee: ~$400 USD.

![Alt text](/images/8.png)

## **KCNA - Kubenetes and Cloud Native Associate (Entry-level)**

- Focus: Foundational knowledge of kubernetes and cloud-native concepts. 
- Audience: Beginners, students or non-tech stakeholders.
- Duration: 90 minutes(multiple choice)
- Exam Fee: ~$250 USD.

![Alt text](/images/9.png)

# Kubernetes Training Syllabus (CKA + CKAD)

# Module 1: Kubernetes Fundamentals (Common for CKA & CKAD)
- History of Kubernetes and CNCF
- Kubernetes architecture (control plane and node components)
- Understanding Clusters and Nodes
- Kubernetes API server and object lifecycle
- Working with kubectl CLI
- YAML basics for kubernetes objects

# Module 2: Core Kubernetes concepts
- Pods:definition, lifecycle, multi-container pods
- ReplicaSets and Deployments
- Labels, Selectors and Annotations
- Namespaces and Resource Quotas
- Services: Cluster IP, NordPort, LoadBalancer, ExternalName
- Headless services and service discovery.

# Module 3: CKA-Specific - Cluster Administration
- Setting up a Kubernetes cluster (kubeadm, kind, Minikube)
- Certificate and Kubeconfig management
- Role-Based Access Control(RBAC)
- Static Pods, DaemonSets, and Taints/Tolerations
- Node management and troubleshooting (cordon, drain, taints, logs)
- Managing etcd and control plane components.

# Module 4: CKAD-Specific - Application Design & Development
- Desigining Cloud-native applications for kubernetes
- ConfigMaps and Secrets
- Probes: Liveness, Rediness and Startup
- Jobs and CronJobs
- Init Containers and Lifecycle Hooks
- Sidecar, Ambassador, and Adapter containers

# Module 5: Configuration and Secrets
- ConfigMaps: creation, usage in pods
- Secrets: creation, usage, mounting in pods
- Environment variable and volume-based configuration
- Resource Requests and Limits
- Working with kubectl explain, kubectl get, kubectl describe, kubectl logs

# Module 6: Networking
- Kubernetes networking model
- CNI plugins overview (Calico, Flannel, Weave)
- Pod-to-Pod and Pod-to-Service networking
- DNS in Kubernetes
- Ingress Controllers and ingress Resources (Nginx, Traefik)
- Network policies

# Module 7: Storage
- Volumes: emptyDir, hostpath, configMap, secret
- PersistentVolumes (PVs) and PersistentVolumeClaims (PVCs)
- StorageClasses and dynamic provisioning
- StatefulSets and VolumeClaim Templates
- CSI drivers overview

# Module 8: Observability, Logging and monitoring
- Kubernetes logging architecture
- kubectl logs, kubectl top and kubectl events
- Monitoring with Prometheus and Grafana
- Metric Server
- Troubleshooting common pod and node issues
- Audit logs and access review

# Module 9: Scheduling and Affnity (CKA)
- Manual and automatic scheduling
- Scheduler policies and strategies
- Affinity and Anti-Affinity rules
- Node Affinity, Pod Affinity
- Taints and Tolerations
- Resource limits and quality of service (QoS)

# Module 10: Testing & Debugging Applications (CKAD)
- Debugging failing pods using kubectl
- Troubleshooting probes
- Logs and exec into containers
- Ephemeral containers for debugging
- Understanding and resolving CrashLoopBackOff and ImagePullBackOff

# Module 11: Security and RBAC
- Users, Groups and ServiceAccounts
- RBAC: Roles, CluserRoles, RoleBindings, ClusterRoleBindings
- Pod Security Standards (Restricted, Baseline, Previleged)
- Network policies for traffic control
- SecurityContext and PodSecurityContext
- Image security and best practices

# Module 12: Helm and Packaging(Bonus)
- Introduction to Helm
- Installing and configuring Helm
- Helm charts: structure and usage
- Deploying applications with Helm
- Creating your own Helm charts

# Module 13: Advanced Topics(CKA)
- API access and aggregation
- Custom Resource Definitions(CRDs)
- Controllers and Operators overview
- Kubernetes Upgrades and version skew
- Backup and restore with etcdctl and Velero
- Cluster maintenance and draining

# Module 14: Exam Preparation and Practice
- CKAD: Practice Questions and Sample Tasks
- CKA: Practice Questions and Sample Tasks
- Realistic scenario-based labs
- Time-boxed mock exams
- Tips and strategies for exam environment

# Course Duration & Format:

**- Total Duration:** 60-70 hours
**- Format:**
 - 70% hands-on labs
 - 30% conceptual explanations
 - Weekly assessments.
 - Final mock exams for both CKA and CKAD



