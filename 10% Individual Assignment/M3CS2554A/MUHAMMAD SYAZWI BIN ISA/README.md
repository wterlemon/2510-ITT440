# 🚀 Web Application Performance Testing

**Course:** 2510-ITT440  
**Assessment:** 1 (10%)  
**Name:** MUHAMMAD SYAZWI BIN ISA 
**Matrix Number:** 2024783361  
**Test Type:** Smoke Test (Basic Health Check)  


---

## 🛠️ Tool of Choice: `k6` by Grafana Labs

I have selected **`k6`** as my performance testing tool.

*   **Why k6?** k6 is a modern, developer-centric, and open-source load testing tool built for making performance testing a productive and enjoyable experience. It uses JavaScript for test scripting, making it accessible and powerful.
*   **Key Features:**
    *   CLI-based with a simple and clean API.
    *   Scripting in JS (ES6+ supported).
    *   Built-in metrics for performance analysis.
    *   Designed for automation and CI/CD integration.

---

## 🧪 Test Strategy: Smoke Test

I conducted a **Smoke Test** to verify basic system health and core functionality under minimal load.

*   **Objective:** Quick verification that critical endpoints are available and responsive
*   **Load Profile:** Minimal load (3 virtual users) for short duration
*   **Success Criteria:** High availability and fast response times

### Tested Endpoints:
- `https://jsonplaceholder.typicode.com/posts/1`
- `https://jsonplaceholder.typicode.com/users/1` 
- `https://httpbin.org/status/200`

---

## 📊 Test Results & Analysis

### 🎯 Executive Summary
**STATUS: PASSED ✅** - The smoke test successfully verified system health with excellent performance metrics.

### 📈 Key Performance Indicators

| Metric | Result | Assessment |
|--------|--------|------------|
| **Check Success Rate** | 97.97% | ✅ **Excellent** |
| **HTTP Failure Rate** | 0.31% | ✅ **Excellent** |
| **Average Response Time** | 279.39ms | ✅ **Excellent** |
| **95th Percentile Response** | 1.28s | ✅ **Good** |
| **Virtual Users** | 3 | ✅ **As Configured** |

### 📋 Detailed Results

```yaml
Checks:
  Total Checks: 2,568
  Succeeded: 2,516 (97.97%) ✅
  Failed: 52 (2.02%) ⚠️

HTTP Metrics:
  Total Requests: 1,284
  Failed Requests: 4 (0.31%) ✅
  Average Duration: 279.39ms ✅
  P95 Duration: 1.28s ✅
  Maximum Duration: 12.68s ⚠️

Execution:
  Iterations: 428
  Virtual Users: 3 (consistent)
  Test Duration: 2 minutes
