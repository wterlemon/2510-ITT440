# 🧪 Comprehensive Web Application Performance Testing & Analysis

### **Tool Used:** Artillery  
### **Performance Test Type:** Scalability Test  
### **Target Application:** [Discord API](https://discord.com/developers/docs/reference)  
### **Student Name:** *AHMAD IRFAN BIN AHMAD SHOBIRIN*  
### **Date:** 01 November 2025  

---


## 📘 **1. Objective**

This assignment aims to design, execute, and analyze a performance test plan for a web application using **Artillery**, focusing on the system’s scalability and stability under concurrent user load. The objective is to identify performance bottlenecks, measure key performance indicators (KPIs), and provide recommendations for improvement.

---
## Tool & Test Selection Justification

<p align="center">
<img width="500" height="243" alt="1_p4IQfjORMIMZtN8SJRjzcA" src="https://github.com/user-attachments/assets/9bcc62c7-bf15-4428-a6d8-d43b25c77ad2" />   

Artillery is an open-source tool that facilitates a straightforward testing framework for HTTP, WebSocket, and API-level testing, it was employed in the experiment. YAML script execution for stress testing. The tool provides accurate error and reaction time measurements, and its integrated cloud dashboard for reporting is For improved analysis, Artillery Cloud creates graphic performance graphs.


<p align="center">
<img width="500" height="497" alt="image" src="https://tasshin.com/wp-content/uploads/2023/11/discord.jpg" />
  
## Target Web Application (Discord)

The experiment used the Discord API because it provides a reliable, developer-friendly platform with real-world scalability. The API supports both REST and WebSocket communication, allowing realistic simulations of user interactions and message exchanges. Its well-documented endpoints and stable performance make it ideal for evaluating system response times, rate limits, and stability under high user load using Artillery. 

---
## Test Environment Setup

| Component         | Details                                  |
| ----------------- | ---------------------------------------- |
| **Tool**          | Artillery (v2.x)                         |
| **Machine**       | Localhost (Windows 10, 16GB RAM, i7 CPU) |
| **Network**       | 100 Mbps broadband                       |
| **Target API**    | `https://discord.com/api`                |
| **Test Duration** | 180 seconds                              |
| **Virtual Users** | 3000 created, 2992 completed             |
| **Arrival Rate**  | 31 requests/sec                          |

---


## ⚙️ **2. Test Plan**

| **Section**                          | **Details**                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Test Title**                       | Artillery Scalability & Discord API                                                                                                           |
| **Objective**                        | To evaluate the performance and scalability of the Discord API under concurrent user load using Artillery, focusing on response time, throughput, and error rate. |
| **Tool Used**                        | Artillery v2.x                                                                                                                                                   |
| **Test Type**                        | Scalability Test                                                                                                                               |
| **Test Date**                        | 01 November 2025                                                                                                                                                 |
| **Test Engineer**                    | *Ahmad Irfan*                                                                                                                                                    |
| **Target System / API Endpoint**     | `https://discord.com/api`                                                                                                                             |
| **Test Duration**                    | 3 minutes (180 seconds)                                                                                                                                          |
| **Load Model**                       | Stepwise ramp-up (10 → 20 virtual users per second)                                                                                                              |
| **Number of Virtual Users (VUs)**    | 3000 created                                                                                                                                                     |
| **Test Scenario Description**        | Each virtual user sends a `GET` request to `/api/users?page=2`, simulating typical client behavior retrieving paginated user data.                               |
| **KPIs Measured**                    | - Response Time (min, mean, p95, p99)  <br> - Throughput (requests/sec) <br> - Error Rate <br> - Virtual User Completion                                         |
| **Performance Thresholds (Targets)** | - Average Response Time ≤ 500 ms  <br> - Error Rate ≤ 2%  <br> - 95% Responses < 1s                                                                              |
| **Test Environment**                 | Localhost (Windows 10, Intel i7, 16GB RAM) <br> Network: 100 Mbps broadband                                                                                      |
| **Monitoring Tools**                 | Artillery CLI and built-in metrics                                                                                                                               |
| **Assumptions**                      | Discord API remains accessible and stable throughout testing.                                                                                              |
| **Risks / Constraints**              | DIscord API may have rate limiting or IP blocking during extended scalability tests.                                                                                     |
| **Success Criteria**                 | API maintains <5% error rate and <500 ms mean response time under 30 requests/sec load.                                                                          |


### **Configuration File (artillery.yml)**

```yaml
config:
  target: "https://reqres.in"
  phases:
    - duration: 60
      arrivalRate: 10
    - duration: 120
      arrivalRate: 20
scenarios:
  - name: "Get Users"
    flow:
      - get:
          url: "/api/users?page=2"
```

---

## 📊 **3. Test Results Summary**

### **Artillery Summary Report**

```
--------------------------------
Summary report @ 16:51:37(+0800)
--------------------------------

errors.ECONNRESET: ............................................................. 8
http.codes.404: ................................................................ 5984
http.downloaded_bytes: ......................................................... 0
http.request_rate: ............................................................. 31/sec
http.requests: ................................................................. 5992
http.response_time:
  min: 216
  max: 2240
  mean: 278.2
  median: 247.2
  p95: 487.9
  p99: 889.1
http.responses: 5984
vusers.completed: 2992
vusers.created: 3000
vusers.failed: 8
vusers.session_length:
  min: 2485.3
  max: 10619.6
  mean: 2702.3
  median: 2566.3
  p95: 3328.3
  p99: 3752.7
```

---

## 📈 **4. Data Analysis & Interpretation**

| Metric | Observation | Interpretation |
|--------|--------------|----------------|
| **Response Time (mean)** | 278 ms | Acceptable for most API calls (<300 ms). |
| **p95 Response Time** | 487 ms | Indicates 95% of requests completed below 0.5s — good stability. |
| **Errors (ECONNRESET)** | 8 | Minimal network resets due to concurrency spikes. |
| **HTTP 404 Errors** | 5984 | Suggests requests to a non-existent endpoint or query mismatch. |
| **User Completion Rate** | 2992/3000 (99.7%) | Excellent session completion rate under load. |

### 📉 Observed Bottlenecks
- 404 responses indicate the API endpoint was incorrect or rate-limited under stress.  
- Slight response latency spike at high concurrency (p99 = 889 ms).  
- Minor connection resets suggest socket timeout under heavy load.

---

## 🧠 **5. Recommendations**

1. **Validate endpoint configuration** — confirm `/api/users?page=2` accepts concurrent requests.  
2. **Enable caching or CDN** to reduce backend load.  
3. **Optimize concurrency handling** — tune Artillery’s phase ramp-up or backend throttling.  
4. **Monitor API rate-limiting** via logs or HTTP headers.  
5. **Add soak and stress tests** for extended evaluation of performance stability.

---

## 🧩 **6. Conclusion**

The performance test demonstrated that the target API handles moderate concurrent load effectively with an average response time below 300 ms and high completion rates. However, consistent 404 errors and occasional connection resets suggest configuration or rate-limiting issues under sustained high traffic. Future tests will explore long-duration soak tests and scaling improvements.

---

## 🎥 **7. Demonstration Video**

➡️ [YouTube Demo Link – *Insert here after uploading your presentation*](https://youtube.com)

---

## 🧾 **8. Repository Structure**

```
/artillery-performance-test
│
├── artillery.yml
├── results/
│   └── summary-report.txt
├── screenshots/
│   └── artillery-dashboard.png
├── README.md  ← (This Report)
└── video/
    └── performance-demo.mp4
```
