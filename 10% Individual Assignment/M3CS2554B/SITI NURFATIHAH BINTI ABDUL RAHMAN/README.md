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

---

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
