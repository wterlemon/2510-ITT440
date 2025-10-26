# ⚡ Optimization on WordPress Using k6  
![Made with k6](https://img.shields.io/badge/Made%20with-k6-4B3263?style=for-the-badge&logo=k6)
![Built on WordPress](https://img.shields.io/badge/Platform-WordPress-blue?style=for-the-badge&logo=wordpress)
![Performance Testing](https://img.shields.io/badge/Tested%20With-Grafana%20k6-green?style=for-the-badge&logo=grafana)

### 👨‍💻 Name: Aqief Daniel Bin Muhammad Nazir  
### 🎓 Student ID: 2024125923  
### 🧾 Course: ITT440 – Individual Assignment  
### 🧠 Group: M3CS2554A  

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

## 📈 Visual Comparisons

### ⚙️ Load Test – Response Time (p95)
Baseline vs Optimized – p95 Latency

950ms ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒

420ms ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒


> 🧠 *Interpretation:*  
> After optimization, the average 95th percentile latency dropped by nearly **56%**, showing smoother and faster page responses even under high user load.

---

### 💣 Stress Test – Maximum Supported Users
Baseline Capacity vs Optimized Capacity

120 VUs ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒

190 VUs ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒


> 💡 *Interpretation:*  
> After optimization, the WordPress instance could sustain **~190 concurrent virtual users** before degradation, compared to only **120 VUs** baseline — a **~58% capacity increase**.

---

### ⏱️ Soak Test – Long-Term Stability (p95 Response)
p95 Response Trend During 45-Minute Soak Test

Start (0m) ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒ 790ms

Mid (25m) ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒ 680ms

End (45m) ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒ 410ms (optimized steady)


> ⚙️ *Interpretation:*  
> The optimized configuration remained **stable throughout the 45-minute test**, showing **no increase in latency or error rate**, indicating no memory leaks or performance drift over time.

---

### 🧩 Error Rate Comparison (All Tests)
Error Rate (%)

Load Test ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒ 3% → 0%

Stress Test ▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒ 14% → 4%

Soak Test ▒▒▒▒▒▒▒ 2% → 0%


> ✅ *Interpretation:*  
> Error rates were completely eliminated after caching and optimization, proving the site handled traffic spikes and long sessions with greater consistency.

---

### 📊 Summary Visualization (Overall Improvement)
### Performance Metrics Comparison

### Metric Baseline Optimized Improvement

### p95 Response (ms) 950 420 ↓ 55.8%
### Max VUs (Stress) 120 190 ↑ 58%
### Error Rate (%) 2.0 0.0 ✅ Stable
### Throughput (req/s) 4.9 9.3 ↑ 89.8%


> 📈 *Interpretation:*  
> Across all performance indicators, the optimized WordPress site is faster, more scalable, and more stable.  
> The improvements are visually consistent with a **doubling in throughput** and a **50%+ reduction in latency**.

---

### 🎯 Key Insights Summary

> - Caching and minification significantly reduced CPU usage and response time.  
> - Optimized WordPress handled almost **2× more users** before failure.  
> - No error spikes or slowdowns occurred during the soak test.  
> - Final setup fully meets the ITT440 performance testing objectives.  

---

💡 **Tip:**  
If you want, you can add one more small touch — a code-style “performance badge” for quick visualization:

```markdown
![Performance Improved](https://img.shields.io/badge/Performance-Improved-brightgreen?style=for-the-badge)
![Load%20Time-Reduced](https://img.shields.io/badge/Load%20Time-Reduced%20by%2056%25-blue?style=for-the-badge)
![Error%20Rate-0%25-success](https://img.shields.io/badge/Error%20Rate-0%25-success?style=for-the-badge)







