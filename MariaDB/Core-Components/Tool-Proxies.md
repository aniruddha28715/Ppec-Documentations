Tools & Proxies 

MariaDB MAxScale
MariaDB MaxScale is an advanced database proxy, intelligent query router, and load balancer designed to sit between client applications and backend MariaDB servers.

## Traffic Flow Diagram

┌───────────────────────────────────────────────────────────────────────────────┐
│                              Observability Layer                              │
│         [ MariaDB Enterprise Manager (Fleet Monitoring & Diagnostics) ]        │
└───────────────────────────────────────▲───────────────────────────────────────┘
                                        │
                         Metrics &      │ Visibility for
                        Audit Data      │ SREs & DBAs
                                        │
┌───────────────────────────────────────┴───────────────────────────────────────┐
│                           Traffic & Lifecycle Layer                           │
│        [ MaxScale (Traffic Routing) ]   [ Kubernetes Operator (Lifecycle) ]   │
└───────────────────┬───────────────────────────────────────┬───────────────────┘
                    │ Active Traffic                        │ Lifecycle
                    │ Management                            │ Orchestration
                    ▼                                       ▼
┌───────────────────────────────────────────────────────────────────────────────┐
│                         Database Infrastructure Layer                         │
│   [ Transactional / InnoDB ]  [ Analytical / ColumnStore ]  [ HA / Galera ]   │
└───────────────────────────────────────────────────────────────────────────────┘

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

[ Client Applications ]
           │
           │ 1. Connection Point
           ▼
┌───────────────────────────────────────────────────────────────────────────────┐
│                        MariaDB MaxScale Proxy Layer                           │
│                                                                               │
│ 1. [ Connection Receipt & Auth ]                                              │
│               │                                                               │
│               ▼                                                               │
│ 2. [ Traffic Analysis & Security Firewall ]                                   │
│               │                                                               │
│               ▼ (Filtered Queries)                                            │
│ 3. [ SQL Query Parser & Router ]                                              │
│        ├── Writes (DDL/DML) ──► 4. [ Primary / Write Router ]                  │
│        └── Reads (SELECTs)  ──► 5. [ Read-Only Load Balancer ]                │
│                                                                               │
│ 5. [ Continuous Health Monitor ] ─── (Real-time Protocol Polling) ───┐        │
└──────────────────┬─────────────────────────────────┬─────────────────┼────────┘
                   │ Direct                          │ Balance         │
                   │ Writes                          │ Reads           │
                   ▼                                 ▼                 │
┌──────────────────────────────────────────────────────────────────────┴────────┐
│                          Backend MariaDB Ecosystem                            │
│    [ Primary Server / Active Node ]      [ Read Replicas / Galera Nodes ]     │
│                   ▲                                                           │
└───────────────────┼───────────────────────────────────────────────────────────┘
                    └──────────── (6. Automatic Failover) ─────────────────────┘

# AI & Analytics Innovation (MariaDB Platform)

The MariaDB Enterprise Platform integrates AI operations and high-speed analytical extensions directly into its core architecture, enabling transactional, analytical, vector, and generative AI workloads within a single environment.

---

## Architectural Workflow

```text
┌────────────────────────────────────────────────────────────────────────┐
│                        AI & Analytical Interfaces                      │
│     [ MariaDB AI RAG ]    [ MCP Server ]    [ Vector Search ]          │
└───────────────────┬────────────────────────────────┬───────────────────┘
                    │                                │
                    ▼                                ▼
┌────────────────────────────────────────────────────────────────────────┐
│                       Accelerated Analytics Layer                      │
│            [ MariaDB Exa ]    [ MariaDB Query Accelerator ]            │
└───────────────────┬────────────────────────────────┬───────────────────┘
                    │                                │
                    ▼                                ▼
┌────────────────────────────────────────────────────────────────────────┐
│                             Core Engines                               │
│        [ Enterprise Server ]  │  [ ColumnStore ]  │  [ MaxScale ]      │
└────────────────────────────────────────────────────────────────────────┘

## Key Capabilities

* **MariaDB AI RAG**  
  Enterprise Retrieval-Augmented Generation solution enabling semantic search, natural language generation, and AI document processing.

* **MariaDB MCP Server**  
  Secure interface managing interactions between external AI assistants and the MariaDB data ecosystem.

* **Vector Embedded Search**  
  Native vector search capabilities embedded directly into the database environment.

* **MariaDB Exa**  
  High-performance, in-memory analytical database leveraging Massively Parallel Processing (MPP) for large-scale SQL queries.

* **MariaDB Query Accelerator**  
  Offloads heavy transactional overhead by automatically rerouting complex InnoDB queries to ColumnStore.

---

## Core Engine Integration

* **Enterprise Server:** Hardened foundation providing ACID compliance, data persistence, and DoD STIG certification.
* **MaxScale:** Intelligent proxy layer securing AI workloads via database firewalls and load balancing.
* **ColumnStore:** Distributed columnar engine powering the analytics for MariaDB Exa and Query Accelerator.

