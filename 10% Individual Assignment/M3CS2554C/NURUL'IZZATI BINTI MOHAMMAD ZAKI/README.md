# 🚀 Performance Testing on JSONPlaceholder API Using Artillery

**Name:** Nurul’Izzati binti Mohammad Zaki  
**Student ID:** 2025395205  
**Class:** M3CS2554c

🎥 **Demo Video:** [Watch on YouTube](https://youtu.be/YOUR_VIDEO_LINK)

---

## 🧭 Introduction

This project focuses on evaluating the performance and stability of the **JSONPlaceholder API** by running a **load test** using **Artillery**, a popular open-source performance testing tool built for Node.js.  
The aim is to measure the system’s behavior when multiple users access it simultaneously and to determine how well it performs under different traffic conditions.

---

## 🎯 Goal and Hypothesis

The main goal of this test is to analyze how **JSONPlaceholder** handles increasing user load and whether it remains stable under pressure.

**Hypothesis:**  
> The JSONPlaceholder API will maintain good performance under load, with average response times below 500 milliseconds, minimal latency spikes, and no request failures even at peak user load.

---

## ⚙️ Tool Selection Justification

| Reason | Explanation |
| --- | --- |
| Easy setup | Artillery uses simple YAML configuration files that are easy to modify and read. |
| Detailed metrics | Provides in-depth response time and throughput reports with percentiles (p50, p95, p99). |
| Cloud visualization | Integrates with **Artillery Cloud** for graphical results and trend analysis. |
| Lightweight | Works efficiently on local machines without extra dependencies. |
| Industry adoption | Commonly used for API and backend performance testing in CI/CD pipelines. |

Artillery was chosen because it offers the balance of simplicity, accuracy, and modern visualization tools that fit academic and industry testing standards.

---

## 🧩 Test Environment

| Component | Details |
| --- | --- |
| Operating System | Windows 10 |
| Node.js Version | 18.x |
| Artillery Version | 2.x |
| Target URL | https://jsonplaceholder.typicode.com |
| Internet Connection | Stable broadband |

---

## 📋 Test Scenario Configuration

Each virtual user (VU) simulates a normal usage pattern by sending a sequence of API requests.  

| Step | Action | Endpoint | Method |
| --- | --- | --- | --- |
| 1 | Retrieve a post | `/posts/1` | GET |
| 2 | Retrieve a user | `/users/1` | GET |
| 3 | Create a new post | `/posts` | POST |
| 4 | Wait between requests | — | think(1s) |

---

## 📈 Load Phases

| Phase | Duration | Arrival Rate | Ramp To | Description |
| --- | --- | --- | --- | --- |
| Low | 30s | 2 users/sec | 5 users/sec | Establish baseline load |
| Moderate | 60s | 5 users/sec | 10 users/sec | Typical daily traffic simulation |
| Heavy | 90s | 10 users/sec | 15 users/sec | Peak traffic to test stability |

This gradual increase simulates real-world traffic, helping to identify how performance scales with concurrent users.

---

## 🧰 Test Execution

### Step 1: Run test locally and save results
```bash
artillery run jsonplaceholder-load-test.yml -o results/test_output.json
