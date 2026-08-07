# 🚀 Alternative roadmap.sh Projects

This document provides officially recognized project ideas from [roadmap.sh/projects](https://roadmap.sh/projects) as alternatives to the custom Mini-Exercises and Mega-Projects listed in the primary `roadmap.md`. These projects are designed to validate the exact same skills while following community-standard project specifications.

---

## 🔹 Phase 1: Go Foundations, Concurrency & gRPC

### Original Mini-Exercises
*   Slice vs Map Benchmarker
*   Bounded Worker Queue
*   Protobuf vs JSON Payload Comparison

### 🛠️ roadmap.sh Alternative Projects
1.  **[Task Tracker CLI](https://roadmap.sh/projects/task-tracker)**: 
    *   **Goal:** Learn basic Go file I/O, structs, arrays/slices, and CLI argument parsing. 
    *   **Why it works:** Replaces the Slice/Map benchmarker by focusing on core language mechanics and JSON file persistence without external dependencies.
2.  **[GitHub User Activity CLI](https://roadmap.sh/projects/github-user-activity)**:
    *   **Goal:** Learn Go HTTP clients, JSON parsing, and handling external APIs.
    *   **Why it works:** Builds on the Task Tracker by introducing networking.
3.  **[Broadcast Server](https://roadmap.sh/projects/broadcast-server)**:
    *   **Goal:** Master Go concurrency (goroutines, channels) and raw TCP connections.
    *   **Why it works:** Directly replaces the "Bounded Worker Queue" and "Protobuf vs JSON" exercises by forcing you to handle concurrent client states and binary/text network boundaries.

---

## 🔹 Phase 2: High-Performance Storage & Event Streaming

### Original Mini-Exercises
*   Postgres Query Optimizer Benchmark
*   Redis Lua Atomic Rate Limiter
*   Kafka Producer & Idempotent Consumer

### 🛠️ roadmap.sh Alternative Projects
1.  **[Expense Tracker API](https://roadmap.sh/projects/expense-tracker-api)** (PostgreSQL Focus):
    *   **Goal:** Build a robust API with advanced SQL queries, filtering, and aggregations.
    *   **Why it works:** Serves as a great playground for `EXPLAIN ANALYZE` and B-Tree indexing on filtering parameters (like dates and categories).
2.  **[URL Shortener API](https://roadmap.sh/projects/url-shortener)** (Redis Focus):
    *   **Goal:** Implement fast data retrieval and caching layers.
    *   **Why it works:** Replaces the Lua Rate Limiter exercise by applying Redis for caching, TTL expiration, and handling high-read volumes.
3.  **[Real-time Chat Application](https://roadmap.sh/projects/realtime-chat-app)** (Kafka / Pub-Sub Focus):
    *   **Goal:** Handle real-time messaging and state.
    *   **Why it works:** Swap standard WebSockets with Kafka (or Redis Pub/Sub) to act as the message broker between chat instances, proving event-streaming competence.

---

## 🏆 Milestone 1: Backend Mega-Project

### Original Project
*   `StreamPulse` (High-Throughput Ingestion & Transaction Engine)

### 🌟 roadmap.sh Alternative Project
*   **[E-Commerce API](https://roadmap.sh/projects/ecommerce-api)**
    *   **Integration Goal:** Synthesize Phase 1 and 2 into a distributed architecture.
    *   **Execution:** Instead of a simple monolith, build it using Go microservices (e.g., Users, Products, Orders). Use **gRPC** for internal service communication, **PostgreSQL** (partitioned by order dates) for storage, **Redis** for cart caching and rate-limiting, and **Kafka** to handle order-creation events asynchronously.

---

## 🔹 Phase 3: AWS Core Infrastructure & Terraform IaC

### Original Mini-Exercises
*   LocalStack AWS Test Script
*   Terraform VPC Module

### 🛠️ roadmap.sh Alternative Projects
1.  **[Server Performance Stats CLI](https://roadmap.sh/projects/server-stats)**:
    *   **Goal:** Understand underlying Linux/Cloud compute metrics (CPU, RAM, Disk).
    *   **Why it works:** A great prerequisite before provisioning cloud servers, teaching you what to monitor on your EC2 instances.
2.  **Deploying a Personal Blog / API on AWS** (Manual to IaC):
    *   **Goal:** Provision VPC, EC2, Security Groups, and RDS.
    *   **Why it works:** Instead of abstract Terraform modules, take the E-Commerce API from Milestone 1 and write Terraform scripts to deploy its underlying infrastructure (VPC, Subnets, EC2/ALB) onto AWS or LocalStack.

---

## 🔹 Phase 4: Kubernetes & Full-Stack Telemetry

### Original Mini-Exercises
*   Single-Service Minikube Deployment
*   OTel Prometheus Exporter Script

### 🛠️ roadmap.sh Alternative Projects
1.  **[Nginx Log Analyser](https://roadmap.sh/projects/nginx-log-analyser)**:
    *   **Goal:** Parse, aggregate, and report on log data.
    *   **Why it works:** Teaches the fundamentals of log aggregation before moving to complex OpenTelemetry and Grafana setups.
2.  **Kubernetes Cluster Deployment**:
    *   **Goal:** Orchestrate containers.
    *   **Why it works:** Write custom Helm charts and K8s manifests for the E-Commerce API (Milestone 1), running it locally on Minikube or Kind before pushing to the cloud.

---

## 🏆 Milestone 2: Cloud-Native Mega-Project

### Original Project
*   `CloudPulse-Platform`

### 🌟 roadmap.sh Alternative Project
*   **Full CI/CD & Monitoring Stack**
    *   **Integration Goal:** Deploy the E-Commerce Microservices architecture to AWS EKS using Terraform. Set up a GitHub Actions pipeline that builds Docker images and updates the cluster. Finally, attach Prometheus, Grafana, and Jaeger to the cluster to monitor the distributed traces between the cart, user, and order services.

---

## 🔹 Phase 5 & Milestone 3: Resiliency, Security & Production Hardening

### Original Projects
*   Faulty Proxy Retry, Secrets Fetcher
*   `Enterprise-Resilience-Gateway`

### 🛠️ roadmap.sh Alternative Project
*   **[Build your own Rate Limiter](https://roadmap.sh/projects/rate-limiter)** / **Custom API Gateway**
    *   **Integration Goal:** Build an edge proxy in Go that sits in front of your E-Commerce K8s cluster. 
    *   **Execution:** Have this proxy fetch JWT secrets from AWS Secrets Manager dynamically. Implement Circuit Breakers for when the Order service goes down, and use Exponential Backoff for retries. This perfectly encapsulates production hardening in one custom-built infrastructure component.
