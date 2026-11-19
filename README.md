<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0a,100:ED1944&height=170&section=header&text=Multi-Node%20OpenStack%20Cloud&fontSize=42&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Private%20cloud%20automated%20with%20Ansible%20%7C%20Kubernetes%20%7C%20Prometheus%20%26%20Grafana&descAlignY=60&descSize=16" alt="banner" width="100%" />

<br>

![ESPRIT](https://img.shields.io/badge/ESPRIT_School_of_Engineering-C8102E?style=for-the-badge&logoColor=white)

<br>

![Period](https://img.shields.io/badge/Oct_2024_--_May_2025-blue?style=flat-square)
![Type](https://img.shields.io/badge/type-academic_project-orange?style=flat-square)
![Domain](https://img.shields.io/badge/domain-private_cloud_%7C_IaC-2ea44f?style=flat-square)

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

Design and deployment of a **multi-node private cloud** built on **OpenStack**, running **Kubernetes** clusters on top of it. Instance provisioning and scaling are automated to make optimal use of resources, cluster configuration is managed with **Ansible**, and the whole platform is observed in real time with **Prometheus** and **Grafana**.

## 🏗️ Architecture

> TODO: adjust this diagram to match your real topology (node roles, networks, number of nodes).

```mermaid
flowchart TB
    ANS["Ansible control node"]
    subgraph Cloud["OpenStack multi-node cloud"]
        CTRL["Controller node"]
        COMP1["Compute node 1"]
        COMP2["Compute node 2"]
        CTRL --- COMP1
        CTRL --- COMP2
    end
    subgraph K8S["Kubernetes cluster on OpenStack instances"]
        MASTER["Control plane"]
        W1["Worker 1"]
        W2["Worker 2"]
        MASTER --- W1
        MASTER --- W2
    end
    subgraph MON["Monitoring"]
        PROM["Prometheus"] --> GRAF["Grafana dashboards"]
    end
    ANS -->|provisions and configures| Cloud
    ANS -->|configures| K8S
    Cloud -->|hosts| K8S
    PROM -. scrapes metrics .-> Cloud
    PROM -. scrapes metrics .-> K8S
```

## ✨ What I built

- **Multi-node OpenStack cloud**: controller and compute nodes working together as one private cloud
- **Automated provisioning and scaling** of instances to use resources efficiently
- **Kubernetes clusters** deployed on top of the OpenStack instances
- **Configuration management with Ansible**: repeatable, idempotent setup of every cluster node
- **Real-time monitoring**: Prometheus collects metrics, Grafana visualizes them, giving full visibility into the infrastructure

## 🔄 Workflow

1. **Prepare** the nodes and networking
2. **Deploy OpenStack** across the controller and compute nodes
3. **Provision instances** automatically for the Kubernetes nodes
4. **Configure the clusters** with Ansible playbooks
5. **Monitor** everything with Prometheus and Grafana, and scale as needed

## 🛠️ Tech stack

| Area | Technologies |
|---|---|
| Private cloud | OpenStack |
| Orchestration | Kubernetes |
| Automation | Ansible |
| Monitoring | Prometheus, Grafana |
| Systems | Linux server administration |

> TODO: add what you actually used, e.g. the OpenStack deployment method and services (Nova, Neutron, Keystone, Glance, Horizon...), the Kubernetes distribution, the CNI plugin, the number of nodes.

## 🎯 Key takeaways

- Building and operating a private cloud from the ground up
- Infrastructure as Code with Ansible for reproducible environments
- Running Kubernetes on top of an IaaS layer
- Observability: metrics collection, dashboards and resource visibility

## 📂 Repository structure

> TODO: only keep this section if you publish the code. Example:

```text
.
├── ansible/          # playbooks and roles
├── openstack/        # deployment configuration
├── kubernetes/       # cluster manifests
├── monitoring/       # Prometheus and Grafana configuration
└── docs/             # screenshots and notes
```

## 📸 Screenshots

> TODO: add 2 or 3 screenshots (OpenStack dashboard, Grafana dashboard, `kubectl get nodes`). Put them in `docs/` and embed them like this:
> `![Grafana](docs/grafana.png)`

---

<div align="center">

### 👤 Author

**Mohamed Khelifi** · Cloud & DevOps Engineer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0a66c2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/khelifimohamed)
[![Portfolio](https://img.shields.io/badge/Portfolio-A7A459?style=for-the-badge&logo=githubpages&logoColor=white)](https://hamoda73.github.io)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Hamoda73)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:ED1944,100:0a0a0a&height=90&section=footer" width="100%" alt="footer" />

</div>
