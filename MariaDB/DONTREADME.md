# MariaDB Resources

Welcome to my personal knowledge base for MariaDB. This repository serves as an in-depth resource for architecting, deploying, and managing MariaDB ecosystems at scale. It focuses on the MariaDB Enterprise Platform, emphasizing high availability, performance tuning, and automated operations.

## Repository Structure

* **MariaDB Platform**  
  Focuses on the integrated database solution that combines transactional, analytical, and hybrid (HTAP) workloads.  
  *Key Topics:* Unified data platform architecture, security best practices (TDE, Database Firewall), and DoD STIG certification.

* **Server**  
  Deep dives into the core MariaDB Enterprise and Community Server engines.  
  *Key Topics:* Storage engines like MyRocks (LSM-tree for high write performance) and Spider (horizontal sharding), pluggable architecture, and advanced SQL querying.

* **MaxScale**  
  Documentation on the advanced database proxy used for traffic management.  
  *Key Topics:* Load balancing, query routing, automated failover, and simplifying administrative tasks.  
  *SRE Note:* The MaxScale documentation alone covers over 5,800 pages of configuration logic.

* **Analytics**  
  Technical guides for MariaDB ColumnStore.  
  *Key Topics:* Distributed columnar storage, Massively Parallel Processing (MPP) for OLAP workloads, and S3-compatible object storage integration.

* **Galera Cluster**  
  Focuses on High Availability (HA) through synchronous replication.  
  *Key Topics:* Active-active multi-master clustering, ensuring no data loss, and maintaining cluster health.

* **Connectors**  
  The drivers required for application-tier connectivity.  
  *Key Topics:* Official support for Java (JDBC), C, C++, Python (DB API 2.0), Node.js, and ODBC.

* **Tools**  
  Operations and automation utilities.  
  *Key Topics:* MariaDB Enterprise Kubernetes Operator for cloud-native orchestration, Enterprise Manager for fleet observability, and AI RAG for semantic search capabilities.

* **MariaDB Cloud**  
  Documentation for cloud-native deployments.  
  *Key Topics:* Managed service configurations, public/private cloud deployment strategies, and the MCP Server for AI assistant interfaces.

* **Release Notes**  
  Version-specific tracking for security patches and feature updates.  
  *Key Topics:* Lifecycle management for Enterprise Server 10.6, 11.4, and rolling releases like 12.x/13.x.

* **General Resources**  
  Broad ecosystem links and offline study materials.  
  *Key Topics:* Links to the Developer Hub, MariaDB Blog, and massive Offline PDF Snapshots (over 19,000 total pages across all products).

---

## Quick Reference

* **Authoritative Source:** mariadb.com/docs
* **Massive Deep Dive:** The MariaDB Server PDF snapshot contains 6,166 pages of architectural detail.
* **Best Practices:** Dedicated production servers, structured change management, and regular, tested backups are mandatory for robust deployments.
