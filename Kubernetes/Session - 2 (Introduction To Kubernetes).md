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

![Alt text](/images/1.png)

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

# Running containers without Kubernetes

Running containers **without Kubernetes:**

In a standalone mode (e.g using just Docker), can lead to several operational and scalability problems, especially as your system grows.

![Alt text](/images/10.png)

Problems associated while running containers in standalone mode:

![Alt text](/images/11.png)

**1. No Built-in High Availablility**
- Containers can fail or crash.
- Without Kubernetes, there's no atomatic rescheduling or failover.
- You must manually detect and restart failed containers.

**2. Manual Scaling**
- Scaling up or down requires scripting or manual intervention.
- No horizontal pod autoscaling based on CPU, memory or custom metrics.

**3. Lack of Self-Healing**
- If a container dies, it's gone unless you have custom watchdog scripts.
- Kubernetes automatically restarts or replaces failed containers.

**4. No Service Discovery or Load Balancing**
- You must manually manage IP addresses or DNS for container-to-container communication.
- Load balancing across container instances isn't built-in

**5. Poor configuration & Secret Management**
- You often hardcore environment variables or config files.
- Kubernetes provides ConfigMaps and Secrets for secure and flexible config injection.

**6. No Declarative Infrastructure**
- Without Kubernetes, deployment is usually done imperatively(commands/scripts).
- No unified YAML/manifest files to describe desired state.

**7. Difficult Rollouts & Rollbacks**
- No built-in mechanisms for rolling updates or versioned rollbacks.
- Kubernetes offers zero-downtime rollouts, rollback and progressive delivery strategies.

**8. No Native Monitoring or Logging Integration**
- You must integrate external tools for health checks, metrics and logging.
- Kubernetes has native support or integration paths for Prometheus, Fluentd, etc

**9. Security & Resource Isolation Issues**
- Without Kubernetes limiting container CPU/memory usage is manual and error-prone.
- Kubernetes enforces resource quotas, namespaces and policies.

**10. Difficult Multi-Host Deployments**
- Orchestrating containers across multiple servers is complex.
- Kubernetes simplifiles this with cluster management and node scheduling.

# Benefits of using Kubernetes

Using an orchestration tool like **Kubernetes** offers numerous advantages, especially for managing containerized applications at scale. Here are the key benefits:

![Alt text](/images/12.png)

**1. Centralized Management**
- Manage containers, deployments, updates and configurations from a single control plane.
- Consistent policy enforcement and monitoring across environments.

**2. Efficient Resource Utlilization**
- Kubernetes schedules workloads based on available CPU, memory and other resources.
- Prevents overprovisioning and underutlilization of nodes.

**3. Self-Healing & Auto-Recovery**
- Automatically restarts failed containers.
- Reschedules pods on healthy nodes in case of failure.
- Ensures services maintain desired state.

**4. Scalability**
- Easly scale applications up or down using horizontal pod autoscalers.
- Supports both manual and automatic scaling based on metrics.

**5. Cluster Architecture & High Availability**
- Multi-node arcitecture allows for failover and redundancy.
- Control plane components can be run in High Availability(HA) mode.

**6. Rolling Updates & Rollback**
- Deploy application updates without downtime.
- Instantly rollback to previous stable versions if something breaks.

**7. Service Discovery & Load Balancing**
- Built-in service discovery (via DNS).
- Automatic load balancing across pod replicas.

**8. Security & Policy Enforcement**
- Role-based access control(RBAC).
- Secrets and ConfigMaps for security & modular configurations.
- Network policies to isolate workloads.

**9. Infrastructure Abstraction**
- Abstracts the underlying infrastructure (cloud, on-prem, hybrid).
- Consistent deploymennt experience across environments.

**10. Declarative Configuration & Automation**
- Use YAML manifest for versioned, reproducible & auditable deployments.
- Works seamlessly with GitOps and CI/CD pipelines.

# Kubernetes Arcitecture:

![Alt text](/images/13.png)

Kubernetes architecture is based on:
- **Control Plane (Master Node) -** Manages the cluster.
- **Worker Nodes -** Run containerized applications.
- **etcd -** A consistent and highly available key-value store used to store all cluster data.

