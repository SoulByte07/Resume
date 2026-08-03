---
Soul
Backend Engineer
SoulByte07@protonmail.com
linkedin.com/in/SoulByte07 | github.com/SoulByte07
---

## PROFILE SUMMARY
- Backend Engineer specializing in resilient, highly available infrastructure and backend systems. Experienced in designing Multi-AZ AWS architectures, building async API services with FastAPI, and automating CI/CD pipelines using GitHub Actions. Focused on local-first cloud testing with LocalStack, containerized deployments, and Infrastructure as Code.


## KEY SKILLS
- Cloud & Infrastructure: Terraform, AWS (EC2, VPC, S3, RDS, Lambda, CloudFront, CloudWatch)
- Programming Languages & Tools: Python, Bash, Java, Go, Linux, Rclone, OOP, REST API
- CI/CD & Containers: GitHub Actions, Docker, Docker Compose, Jenkins, Podman, Buildah
- Database & Analytics: PostgreSQL, SQL, MySQL, Pandas, PowerBI

---

## PROJECTS

### AWS Scalable Web Architecture (Vocal4Local Migration) (https://github.com/SoulByte07/AWS-Scalable-Web-Architecture.git)
> AWS (Route 53, CloudFront, ALB, ASG, RDS Multi-AZ), Terraform, SOPS
- Eliminated 4 critical business risks (downtime, latency, data exposure, traffic surges) by migrating a legacy monolithic application to a 3-tier AWS architecture with Multi-AZ redundancy across 2 Availability Zones and global edge caching.
- Isolated application and database tiers across 3 private subnets behind AWS WAF, achieving defense-in-depth network segmentation.
- Reduced page load times for global users by serving static assets through CloudFront edge caching across 400+ points of presence.

### Multi-Cloud Cost Hygiene Automation (https://github.com/SoulByte07/Multi-Cloud-Cost-Hygiene-Automation)
> LocalStack, Terraform, Python, GitHub Actions, AWS (EC2, EBS, S3, VPC)
- Eliminated recurring cloud infrastructure costs during development by building a local-first cost detection workflow with LocalStack and Terraform, removing dependency on real AWS environments.
- Reduced risk of orphaned cloud resources by building a Python janitor CLI that detects 3 categories of idle assets (unattached EBS, stopped EC2, unassociated EIPs) with dry-run safety and Protected-tag skip.
- Standardized infrastructure validation across 7 pipeline stages by implementing a GitHub Actions CI/CD workflow automating Terraform checks and janitor reporting.

### RankGuard – Async Transaction Processor & Leaderboard (https://github.com/SoulByte07/RankGuard.git)
> Python, FastAPI, PostgreSQL, SQLAlchemy 2.0, Alembic, Docker Compose, pytest
- Guaranteed exactly-once transaction processing across 4 database tables by building an async FastAPI backend with idempotency keys and per-user concurrency locks.
- Enabled multi-factor scoring across 3 transaction types (earn, spend, bonus) by implementing materialized rank computation with atomic SQLAlchemy snapshot updates.
- Streamlined deployment and schema consistency by containerizing with Docker Compose and automating PostgreSQL migrations via Alembic, validated by 8 tests.

---

## EDUCATION
B.Tech in Computer Science and Engineering ABC Engineering College, Andhra Pradesh, India 2023-2027
CGPA: 8.5/10

## CERTIFICATIONS
- AI-Powered Cloud Engineer & AWS Cloud Fundamentals -- EduSkills Foundation
- CyberSecurity & Software Testing -- NPTEL
- Advanced SQL -- HackerRank | Google Project Management -- Coursera

## ACHIEVEMENTS
- TCS Digital Systems Engineer Offer: Secured TCS Digital Systems Engineer placement offer through competitive on-campus recruitment.
- NPTEL Gold Medalist -- Cyber Security: Awarded Elite + Gold Medal certification by NPTEL/IIT in Cyber Security (Top Percentile).
---

