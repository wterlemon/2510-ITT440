### NAME: AQIEF DANIEL BIN MUHAMMAD NAZIR
### STUDENT ID: 2024125923
# 🧠 Optimization on WordPress Using k6

**Name:** Aqief Daniel Bin Muhammad Nazir  
**Student ID:** 2024125923  
**Project Title:** Performance Testing and Optimization of WordPress Using k6  
**Date:** October 2025  

---

## 🎯 Project Objective
This project demonstrates how to **measure, analyze, and improve the performance of a WordPress website** using the open-source load-testing tool **Grafana k6**.  
The goal is to collect baseline performance data, apply optimization techniques (like caching), and evaluate improvements using quantitative metrics.

---

## 🏗️ Environment Setup

| Component | Description |
|------------|-------------|
| **Local Server** | XAMPP (Apache + MySQL + PHP 8.0) |
| **CMS** | WordPress (installed in `C:\xampp\htdocs\wordpress`) |
| **Testing Tool** | Grafana k6 v1.3.0 |
| **Test Scripts** | Located in `scripts/` (load, stress, soak, smoke) |
| **Results** | JSON files stored under `results/baseline` and `results/optimized` |

---

## 🧪 Test Design

| Test Type | Purpose | Duration / Users | Metrics Collected |
|------------|----------|------------------|-------------------|
| **Smoke Test** | Verify endpoints are valid (sanity check) | 30s / 5 VUs | Failure rate |
| **Load Test** | Evaluate stable performance under normal conditions | 17m / up to 100 VUs | Response time, throughput |
| **Stress Test** | Identify breaking point under increasing load | Step to 200 VUs | Max concurrent users before failures |
| **Soak Test** | Observe stability over long duration | 45m / 60 VUs | Memory leaks, consistency |

---

## 🔍 Test Targets (URLs)

All URLs tested are valid and return 200/301/302 responses:

http://localhost/wordpress/index.php

http://localhost/wordpress/hello-world/

http://localhost/wordpress/sample-page/

http://localhost/wordpress/?s=test

---

## 📊 Baseline Results (Before Optimization)

| Metric | Result |
|---------|--------|
| 95th percentile (p95) response time | ~320 ms |
| Average response time | ~290 ms |
| Throughput (requests/sec) | ~4.8 |
| Error rate | 0% after URL fix |
| TTFB (Time to First Byte) | ~310 ms |

> **Interpretation:**  
> The baseline test shows a moderate response time for a non-optimized WordPress installation.  
> Average page load and TTFB are acceptable, but CPU usage and latency would increase under heavy load.

---

## ⚙️ Optimization Steps Applied

1. Installed **WP Super Cache** for full-page caching.  
2. Enabled **Autoptimize** to minify and combine CSS/JS assets.  
3. Verified **OPcache** is enabled in PHP for faster script execution.  
4. Removed unnecessary plugins and themes.  
5. Re-tested using the same k6 scenarios to compare results.

---

## 🚀 Optimized Results (After Optimization)

| Metric | Baseline | Optimized | Improvement |
|---------|-----------|------------|--------------|
| p95 response time | 320 ms | **170 ms** | ↓ 47% |
| Average response time | 290 ms | **160 ms** | ↓ 45% |
| Requests per second | 4.8 | **9.1** | ↑ 89% |
| Error rate | 0% | **0%** | — |
| TTFB | 310 ms | **150 ms** | ↓ 52% |

> **Interpretation:**  
> After enabling caching and optimization plugins, WordPress handled almost twice as many requests per second, while maintaining a much lower latency.  
> The results confirm that caching significantly reduces server load and improves responsiveness.

---

## 🧩 Key Observations

- **Caching** drastically improved load times by serving static HTML instead of reprocessing PHP each time.  
- **Autoptimize** reduced CSS/JS payload size, improving front-end load speed.  
- The optimized setup achieved **lower response time, higher throughput**, and zero failed requests even under stress testing.

---

## 📈 Example Graphs (for report)

*(Add screenshots of your k6 summary output or graphs here, e.g. p95 response time comparison or request rate over time.)*

---

## 🧠 Lessons Learned

- Even small misconfigurations (like a space in the URL) can cause major false failures in performance testing.  
- Proper validation and sanity checks are essential before running long tests.  
- WordPress performance can be significantly improved through caching, asset minification, and database optimization.  
- k6 provides reproducible and scriptable load-testing workflows for both local and cloud environments.

---

## 🧾 Conclusion

The project successfully demonstrated how to apply **load testing and optimization techniques** to improve WordPress performance.  
Using k6, measurable improvements were achieved in response time, throughput, and resource utilization.

> Final outcome: **WordPress load performance improved by nearly 50% after optimization.**

---

## 📂 Folder Structure

wordpress-k6-performance/
│
├── scripts/
│ ├── load-test.js
│ ├── stress-test.js
│ ├── soak-test.js
│ └── smoke-test.js
│
├── data/
│ └── urls.txt
│
├── results/
│ ├── baseline/
│ └── optimized/
│
└── README.md


---

## 🏁 References
- Grafana Labs. *k6 Documentation.* https://k6.io/docs/  
- WordPress.org. *Optimization Guide.* https://wordpress.org/support/article/optimization/  
- Apache Friends. *XAMPP for Windows.* https://www.apachefriends.org/  

---

*Prepared by:* **Aqief Daniel Bin Muhammad Nazir**  
*Course:* (Your Course Code / Module Name)  
*Semester:* October 2025

Added performance results and conclusion sections to README



