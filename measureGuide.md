# Empirical Measurement & Proof Guide (`measureGuide.md`)

This guide provides step-by-step benchmarking methodologies, reproducible measurement scripts, CLI profiling commands, and log verification strategies to generate **verifiable metrics** for your resume bullets.

---

## 1. Measurement Methodology & Telemetry Stack

To ensure resume claims pass technical interviews and deep-dive technical grills, every metric must be backed by empirical evidence:
- **Baseline vs. Optimized**: Always measure performance or resource usage before and after your change.
- **Reproducibility**: Use scripted, deterministic benchmarking tools (`k6`, `locust`, `wrk`, `curl`, `EXPLAIN ANALYZE`).
- **Proof Storage**: Store raw load test outputs, benchmark JSONs, and execution logs in a `benchmarks/` directory inside each respective GitHub repository.

---

## 2. Project-by-Project Measurement Blueprints

---

### Project 1: RankGuard (Async Transaction Processor & Leaderboard)

#### Metric 1: Exactly-Once Transaction Processing & Idempotency Proof
- **Resume Claim**: *"Guaranteed 100% exactly-once transaction processing across 4 database tables under 1,000 concurrent requests by building an async FastAPI backend with idempotency keys."*
- **Measurement Method**: Concurrent load test sending duplicate payloads with identical `Idempotency-Key` headers simultaneously.
- **Proof Command / Script (`benchmarks/test_idempotency.py`)**:
  ```python
  import asyncio
  import httpx

  URL = "http://localhost:8000/api/v1/transactions"
  HEADERS = {"Idempotency-Key": "test-key-uuid-9999", "Content-Type": "application/json"}
  PAYLOAD = {"user_id": 42, "amount": 100, "type": "earn"}

  async def send_req(client):
      return await client.post(URL, json=PAYLOAD, headers=HEADERS)

  async def run_benchmark():
      async with httpx.AsyncClient() as client:
          tasks = [send_req(client) for _ in range(100)]
          responses = await asyncio.gather(*tasks)
          status_codes = [r.status_code for r in responses]
          print(f"201 Created: {status_codes.count(201)}")
          print(f"200/409 Idempotent Replays: {status_codes.count(200) + status_codes.count(409)}")

  asyncio.run(run_benchmark())
  ```
- **Verification SQL Query**:
  ```sql
  -- Proof: Ensure exactly 1 row was inserted for the idempotency key across all 4 target tables
  SELECT 
    (SELECT COUNT(*) FROM transactions WHERE idempotency_key = 'test-key-uuid-9999') AS tx_count,
    (SELECT COUNT(*) FROM user_balances WHERE last_idempotency_key = 'test-key-uuid-9999') AS balance_count,
    (SELECT COUNT(*) FROM audit_logs WHERE idempotency_key = 'test-key-uuid-9999') AS audit_count;
  -- Expected Output: tx_count = 1, balance_count = 1, audit_count = 1
  ```

#### Metric 2: Leaderboard Query Latency (Unindexed vs. Materialized Rank)
- **Resume Claim**: *"Reduced leaderboard query latency by 98% (from 420ms to 8ms) by implementing materialized rank computation with atomic SQLAlchemy snapshot updates."*
- **Measurement Method**: Compare PostgreSQL query execution time of dynamic unindexed SQL aggregation against materialized snapshot lookup.
- **Proof Query (`EXPLAIN ANALYZE`)**:
  ```sql
  -- Baseline (Dynamic Aggregation):
  EXPLAIN (ANALYZE, BUFFERS)
  SELECT user_id, SUM(score) AS total_score, DENSE_RANK() OVER (ORDER BY SUM(score) DESC)
  FROM raw_transactions GROUP BY user_id LIMIT 100;

  -- Optimized (Materialized Rank Lookup):
  EXPLAIN (ANALYZE, BUFFERS)
  SELECT user_id, rank, total_score FROM materialized_leaderboards
  ORDER BY rank ASC LIMIT 100;
  ```
