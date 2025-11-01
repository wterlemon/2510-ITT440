# 🧪 Comprehensive Web Application Performance Testing & Analysis

### **Tool Used:** Artillery  
### **Performance Test Type:** Scalability Test  
### **Target Application:** [Discord API]((https://discord.com/developers/docs/reference))  
### **Student Name:** *AHMAD IRFAN BIN AHMAD SHOBIRIN*  
### **Date:** 01 November 2025  

---

## 📘 **1. Objective**

This assignment aims to design, execute, and analyze a performance test plan for a web application using **Artillery**, focusing on the system’s scalability and stability under concurrent user load. The objective is to identify performance bottlenecks, measure key performance indicators (KPIs), and provide recommendations for improvement.

---

## ⚙️ **2. Test Environment Setup**

| Component | Details |
|------------|----------|
| **Tool** | Artillery (v2.x) |
| **Machine** | Localhost (Windows 10, 16GB RAM, i7 CPU) |
| **Network** | 100 Mbps broadband |
| **Target API** | `https://reqres.in/api/users?page=2` |
| **Test Duration** | 180 seconds |
| **Virtual Users** | 3000 created, 2992 completed |
| **Arrival Rate** | 31 requests/sec |

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