The **Kubernetes master node** (now often referred to as **control plane**) is the central component of a kubernetes cluster. It is responsible for managing the cluster and orchestrating all activities across the worker nodes, such as scheduling applications, maintaining the desired state, scaling and rolling out updates.

![Alt text](/images/12.png)

![Alt text](/images/14.png)

**Key Components of the Master Node:**

**1. kube-apiserver:**
- Acts as the front-end of the kubernetes control plane.
- All communication (from users, CLI tools, or other components) goes through the API server.

**2. etcd:**
- A distributed key-value store that stores all cluster data(state and configuration).
- It is the single source of truth for the entire cluster.

![Alt text](/images/15.png)

**3. Kube-scheduler:**
- Assigns pods to available worker nodes based on resource requirements, constraints and policies.

**4. kube-controller-manager:**

- Runs various controllers (e.g. Node controller, Replication Controller) to ensure the cluster's desired state machines its actual state.

**5. cloud-controller-manager**(optional):
- Manages cloud-specific control logic if running on a cloud provider (e.g. load balancer, storage, etc.)

A **Kubernetes Worker Node** is a machine (physical or virtual) that runs the actual applications (containers) in a kubernetes cluster. The worker node receives instructions from the **control plane** (master node) and manages the execution of workloads.

![Alt text](/images/16.png)

**Key components of a Worker Node:**

**1. Kubelet:**
- An agent that runs on every worker node.
- It communicates with the control plane, ensuring the containers describe in the PodSpecs are running and healthy.

![Alt text](/images/17.png)

**2. kube-proxy:**
- A network component that manages networking rules on the node.
- It handles routing and load-balancing traffic to the correct containers across the cluster.

**3. Container Runtime**
- Software responsible for running containers (e.g. Docker, containerd, CRI-O).
- It pulls container images and starts containers based on kubernetes instructions.

**4. Pods:**
- The smallest deployable units in kubernetes usually containing one or more containers.

# Types of Kubernetes Clusters:

User-managed Vs Cloud-managed.

**1. User-Managed Kubernetes Clusters(Self-Managed)**

**Definition:** You (or your team) are responsible for installing, configuring, operating and maintaining the entire kubernetes cluster (control plane + worker nodes).

- **Examples:**
  - Kubernetes installed on VMs (e.g. using kubeadm)
  - Bare metal kubernetes clusters.
  - On-premises kubernetes (e.g. Rancher, OpenShift, self-hosted)

- **Responsibilities:**

  - Install kubernetes (control plane and nodes)
  - Upgrades and patch the kubernetes versions manually
  - Set-up networking, storage, monitoring, logging, security.
  - Handle scaling manually

- **Pros:**
  - Full control over cluster configuration and infrastructure
  - Flexibility to customize
  - Often lower costs at scale (after setup)

- **Cons:**
  - High operational complexity
  - Requires deep kubernetes expertise
  - Higher risk of misconfigurations
  - Responsible for HA (high availability), backup, recovery, etc.

**2. Cloud-Managed Kubernetes Clusters (Managed Kubernetes)**

**Definition:** A cloud provider sets up and manages the Kubernetes control plane (and sometimes nodes too). You focus mainly on deploying and managing your applicatiobs. (PAAS Model)

- **Examples:**
  - **Amazon EKS** (Elastic Kubernetes Service)
  - **Google GKE** (Google Kubernetes Engine)
  - **Azure EKS** (Azure Kubernetes Service)
  - **IBM Cloud Kubernetes Service**
  - **DigitalOcean Kubernetes**, etc.

- **Responsibilities:**
  - User typically manages worker nodes and applications (sometimes nodes are also managed).
  - Provider handles control plane upgrades, patching, backup, availability.
  - Integrations with cloud services (storage, networking, IAM, etc.)

- **Pros:**
  - Simplified operations (less DevOps overhead)
  - Automatic upgrades, scaling, HA for the control plane
  - Integrated security and compliance options
  - Faster to get started and scale

- **Cons:**
  - Less flexibility (some cloud restrictions)
  - Cost can be higher
  - Potential vendor lock-in
  - Limited access to control plane internals (no "full" admin access)










