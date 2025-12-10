# 🚀 Airflow Docker Project  
A fully containerized Apache Airflow environment running with Docker Compose on WSL2 (Ubuntu).  
Includes a complete ETL pipeline, persistent storage, and a production-like Airflow architecture.

---

## 📌 Overview

This project demonstrates how to build and run a professional Apache Airflow environment using Docker.  
It includes:

- Webserver, Scheduler, Worker & Triggerer  
- Redis + Postgres backend  
- Persistent volumes (DAGs, Logs, Data, Plugins, Config)  
- A complete ETL pipeline (extract → transform → load)  
- A clean, reproducible setup for portfolio or real-world deployment

This repository is ideal for:
- Learning Airflow internals  
- Demonstrating ETL / Orchestration skills  
- Building a foundation for bigger Data Engineering projects  

---

## 🧱 Architecture

```txt
              +------------------------+
              |      Webserver         |
              |  (UI & DAG rendering)  |
              +-----------+------------+
                          |
                          v
+-------------+    +------+-------+    +-------------+
|  Triggerer  | -> |  Scheduler   | -> |   Worker     |
+-------------+    +------+-------+    +-------------+
                          |
                          v
                   +--------------+
                   |   Postgres   |
                   |  Metadata DB |
                   +--------------+
                          |
                          v
                   +--------------+
                   |    Redis     |
                   |   Message    |
                   |     Queue    |
                   +--------------+

Volumes:
- dags/ → /opt/airflow/dags
- logs/ → /opt/airflow/logs
- data/ → /opt/airflow/data
- plugins/ → /opt/airflow/plugins
- config/ → /opt/airflow/config