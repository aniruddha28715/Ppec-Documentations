Tools & Proxies 

MariaDB MAxScale
MariaDB MaxScale is an advanced database proxy, intelligent query router, and load balancer designed to sit between client applications and backend MariaDB servers.

## Traffic Flow Diagram

```mermaid
flowchart TD
    App[Client Applications] -->|1. Client Connection Point| Proxy

    subgraph Proxy ["MariaDB MaxScale Proxy Layer"]
        B1[1. Connection Receipt & Auth] --> B2[2. Traffic Analysis & Security Firewall]
        B2 -->|Pass Filtered Queries| B3{3. SQL Query Parser & Router}
        
        B3 -->|Write Operations / DDL / DML| B4[Primary / Write Router]
        B3 -->|Read Operations / SELECTs| B5[Read-Only Load Balancer]
        
        B6((5. Continuous Health Monitor)) -.->|Real-time Protocol Polling| Backend
    end

    subgraph Backend ["Backend MariaDB Ecosystem"]
        B4 -->|Direct Writes| Master[(Primary Server / Active Node)]
        B5 -->|Balance Reads| Replicas[(Read Replicas / Galera Nodes)]
    end

    B6 -.->|6. Automatic Failover & Re-routing| Master
```


# MaxScale Core Objectives ("Max Goal")

The primary objective of MariaDB MaxScale is to simplify application development and database administration by providing a single, intelligent entry point for complex database topologies.

## Core Goals & Capabilities

* **Continuous High Availability**  
  Ensures mission-critical applications remain accessible during hardware failures or routine maintenance through automated failover and cluster reconfiguration.

* **Elastic Scalability**  
  Enables scaling read and write operations across multiple nodes without requiring any changes to application code.

* **Hardened Security**  
  Serves as a centralized security layer that protects the entire database fleet using database firewalls and query filtering.

* **Operational Validation**  
  Facilitates safe database upgrades and troubleshooting using tools like Workload Capture and Replay (WCAR) and the Diff Router to compare server behavior across versions.


# MariaDB Enterprise Manager Overview

MariaDB Enterprise Manager is a fleet-wide management and observability solution within the MariaDB Enterprise Platform. It acts as a single-pane-of-glass interface to monitor transactional, analytical, and hybrid workloads across an enterprise's entire database infrastructure.

---

## Strategic Role Across Tools & Proxies

* **Enterprise Manager (Observability):** Monitors overall health, query performance, and operational diagnostics across all clusters and instances.
* **MaxScale (Traffic Management):** Acts as an active proxy layer handling query routing, load balancing, and failover.
* **Kubernetes Operator (Automation):** Automates containerized lifecycle tasks like provisioning, scaling, and self-healing.

---

## Operational Workflow

```mermaid
flowchart TD
    subgraph Observability ["Observability Layer"]
        EM["MariaDB Enterprise Manager\n(Fleet Monitoring & Diagnostics)"]
    end

    subgraph Operations ["Traffic & Lifecycle Layer"]
        MS["MariaDB MaxScale\n(Traffic Routing & Failover)"]
        K8s["Kubernetes Operator\n(Provisioning & Self-Healing)"]
    end

    subgraph DataFleet ["Database Infrastructure Layer"]
        DB1[(Transactional / InnoDB)]
        DB2[(Analytical / ColumnStore)]
        DB3[(HA / Galera Cluster)]
    end

    MS -->|Active Traffic Management| DataFleet
    K8s -->|Lifecycle Orchestration| DataFleet
    DataFleet -.->|Metrics & Audit Data| EM
    EM -.->|Visibility for SREs & DBAs| Operations

```

