# Database Engines (MariaDB Enterprise Server)

MariaDB Enterprise Server is the hardened, secured, and stabilized foundation of the MariaDB Enterprise Platform, engineered specifically for mission-critical production environments. It features a unique pluggable storage engine architecture, allowing distinct table-level optimization based on workload demands.

## Key Storage Engines

* **InnoDB**  
  The default, general-purpose engine optimized for transactional (OLTP) workloads, featuring row-level locking and robust crash recovery.

* **MyRocks**  
  An LSM-tree-based engine (built on RocksDB) tailored for write-intensive workloads and superior SSD data compression.

* **Spider**  
  A federated engine that provides horizontal sharding, allowing a single MariaDB instance to route queries across multiple backend servers.

* **Aria**  
  A crash-safe successor to MyISAM designed primarily for internal system operations and complex temporary tables.

* **ColumnStore**  
  A specialized engine using columnar storage and Massively Parallel Processing (MPP) for high-performance analytical (OLAP) workloads.

# Analytics (MariaDB ColumnStore)

MariaDB ColumnStore is a specialized columnar storage engine engineered for Online Analytical Processing (OLAP) and big data warehousing. Unlike traditional row-based engines (e.g., InnoDB), it optimizes I/O efficiency, storage footprint, and parallel query execution for large-scale analytical workloads.

## Key Architecture & Features

* **Columnar Storage Architecture**  
  Stores data column-by-column rather than row-by-row, drastically reducing disk I/O by fetching only query-relevant attributes while maximizing compression ratios across uniform data types.

* **Massively Parallel Processing (MPP)**  
  Utilizes a distributed architecture to execute complex analytical queries across multiple compute nodes concurrently.

* **Hybrid Transactional/Analytical Processing (HTAP)**  
  Integrates seamlessly into MariaDB's pluggable engine model, enabling unified HTAP via cross-engine `JOIN` operations between InnoDB (OLTP) and ColumnStore (OLAP).

* **Decoupled Storage & Compute**  
  Integrates natively with S3-compatible cloud object storage to enable cost-effective, elastic scaling of massive datasets.

* **Performance Accelerators**  
  Leverages tools like **MariaDB Query Accelerator** (automatically offloading heavy InnoDB queries to ColumnStore) and **MariaDB Exa** (in-memory MPP analytical processing).

* **Operational Resilience & Ingestion**  
  Optimized for high-speed bulk data ingestion and high availability via MariaDB MaxScale automatic failover and read-scaling.




# Galera Cluster (MariaDB Enterprise Cluster)

MariaDB Galera Cluster is a specialized High Availability (HA) solution providing a virtually synchronous, multi-master (active-active) environment designed for continuous uptime and zero data loss.

## Core Features & Architecture

* **Virtually Synchronous Replication**  
  Uses certification-based replication to apply write-sets across all nodes before finalizing commits, eliminating data loss upon node failure.

* **Multi-Master (Active-Active) Setup**  
  Every node in the cluster actively handles concurrent reads and writes, enabling instant, transparent failover without needing primary-node election delays.

* **Automated Node Provisioning**  
  Simplifies scaling and recovery through automatic synchronization via Incremental State Transfer (IST) or Snapshot State Transfer (SST).

* **InnoDB Integration**  
  Specifically optimized to work alongside the InnoDB storage engine for mission-critical transactional (OLTP) workloads.

* **Ecosystem Integration**  
  Integrates with **MaxScale** (intelligent query routing and read scaling), **MariaDB Kubernetes Operator** (cloud-native orchestration), and **MariaDB Enterprise Backup** (disaster recovery).

## Common Use Cases

* E-commerce platforms and financial transaction systems requiring zero data loss.
* Multi-datacenter, active-active application architectures.
* Mission-critical applications requiring uninterrupted, continuous uptime.