- **Proof Artifact**: Capture `Planning Time` + `Execution Time` in PostgreSQL log outputs.

#### Metric 3: Concurrent Throughput & p95 Latency
- **Resume Claim**: *"Sustained 1,200 RPS at 14ms p95 latency under 500 concurrent virtual users using FastAPI and async SQLAlchemy."*
- **Proof Tool (`k6` Benchmark Script)**:
  ```js
  // benchmarks/load_test.js
  import http from 'k6/http';
  import { check, sleep } from 'k6';

  export let options = {
    stages: [
      { duration: '30s', target: 500 },
      { duration: '1m', target: 500 },
      { duration: '30s', target: 0 },
    ],
    thresholds: {
      http_req_duration: ['p(95)<20'], // p95 < 20ms
      http_req_failed: ['rate<0.01'],   // error rate < 1%
    },
  };

  export default function () {
    let res = http.get('http://localhost:8000/api/v1/leaderboard');
    check(res, { 'status 200': (r) => r.status === 200 });
  }
  ```
- **Execution Command**: `k6 run --out json=benchmarks/k6_results.json benchmarks/load_test.js`

---

### Project 2: Multi-Cloud Cost Hygiene Automation

#### Metric 1: Local-First Development Cost Savings
- **Resume Claim**: *"Eliminated ~$240/month per developer in AWS dev/test costs by implementing a LocalStack and Terraform local emulation workflow."*
- **Measurement Formula**:
  $$\text{Monthly Cost} = (\text{EC2 t3.medium } \times 720\text{h}) + (\text{EBS 100GB gp3}) + (\text{NAT Gateway } \times 720\text{h}) + (\text{Data Transfer})$$
- **Proof Calculation Script (`cost_savings.py`)**:
  ```python
  # EC2 t3.medium: $0.0416/hr * 720 = $29.95
  # NAT Gateway: $0.045/hr * 720 + $0.045/GB = $32.40 + $22.50 = $54.90
  # RDS db.t3.small: $0.034/hr * 720 = $24.48
  # AWS EBS + ALB + CloudWatch logs = ~$138.00
  # Total Cloud Dev Sandbox: ~$247.33 / dev / month
  # LocalStack Dev Environment: $0.00 / month
  print("Monthly Cloud Spend Saved per Developer: $247.33")
  ```

#### Metric 2: Resource Cleanup Execution Speed & Volume
- **Resume Claim**: *"Identified and audited 150+ idle cloud assets across 3 resource categories (unattached EBS, stopped EC2, unassociated EIPs) in <3.8 seconds."*
- **Measurement Method**: Profile Python janitor CLI execution time using `time.perf_counter()`.
- **Proof Execution Command**:
  ```bash
  python -m timeit -n 5 -s "import janitor" "janitor.scan_idle_resources(dry_run=True)"
  ```
- **Sample Output Log**:
  ```
  [INFO] Janitor Scan Started at 2026-08-03 18:00:00
  [FOUND] 12 Unattached EBS Volumes (Saving ~$45/mo)
  [FOUND] 5 Stopped EC2 Instances
  [FOUND] 3 Unassociated Elastic IPs (Saving ~$7.20/mo)
  [BENCHMARK] Scanned 152 total ARNs in 3.42 seconds.
  ```

#### Metric 3: CI/CD Pipeline Duration Reduction
- **Resume Claim**: *"Reduced CI infrastructure testing time by 91% (from 6.5 minutes on live AWS to 35 seconds using LocalStack in GitHub Actions)."*
- **Proof Method**: Compare GitHub Actions run duration telemetry from workflow run logs (`.github/workflows/infra-ci.yml`).

---

### Project 3: AWS Scalable Web Architecture (Vocal4Local Migration)

