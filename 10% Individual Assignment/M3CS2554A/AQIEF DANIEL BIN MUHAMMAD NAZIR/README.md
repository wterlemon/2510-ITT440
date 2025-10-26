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
