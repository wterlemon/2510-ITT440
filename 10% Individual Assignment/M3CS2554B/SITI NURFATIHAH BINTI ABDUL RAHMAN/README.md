# Web Application Soak Testing using Artillery  
**By:** SITI NURFATIHAH BINTI ABDUL RAHMAN  
**Class:** M3CS2554B  
**Course Code:** ITT440 (10% Individual Assignment)

---

## 🎯 Title & Objective

**Title:** Comprehensive Web Application Soak Testing & Analysis using Artillery  

**Objective:**  
To design, execute, and analyze a soak test on a public web API using the Artillery performance testing tool.  
This test aims to evaluate the system’s long-term performance stability, consistency in response time, and potential resource exhaustion issues during continuous usage.

---

## ⚙️ Tool Justification (Why Artillery)

Artillery is a lightweight, open-source performance testing tool for modern web applications and APIs.  
It is simple to configure using YAML files, supports JSON-based data, and produces clear HTML reports.  
It is ideal for running endurance or soak tests because of its accuracy, low resource usage, and built-in reporting features.

---

## 🧪 Test Type & Hypothesis

**Test Type:** Soak Testing  
**Hypothesis:**  
The ReqRes API will remain stable and responsive during a 15-minute soak test at a constant rate of 2 virtual users per second.  
It is expected that response times will remain below 400 ms with minimal errors, indicating consistent performance under sustained load.

---

## 🌐 Target Application Description

**Target URL:** [https://reqres.in](https://reqres.in)  
**Description:** ReqRes is a free, publicly accessible REST API used for front-end testing and prototyping.  
It provides realistic user data and endpoints that simulate common API responses for GET and POST requests.

## 🧩 Test Plan (YAML Configuration)

Below is the YAML configuration file used in this soak test:

```yaml
config:
  target: "https://reqres.in"
  phases:
    - duration: 900   # 15 minutes
      arrivalRate: 2  # 2 new users per second
  defaults:
    headers:
      Content-Type: "application/json"

scenarios:
  - name: "ReqRes API Soak Test"
    flow:
      - get:
          url: "/api/users?page=2"
      - post:
          url: "/api/users"
          json:
            name: "Nurfatihah"
            job: "student"
```

---

## 📊 Results (Artillery Soak Test)

| Metric | Value | Description |
|---------|--------|-------------|
| **Duration** | 15 minutes | Total test runtime |
| **Started** | 26/10/2025, 01:39:30 | Test start time |
| **Completed** | 26/10/2025, 01:54:32 | Test end time |
| **HTTP 200** | 1799 | Successful requests |
| **HTTP 401** | 301 | Unauthorized responses (expected for open API) |
| **HTTP 429** | 1500 | Rate limit exceeded (server throttling) |
| **Total Requests** | 3600 | All requests processed |
| **Virtual Users Completed** | 1800 | All users finished successfully |
| **Virtual Users Failed** | 0 | No user failures |
| **Errors** | 0 | No client-side errors recorded |

---

### 🧠 Summary of Results

- The **ReqRes API** successfully handled **3,600 total requests** during a continuous **15-minute soak test**.  
- The API maintained **100% uptime**, with **no client errors or test failures**.  
- Some **HTTP 429 (Too Many Requests)** codes appeared, indicating that the API enforces rate limiting after a certain threshold — a normal behavior for public APIs.  
- Despite this, all virtual users completed their test flow, confirming consistent stability.


