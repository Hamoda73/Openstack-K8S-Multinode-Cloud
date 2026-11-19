<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0a,100:ED1944&height=180&section=header&text=OpenStack%20Multi-Node%20Cloud&fontSize=42&fontColor=ffffff&fontAlignY=38&desc=Private%20cloud%20with%20Kubernetes%20and%20Ansible&descAlignY=60&descSize=18" alt="OpenStack Multi-Node Cloud" width="100%" />

<br>

![ESPRIT](https://img.shields.io/badge/ESPRIT_School_of_Engineering-C8102E?style=for-the-badge&logoColor=white)

<br>

![Period](https://img.shields.io/badge/Oct_2024_--_May_2025-blue?style=flat-square)
![Type](https://img.shields.io/badge/type-team_project-orange?style=flat-square)
![Domain](https://img.shields.io/badge/domain-private_cloud_%2F_IaC-2ea44f?style=flat-square)

<br><br>

<img src="https://skillicons.dev/icons?i=kubernetes,ansible,prometheus,grafana,linux,docker,bash&perline=7" alt="tech stack" />

<br><br>

![OpenStack](https://img.shields.io/badge/OpenStack-ED1944?style=for-the-badge&logo=openstack&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

</div>

---

## 📖 Overview

Design and deployment of a **multi-node private cloud** on **OpenStack**, with **Kubernetes** clusters running on top of it. The platform separates the cloud into dedicated **controller, network, compute and storage nodes**, automates instance provisioning and scaling, manages cluster configuration with **Ansible**, and is monitored in real time with **Prometheus** and **Grafana**.

This was a **team project**. Each team member took ownership of a node role, and I was responsible for the **compute node**.

## 🏗️ Architecture

```mermaid
flowchart TB
    ANS["Ansible automation"]

    subgraph OS["OpenStack private cloud"]
        direction TB
        CTRL["Controller node<br/>Keystone, Glance, Nova API, Placement, Neutron server, Horizon"]
        NET["Network node<br/>Neutron L3, DHCP and metadata agents"]
        COMP["Compute node<br/>Nova compute, hypervisor, Neutron agent"]
        STOR["Storage node<br/>Cinder block storage, Swift object storage"]
        CTRL --- NET
        CTRL --- COMP
        CTRL --- STOR
        NET --- COMP
        STOR --- COMP
    end

    subgraph K8S["Kubernetes cluster running on OpenStack instances"]
        direction LR
        MASTER["Control plane"]
        W1["Worker 1"]
        W2["Worker 2"]
        MASTER --- W1
        MASTER --- W2
    end

    subgraph MON["Monitoring"]
        direction LR
        PROM["Prometheus"] --> GRAF["Grafana dashboards"]
    end

    ANS -->|deploys and configures| OS
    ANS -->|configures| K8S
    COMP -->|hosts the instances| K8S
    PROM -. scrapes metrics .-> OS
    PROM -. scrapes metrics .-> K8S
```

## 🖥️ Node roles

| Node | Responsibility | Main components |
|---|---|---|
| **Controller** | Control plane of the cloud: identity, APIs, scheduling, dashboard | Keystone, Glance, Nova API and scheduler, Placement, Neutron server, Horizon, database, message queue |
| **Network** | Virtual networking, routing, DHCP and external connectivity | Neutron L3 agent, DHCP agent, metadata agent, Open vSwitch / Linux bridge |
| **Compute** | Runs the virtual machines that host the Kubernetes nodes | Nova compute, KVM/QEMU hypervisor, Neutron agent |
| **Storage** | Persistent block and object storage | Cinder (volumes), Swift (objects) |

## 🧩 OpenStack services

| Service | Role |
|---|---|
| **Keystone** | Identity, authentication, authorization and service catalog |
| **Glance** | Image registry for virtual machine images |
| **Nova** | Instance lifecycle and scheduling across compute nodes |
| **Placement** | Resource inventory and allocation tracking for the scheduler |
| **Neutron** | Virtual networks, subnets, routers, security groups and floating IPs |
| **Cinder** | Persistent block storage volumes attached to instances |
| **Swift** | Scalable object storage |
| **Horizon** | Web dashboard to manage the cloud |

## 👤 My contribution: the compute node

- Deployed and configured the **compute node** that hosts the instances of the cloud
- Set up **Nova compute** with the **KVM/QEMU hypervisor** and connected it to the controller's Nova, Placement and message queue services
- Configured the **Neutron agent** on the node so instances attach to the virtual networks managed by the network node
- Integrated the compute node with **Glance** for images and **Cinder** for volumes, so instances boot from images and use persistent storage
- Validated instance provisioning end to end, from image to running VM with networking and a volume attached
- Automated the node configuration with **Ansible** so it can be rebuilt and scaled with additional compute nodes
- Exposed node metrics to **Prometheus** for monitoring in **Grafana**

## ✨ Platform highlights

- **Multi-node OpenStack cloud** split into controller, network, compute and storage roles
- **Automated provisioning and scaling** of instances for optimal resource utilization
- **Kubernetes clusters** deployed on OpenStack instances
- **Infrastructure as Code**: cluster and node configuration managed with Ansible playbooks
- **Observability**: real-time metrics and dashboards with Prometheus and Grafana

## 🔄 Workflow

1. Prepare the nodes, network segments and base operating system
2. Deploy the OpenStack core services on the controller node
3. Configure networking on the network node and virtualization on the compute node
4. Attach block and object storage through Cinder and Swift
5. Provision instances and build the Kubernetes cluster on top
6. Automate configuration with Ansible and monitor everything with Prometheus and Grafana

## 🛠️ Tech stack

| Area | Technologies |
|---|---|
| Private cloud | OpenStack: Keystone, Glance, Nova, Placement, Neutron, Cinder, Swift, Horizon |
| Virtualization | KVM, QEMU |
| Orchestration | Kubernetes |
| Automation | Ansible |
| Monitoring | Prometheus, Grafana |
| Systems | Linux server administration |

## 🎯 Key takeaways

- Designing a private cloud with clearly separated controller, network, compute and storage roles
- Understanding how OpenStack services interact: identity, images, scheduling, networking and storage
- Running Kubernetes on top of an IaaS layer
- Teamwork on shared infrastructure with clear ownership per node
- Infrastructure as Code and observability for reproducible, monitored environments

---

<div align="center">

### 👤 Author

**Mohamed Khelifi** · Cloud & DevOps Engineer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0a66c2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/khelifimohamed)
[![Portfolio](https://img.shields.io/badge/Portfolio-A7A459?style=for-the-badge&logo=githubpages&logoColor=white)](https://hamoda73.github.io)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Hamoda73)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:ED1944,100:0a0a0a&height=90&section=footer" width="100%" alt="footer" />

</div>
