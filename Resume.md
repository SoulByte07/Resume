---
Bokka Mohan Kiran
DevOps / Backend Engineer
mohankiran07@protonmail.com
linkedin.com/in/mohankiran07 | github.com/SoulByte07
---

## PROFILE SUMMARY
- DevOps & Cloud Engineer specializing in resilient, highly available infrastructure. Proven experience designing Multi-AZ AWS architectures, automating serverless workflows with Lambda, and building robust CI/CD pipelines using GitHub Actions. Focused on implementing Infrastructure as Code (IaC) to streamline deployments and optimize system reliability.

## KEY SKILLS
- Cloud & Infrastructure: AWS (EC2, S3, RDS, VPC, Lambda, CloudFront, CloudWatch), Terraform
- CI/CD & Containers: Jenkins, GitHub Actions, Docker, Podman, Buildah, Docker Compose
- Automation & Scripting: Bash, Python, Linux, Rclone
- Database & Analytics: SQL, PostgreSQL, MySQL, Pandas, PowerBI

---

## PROJECTS

### AWS Scalable Web Architecture (Vocal4Local Migration) § GitHub
> AWS (Route 53, CloudFront, ALB, ASG, RDS Multi-AZ), Terraform, SOPS
- Migrated a legacy monolithic application to a 3-tier AWS architecture using Terraform, addressing 4 critical risks (single-point-of-failure, latency, security, scalability) with Multi-AZ redundancy across 2 Availability Zones and global edge caching.
- Secured application and database logic using private subnets and AWS WAF, achieving robust network isolation and edge protection.
- Implemented CloudFront global edge caching to optimize performance and reduce latency for international customers.

### Multi-Cloud Cost Hygiene Automation § GitHub
> LocalStack, Terraform, Python, GitHub Actions, AWS (EC2, EBS, S3, VPC)
- Built a local-first cloud cost detection workflow using LocalStack emulation and Terraform to provision baseline AWS infrastructure for identifying cost-wasting resources.
- Developed a Python janitor CLI to discover unattached EBS volumes, stopped EC2 instances, and unassociated Elastic IPs across 3 resource categories with dry-run and safe deletion modes.
- Implemented a 7-stage CI/CD pipeline via GitHub Actions automating LocalStack provisioning, Terraform validation, and janitor dry-run reporting with artifact uploads.

### RankGuard – Async Transaction Processor & Leaderboard § GitHub
> Python, FastAPI, PostgreSQL, SQLAlchemy 2.0, Alembic, Docker Compose, pytest
- Built an async FastAPI backend across 4 database tables with idempotent transaction processing and per-user asyncio.Lock concurrency control for exactly-once guarantees.
- Implemented a multi-factor ranking leaderboard with 3 transaction types (earn, spend, bonus) and materialised score computation and atomic snapshot updates via SQLAlchemy 2.0 async sessions.
- Containerized the application with Docker Compose, integrated Alembic for PostgreSQL schema migrations, and validated the system with 8 automated test cases.

### IPL Cricket Data Analytics & Visualization § GitHub
> Python (Pandas), Jupyter Notebook, PowerBI
- Performed exploratory data analysis on IPL datasets using Python (Pandas), identifying key performance trends and player statistics for data-driven insights.
- Built interactive PowerBI dashboards to visualize match outcomes, enhancing stakeholder reporting and visual storytelling.

---

## EDUCATION
B.Tech in Computer Science and Engineering SRKR Engineering College, Andhra Pradesh, India 2023-2027
CGPA: 8.7/10

## CERTIFICATIONS
- AI-Powered Cloud Engineer & AWS Cloud Fundamentals -- EduSkills Foundation
- CyberSecurity & Software Testing -- NPTEL
- Advanced SQL -- HackerRank | Google Project Management -- Coursera
---
