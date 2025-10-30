# **⚡️Reqres API Load Test using BlazeMeter⚡️**  
<img width="900" height="350" alt="image" src="https://github.com/user-attachments/assets/42213e1a-1233-474d-83c4-4359806fc9dc" />

### Name: MUHAMMAD HAIRIEL ANUAR BIN MOHD ZAHARI
### Course: ITT440 
### Group: M3CS2554A  

---

## **💻Introduction**
This project focuses on evaluating the performance of a public API, **Reqres.in**, using a load testing approach.  
Load testing helps determine how well a system performs under specific user loads and ensures that it can handle concurrent requests without degradation.  

The goal of this test is to measure **response time, throughput, and stability** when multiple users access the API simultaneously. The test was conducted using **BlazeMeter**, a cloud-based performance testing tool that provides easy configuration, monitoring, and reporting.

---

## **📽️Project Overview**
The target system for this project is **Reqres.in**, a free and publicly available REST API used for testing and prototyping HTTP requests.  

The project aims to:
- Simulate multiple virtual users (VUs) accessing the Reqres API.
- Measure average response time, throughput, and error rate.
- Evaluate the scalability and consistency of the API under continuous load.

**Endpoint tested:**
GET https://reqres.in/api/users?page=2

This endpoint was selected because it returns a paginated list of user data in JSON format, making it ideal for performance testing as it involves real HTTP request–response cycles. Since Reqres.in is designed for safe testing, it provides a stable and controlled environment for load testing without affecting any production systems.

**Screenshot of API response:**

![Reqres API Response](images/reqres_api_response.png)

---

## **🛠️Tool Selection and Justification**
The tool selected for this project is **BlazeMeter**, an online performance testing platform that supports **Apache JMeter** scripts and cloud-based execution.

**Reasons for choosing BlazeMeter:**
1. **Ease of Use:** Provides an intuitive interface for designing and executing tests without requiring local setup.
2. **Scalability:** Supports testing from the cloud with hundreds of concurrent users.
3. **Detailed Analytics:** Automatically generates detailed reports with response time percentiles, throughput, and error rates.
4. **Integration Ready:** Compatible with CI/CD tools for automated testing.
5. **Free Tier:** The free plan supports up to 50 concurrent users, which fits the project’s scope.

BlazeMeter was selected for its simplicity, flexibility, and professional reporting capabilities.

---

## **🧱Test Setup**

| Category | Details |
|-----------|----------|
| **Tool Used** | BlazeMeter (JMeter engine) |
| **Test Type** | Load Test |
| **Target API** | `https://reqres.in/api/users?page=2` |
| **Virtual Users (VUs)** | 50 |
| **Test Duration** | 10 minutes |
| **Ramp-Up Time** | Automatically handled by BlazeMeter |
| **Test Location** | US East (Virginia, Google Cloud) |
| **Request Method** | GET |
| **Expected Response Code** | 200 OK |
| **Success Criteria** | 95% of requests under 500 ms, error rate < 1% |

During the test, BlazeMeter simulated 50 concurrent virtual users for 10 minutes, continuously sending GET requests to the Reqres API endpoint. Metrics such as response time, throughput, and errors were automatically collected through BlazeMeter’s reporting system.

---

## **📄Test Result**
**Summary of Results (from BlazeMeter Dashboard):**
<img width="1288" height="105" alt="image" src="https://github.com/user-attachments/assets/5ff95015-d6a5-4561-8374-c8891ceec37a" />


| Metric | Result | Description |
|--------|---------|-------------|
| **Max Virtual Users** | 50 | Total concurrent users simulated |
| **Average Throughput** | 480.27 hits/sec | Average successful requests per second |
| **Average Response Time** | 98.84 ms | Mean response time for all requests |
| **90th Percentile Response Time** | 115 ms | 90% of requests completed within this time |
| **Error Rate** | 0% | All requests succeeded |
| **Average Bandwidth** | 46.39 MiB/s | Average data transfer per second |
| **Test Duration** | 10 minutes | Total execution time |

**Load:** 

<img width="629" height="375" alt="image" src="https://github.com/user-attachments/assets/121bbb22-645c-4c96-9fcc-e86b293f042b" />


**Response Time:**

<img width="619" height="369" alt="image" src="https://github.com/user-attachments/assets/12b5f9c2-c88a-41cc-84fa-4585d514201b" />

**Main Timeline Chart:**

<img width="1920" height="1080" alt="main-timeline-chart-a492942d-2760-420b-ad75-9ad92909b2fc" src="https://github.com/user-attachments/assets/6c87ceb7-931d-4ef8-ae73-3c8b47468bc8" />


---

## **🔬Analysis**

### **Performance**
The Reqres API maintained excellent performance under a steady load of 50 virtual users.  
- The **average response time** of ~99 ms indicates very fast server processing.  
- The **90th percentile** of 115 ms shows that even the slowest requests were well within acceptable performance limits.  
- The **throughput** of 480 hits per second demonstrates high efficiency.  
- The **error rate** of 0% confirms the API handled the load flawlessly.

### **Scalability**
The test results suggest that Reqres.in can easily scale to handle at least 50 concurrent users without performance degradation.  
Future tests with higher VUs (e.g., 100–200) could help identify the breaking point where response time increases or errors appear.

### **Consistency**
During the 10-minute test, response times remained stable with no spikes or slowdowns.  
Throughput and bandwidth usage were consistent, indicating predictable and reliable system performance across all simulated users.

---

## **🧬Raw Data**
| Parameter | Value |
|------------|--------|
| **Total Requests Sent** | ~288,000 (480 req/s × 600 seconds) |
| **Successful Requests (2xx)** | 100% |
| **Failed Requests** | 0 |
| **Minimum Response Time** | ~90 ms |
| **Maximum Response Time** | ~120 ms |
| **Average Response Time** | 98.84 ms |
| **90th Percentile** | 115 ms |
| **Average Bandwidth** | 46.39 MiB/s |

---

## **🔑Performance Results and Analysis**
The collected data shows that the Reqres API is **highly stable and responsive** under continuous load conditions.  

**Key Observations:**
- Response times consistently under 120 ms.
- No failed requests.
- Throughput maintained at ~480 requests/second.
- Bandwidth usage steady around 46 MB/s.

**Interpretation:**
These metrics demonstrate that Reqres.in’s backend infrastructure efficiently handles simultaneous GET requests.  
The performance remains stable across all simulated users, which is a strong indicator of good backend optimization and API reliability.

---

## **📁Conclusion and Improvement**

### **Conclusion**
The BlazeMeter load test confirmed the excellent stability and performance of the Reqres API. With 50 virtual users and zero errors, the system maintained an average response time below 100 ms. It is showing outstanding efficiency and responsiveness.

### **Recommendations for Improvement**
1. **Increase Load Scale:** Perform stress testing with more users to find the performance threshold.  
2. **Multi-Region Testing:** Execute the same test from other geographic regions to observe latency differences.  
3. **Longer Testing Duration:** Run a soak test (1–2 hours) to detect long-term resource issues.  
4. **Integrate Monitoring Tools:** Use APM tools for server resource tracking.  

---

## **📼Video Demonstration**
