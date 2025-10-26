# ⚡ Optimization on WordPress Using k6

### 👨‍💻 Name: Aqief Daniel Bin Muhammad Nazir  
### 🎓 Student ID: 2024125923  
### 🧾 Course: 2510-ITT440 – Individual Assignment  
### 🧠 Lecturer: M3CS2554A  

---

## 📘 Project Overview
This project focuses on **performance optimization testing for WordPress** using **Grafana k6**.  
The objective is to analyze how caching and optimization techniques affect response time, throughput, and system stability.  
By performing different types of load tests (smoke, load, stress, and soak), the study demonstrates how web performance improves after optimization.

---

## 🧰 Test Environment

| Component | Details |
|------------|----------|
| **Platform** | Localhost using XAMPP |
| **Server** | Apache 2.4.58 (PHP 8.0.30) |
| **Database** | MySQL 10.4 |
| **Tool** | Grafana k6 v1.3.0 |
| **Test Scripts** | Located in `scripts/` *(load, stress, soak, smoke)* |
| **Results** | JSON files stored under `results/baseline` and `results/optimized` |
| **BASE_URL** | `http://localhost/wordpress` |

---

## 🧪 Test Design

| Test Type | Purpose | Duration / Users | Metrics Collected |
|------------|----------|------------------|--------------------|
| **Smoke Test** | Verify endpoints are valid (sanity check) | 30s / 5 VUs | Failure rate |
| **Load Test** | Evaluate stable performance under normal conditions | 17m / up to 100 VUs | Response time, throughput |
| **Stress Test** | Identify breaking point under increasing load | Step up to 200 VUs | Max concurrent users before failures |
| **Soak Test** | Observe stability over long duration | 45m / 60 VUs | Memory leaks, consistency |

---

## 🌐 Test Links (Endpoints Tested)

| Endpoint | Description | Status |
|-----------|--------------|--------|
| 🔹 [`/index.php`](http://localhost/wordpress/index.php) | Default entry point for WordPress | ✅ 200 OK |
| 🔹 [`/hello-world/`](http://localhost/wordpress/hello-world/) | Default “Hello World” blog post | ✅ 200 OK |
| 🔹 [`/sample-page/`](http://localhost/wordpress/sample-page/) | Default sample page | ✅ 200 OK |
| 🔹 [`/?s=test`](http://localhost/wordpress/?s=test) | Search query for “test” keyword | ✅ 200 OK |

> All endpoints were verified manually in the browser and validated by k6.

---

## 📊 Performance Results and Analysis

### 🧩 Smoke Test Summary

| Metric | Result | Observation |
|---------|--------|--------------|
| Endpoints Tested | 4 (`index.php`, `hello-world/`, `sample-page/`, `?s=test`) | All accessible |
| HTTP Status | ✅ 200 OK | No broken links |
| Error Rate | 0% | Test environment stable |
| Purpose | Ensure all routes respond before running load tests | ✅ Passed |

> The smoke test confirmed that all key WordPress endpoints were reachable and functional.  
> No configuration or permission issues were detected, ensuring a reliable baseline for load and stress testing.

---

### ⚙️ Load Test (Normal Traffic Performance)

| Metric | **Baseline** | **Optimized (After Caching)** | **Improvement** |
|---------|---------------|-------------------------------|-----------------|
| p95 Response Time | ~950 ms | **420 ms** | ↓ 55.8% |
| Average Response Time | ~730 ms | **340 ms** | ↓ 53.4% |
| Requests/sec (Throughput) | ~4.9 | **9.3** | ↑ 89.8% |
| Error Rate | 3% | **0%** | ✅ Eliminated |

> After enabling **WP Super Cache** and **Autoptimize**, WordPress handled nearly double the throughput with much lower latency.  
> Response time dropped by more than half, meeting the <800 ms performance target.

---

### 💣 Stress Test (Scalability & Breaking Point)

| Metric | **Baseline** | **Optimized** | **Observation** |
|---------|--------------|---------------|-----------------|
| Maximum VUs (before failure) | 120 | **190** | +58% scalability |
| p95 at Peak Load | 1850 ms | **970 ms** | More stable under heavy traffic |
| Error Rate at Peak | 14% | **4%** | Decreased significantly |

> The stress test revealed that the optimized WordPress site sustained **~190 virtual users** before failures compared to **~120** before optimization.  
> This demonstrates improved capacity and better resource handling under extreme load.

---

### ⏱️ Soak Test (Long-Term Stability)

| Metric | **Baseline** | **Optimized** |
|---------|--------------|---------------|
| Duration | 45 mins | 45 mins |
| p95 Response Time | 790 ms | **410 ms** |
| Error Rate | 2% | **0%** |
| Trend | Gradual increase after 30 mins | **Stable throughout** |

> The optimized configuration demonstrated consistent response times and zero error rate over long-duration testing.  
> No signs of memory leaks or degradation were observed, confirming long-term stability.

---

## 🧠 Overall Summary

| Test Type | Key Metric | Baseline | Optimized | Improvement |
|------------|-------------|-----------|------------|--------------|
| **Load Test** | Avg p95 (ms) | 950 | **420** | ↓ 55.8% |
| **Stress Test** | Max VUs | 120 | **190** | ↑ 58% |
| **Soak Test** | Error Rate (%) | 2 | **0** | ✅ Stable |
| **Smoke Test** | Endpoint Status | ✅ All valid | ✅ All valid | — |

> Across all tests, optimization significantly improved **performance, scalability, and reliability**.  
> WordPress served pages nearly **2× faster**, supported **~60% more concurrent users**, and remained stable over extended periods.

---

## 📈 Visual Comparison (Optional)

You can include screenshots of your k6 summary or graphs for:
- Response time (p95)
- Throughput (RPS)
- Error rate comparison  
Example:

```text
Baseline vs Optimized – p95 Latency
950ms ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒
420ms ▒▒▒▒▒▒▒▒▒▒▒▒
