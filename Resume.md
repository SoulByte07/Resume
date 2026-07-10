---
Soul
DevOps / Backend Engineer
SoulByte07@protonmail.com
linkedin.com/in/SoulByte07 | github.com/SoulByte07
---

## PROFILE SUMMARY
- DevOps & Backend Engineer specializing in resilient, highly available infrastructure and backend systems. Experienced in designing Multi-AZ AWS architectures, building async API services with FastAPI, and automating CI/CD pipelines using GitHub Actions. Focused on local-first cloud testing with LocalStack, containerized deployments, and Infrastructure as Code.

## KEY SKILLS
- Cloud & Infrastructure: AWS (EC2, S3, RDS, VPC, Lambda, CloudFront, CloudWatch), Terraform
- CI/CD & Containers: Jenkins, GitHub Actions, Docker, Podman, Buildah, Docker Compose
- Automation & Scripting: Bash, Python, Linux, Rclone
- Database & Analytics: SQL, PostgreSQL, MySQL, Pandas, PowerBI

---

## PROJECTS

### AWS Scalable Web Architecture (Vocal4Local Migration) § GitHub
> AWS (Route 53, CloudFront, ALB, ASG, RDS Multi-AZ), Terraform, SOPS
- Eliminated 4 critical business risks (downtime, latency, data exposure, traffic surges) by migrating a legacy monolithic application to a 3-tier AWS architecture with Multi-AZ redundancy across 2 Availability Zones and global edge caching.
- Achieved defense-in-depth network security by isolating application and database layers in private subnets behind AWS WAF.
- Improved page load times for international users by serving static assets through CloudFront global edge caching.

### Multi-Cloud Cost Hygiene Automation § GitHub
> LocalStack, Terraform, Python, GitHub Actions, AWS (EC2, EBS, S3, VPC)
- Reduced cloud testing overhead by building a local-first cost detection workflow with LocalStack and Terraform, eliminating the need for real AWS infrastructure during development.
- Reduced risk of orphaned cloud resources by building a Python janitor CLI that detects 3 categories of idle assets (unattached EBS, stopped EC2, unassociated EIPs) with dry-run safety and Protected-tag skip.
- Standardized infrastructure validation across 7 pipeline stages by implementing a GitHub Actions CI/CD workflow automating Terraform checks and janitor reporting.

### RankGuard – Async Transaction Processor & Leaderboard § GitHub
> Python, FastAPI, PostgreSQL, SQLAlchemy 2.0, Alembic, Docker Compose, pytest
- Guaranteed exactly-once transaction processing across 4 database tables by building an async FastAPI backend with idempotency keys and per-user concurrency locks.
- Enabled multi-factor scoring across 3 transaction types (earn, spend, bonus) by implementing materialized rank computation with atomic SQLAlchemy snapshot updates.
- Streamlined deployment and schema consistency by containerizing with Docker Compose and automating PostgreSQL migrations via Alembic, validated by 8 tests.

---

## EDUCATION
B.Tech in Computer Science and Engineering SRKR Engineering College, Andhra Pradesh, India 2023-2027
CGPA: 8.7/10

## CERTIFICATIONS
- AI-Powered Cloud Engineer & AWS Cloud Fundamentals -- EduSkills Foundation
- CyberSecurity & Software Testing -- NPTEL
- Advanced SQL -- HackerRank | Google Project Management -- Coursera
---
