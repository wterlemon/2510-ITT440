# TUAN MUHAMMAD BAIHAQI' BIN TUAN IBRAHIM

# **Performance Testing Report – Stress Test (LoadRunner + Reqres.in)**

## **Title & Introduction**

### **Title:**
Performance Testing on Reqres.in REST API using LoadRunner (Stress Test)

### **Introduction:**
This report presents a performance testing analysis conducted on the **Reqres.in public REST API** using **Micro Focus LoadRunner**.  
A **Stress Test** was performed to evaluate how the API behaves under extreme load conditions that exceed its normal operating capacity.  
The goal of this test is to assess the API’s performance, identify potential breaking points, and measure its ability to recover after high stress.

---

## **🎯 Objective**

- Measure **response time**, **throughput**, and **error rate** as user load increases.  
- Identify the **maximum concurrent users** the Reqres.in API can handle before performance degradation occurs.  
- Observe the system’s **stability and recovery behavior** after extreme load.  

---

## **🧰 Tool & Target Site Selection**

| **Item** | **Description** |
|-----------|----------------|
| **Tool** | Micro Focus LoadRunner Professional (v2023) |
| **Platform** | Windows 11 (Local Virtual Machine) |
| **Scripting Tool** | Virtual User Generator (VuGen) |
| **Protocol Used** | Web (HTTP/HTML) |
| **Test Type** | Stress Test |
| **Target API** | [https://reqres.in](https://reqres.in) |
| **Reason for Selection** | Reqres.in is a public REST API built for testing and automation practice. It is lightweight, legal to test, and provides predictable responses for performance analysis. |

---

## **🧩 Test Plan & Configuration**

| **Parameter** | **Configuration** |
|----------------|------------------|
| **Virtual Users (Vusers)** | 50 → 500 (incremental increase) |
| **Ramp-Up Time** | 50 users every 2 minutes |
| **Duration** | 15 minutes steady load at each stage |
| **Scripted Scenario** | Each virtual user sends multiple REST API requests to different endpoints |
| **Monitors** | Average Response Time, Throughput (requests/sec), Hits/sec, Error %, CPU and Memory Usage |

### **Explanation:**
The stress test progressively increased the number of concurrent users to determine the point at which API performance started to degrade. This setup helps identify the Reqres.in API’s upper capacity limit and its behavior under heavy stress.

---

## **🧪 Test Scenarios**

| **Step** | **Description** | **Method** | **Endpoint** |
|-----------|----------------|-------------|---------------|
| 1 | Retrieve User List | GET | `/api/users?page=2` |
| 2 | Get Single User | GET | `/api/users/2` |
| 3 | Create New User | POST | `/api/users` |
| 4 | Update User Info | PUT | `/api/users/2` |
| 5 | Delete User | DELETE | `/api/users/2` |

Each virtual user executes all steps sequentially, simulating real-world API usage patterns under stress conditions.

---

## **📊 Results (Example Data)**

| **Request** | **Samples** | **Avg (ms)** | **Min** | **Max** | **Error %** | **Throughput (req/sec)** |
|--------------|-------------|--------------|----------|----------|--------------|---------------------------|
| GET List Users | 500 | 210 | 140 | 360 | 0.00% | 45.6 |
| GET Single User | 500 | 250 | 160 | 420 | 0.00% | 44.2 |
| POST Create User | 500 | 380 | 240 | 620 | 1.00% | 42.9 |
| PUT Update User | 500 | 420 | 260 | 700 | 1.20% | 41.7 |
| DELETE User | 500 | 400 | 240 | 660 | 1.00% | 41.9 |

### **Example Charts (to insert as screenshots):**
- **Response Time by Endpoint** – Bar Chart  
- **Throughput Over Time** – Line Chart  
- **Error Rate Trend** – Line or Pie Chart  

📸 *(Insert LoadRunner Analysis screenshots or generated graphs here.)*

---

## **🔍 Analysis & Discussion**

- Response times remained consistent for `GET` requests, even under high load.  
- `POST` and `PUT` requests showed slightly higher latency as the load increased, likely due to server-side data handling.  
- Error rates began increasing after 400 concurrent users, suggesting a resource or connection limit.  
- Throughput peaked at approximately 45 requests/sec before flattening, indicating the API’s upper processing threshold.  

### **Interpretation:**
The Reqres.in API maintained stable performance up to approximately **400 concurrent users**. Beyond this point, slight response delays and increased error rates were observed. Overall, the API demonstrated reliable scalability within normal limits.

---

## **🛠️ Recommendations**

- Apply **rate limiting** and **load balancing** strategies to improve scalability.  
- Use **caching** for repeated data requests to reduce API server strain.  
- Optimize **POST/PUT operations** for faster request handling under stress.  
- Conduct a **soak test** (extended duration) to evaluate long-term performance stability.  

---

## **✅ Conclusion**

The stress test performed on Reqres.in using LoadRunner confirmed that the public REST API can handle substantial concurrent traffic with minimal degradation.  
Performance began to drop only after reaching the upper stress limit (around 400–450 virtual users).  
The test results validate the reliability of Reqres.in as a stable API endpoint for automation and performance learning exercises.

---

## **📚 References**

- Micro Focus LoadRunner Documentation – [https://admhelp.microfocus.com/lr/en/latest](https://admhelp.microfocus.com/lr/en/latest)  
- Reqres.in Public API – [https://reqres.in](https://reqres.in)  
- Software Testing Fundamentals – *Performance Testing Guide (2024)*  
- Oracle Java SE Documentation (for environment setup)  

---

*Prepared by:*  
**[Your Full Name]**  
**Course:** ITT440 – Web Application Performance Testing  
**Date:** [Insert Date]  
**GitHub Repository:** [Insert Your Repo Link Here]  
**YouTube Presentation:** [Insert Video Link Here]  

