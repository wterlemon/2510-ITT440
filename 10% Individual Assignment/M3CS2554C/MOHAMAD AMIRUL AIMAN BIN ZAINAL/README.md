# 🐻Web Application Performance Testing & Analysis Using Grafana K6
***

### 🧑 Name: MOHAMAD AMIRUL AIMAN BIN ZAINAL
### 🎓 Student ID: 2025140465
### 📄 Course: ITT440
### 👥 Group: M3CS2554C
***

## 🏆 Project Objective
This project's goal is to use Grafana K6 to assess the stability and performance of the public API https://httpbin.org.  Smoke testing was used to confirm the API's fundamental stability and responsiveness under light to moderate load, while breakpoint testing was used to progressively raise the load and determine the system's performance limit.  In order to examine how the API functions in various traffic scenarios, the project will monitor important metrics including response time, error rate, and throughput.


## 🌐 Target Application Description
The target application for this project is https://httpbin.org ,a free and public HTTP request and response service. It is commonly used for testing, 
debugging, and experimenting with HTTP methods such as GET, POST, PUT, and DELETE. The website returns data about the requests it receives, making it 
suitable for performance and API testing without affecting any real production system.


## 🛠️ Test Environment

This section details the hardware and software used to execute the performance test, ensuring the results are reproducible.

| Component | Details |
| :--- | :--- |
| **Test Machine** | IdeaPad Gaming 3 |
| **CPU** | 11th Gen Intel(R) Core(TM) i5-11300H @ 3.10GHz (3.11 GHz)|
| **RAM** | 8GB DDR4 |
| **Tool** | Grafana k6 v1.3.0 |
| **Test Type** | Smoke and Breakpoint Testing |
| **Target Application URL** | 'https://httpbin.org' |


## 💻 Test Plan and Configuration
| **Test Type**          | **Configuration Details**                                                                                                                                        |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Smoke Test**         | 50 Virtual Users (VUs), 45-second duration. Purpose: to verify basic system stability and response under a small, short load.                                    |
| **Breakpoint Test**    | Gradual load increase from 50 to 250 VUs, 20 seconds per stage. Purpose: to identify the maximum load the application can handle before performance degradation. |
| **Request Type**       | HTTP GET requests sent to `https://httpbin.org/get`.                                                                                                             |
| **Metrics Observed**   | Response time (latency), error rate, and throughput (requests per second).                                                                                       |
| **Threshold Criteria** | 95% of requests must complete under 1.5 seconds with less than 5% failed requests.                                                                               |
| **Script Language**    | JavaScript (k6 test scripts).                                                                                                                                    |


## 💻 Test Plan and Configuration
Two performance test scenarios were executed using Grafana k6. For the Smoke Test, 50 virtual users were simulated for 45 seconds to confirm that the target application (https://httpbin.org
) was reachable and stable under a light load. For the Breakpoint Test, the number of virtual users was gradually increased from 50 to 250 in stages of 20 seconds to identify the system’s performance limit. During both tests, HTTP GET requests were sent to the /get endpoint, and key metrics such as response time, error rate, and throughput were recorded for analysis.