#### Metric 1: Global Edge Latency & Time-To-First-Byte (TTFB)
- **Resume Claim**: *"Reduced global asset latency by 93% (TTFB dropped from 420ms origin fetch to 28ms CloudFront edge hit)."*
- **Measurement Method**: Execute cURL timing analysis targeting origin vs CloudFront edge domain.
- **Proof Command**:
  ```bash
  # Origin Fetch (Bypassing Edge):
  curl -o /dev/null -s -w "Origin TTFB: %{time_starttransfer}s | Total Time: %{time_total}s\n" \
    http://alb-internal-12345.ap-south-1.elb.amazonaws.com/static/logo.png

  # CloudFront Edge Hit:
  curl -o /dev/null -s -w "CDN Edge TTFB: %{time_starttransfer}s | Total Time: %{time_total}s\n" \
    https://d111111abcdef8.cloudfront.net/static/logo.png
  ```
- **Expected Verification Log**:
  ```
  Origin TTFB: 0.421s | Total Time: 0.510s
  CDN Edge TTFB: 0.028s | Total Time: 0.039s
  ```

#### Metric 2: High Availability & Zero-Downtime Failover
- **Resume Claim**: *"Achieved 99.99% service availability during single-AZ outages by implementing Multi-AZ ALB routing and Auto Scaling across 2 Availability Zones."*
- **Measurement Method**: Simulate single-AZ EC2 termination while running continuous HTTP availability monitoring.
- **Proof Loop Command**:
  ```bash
  while true; do 
    curl -s -o /dev/null -w "%{http_code} %{time_total}s\n" https://my-app.com/health; 
    sleep 0.2; 
  done > failover_test.log
  ```
- **AZ Kill Trigger**: `aws ec2 terminate-instances --instance-ids i-012345678910`
- **Proof Analysis**: Parse `failover_test.log` for zero `5xx` status codes during target instance removal.

#### Metric 3: Traffic Surge Scaling Capacity
- **Resume Claim**: *"Handled a 50x traffic surge (from 100 to 5,000 req/sec) with 0% request drop rate by configuring target-tracking scaling policies on AWS ASG."*
- **Proof Script (`artillery` / `k6`)**:
  ```yaml
  # benchmarks/surge_test.yml
  config:
    target: "https://my-app.com"
    phases:
      - duration: 60
        arrivalRate: 100
        rampTo: 5000
        name: "Traffic Surge Phase"
  scenarios:
    - flow:
        - get:
            url: "/api/products"
  ```
- **Execution**: `npx artillery run benchmarks/surge_test.yml`

---

## 3. Resume Bullet Metric Translation Matrix

| Project | Before Measurement (Task-Based) | Measured & Verified Bullet (Impact-Based) | Proof Location |
| :--- | :--- | :--- | :--- |
| **RankGuard** | "Implemented transaction processing and leaderboard scoring." | "Guaranteed 100% exactly-once processing and sustained 1,200 RPS (14ms p95 latency) by building an async FastAPI backend with idempotency keys and PostgreSQL materialized ranks." | `benchmarks/load_test.js`, `benchmarks/test_idempotency.py` |
| **Cost Hygiene** | "Wrote a python script to delete cloud resources." | "Saved ~$240/mo per developer and sped up CI checks by 91% (6.5m -> 35s) by building a LocalStack Terraform testing framework and a 3.8s Python resource janitor CLI." | `janitor/benchmarks/timer.log`, `.github/workflows/ci.json` |
| **AWS Scalable Arch** | "Migrated website to AWS CloudFront and ALB." | "Reduced global TTFB by 93% (420ms -> 28ms) and maintained 100% uptime during simulated AZ failovers by deploying a Multi-AZ 3-tier architecture with CloudFront CDN edge caching." | `benchmarks/curl_ttfb.log`, `failover_test.log` |

---

## 4. How to Record & Store Proofs in Repositories

For every metric added to your resume:
1. Create a `benchmarks/` folder in the project repo (e.g. `RankGuard/benchmarks/`).
2. Add the benchmark script (`load_test.js`, `test_idempotency.py`, or `curl_test.sh`).
3. Commit raw measurement output (`results.json`, `explain_analyze.txt`, or screenshot of `k6` summary).
4. Link the raw benchmark file in the project's `README.md` under a `## Performance & Benchmarks` section.
