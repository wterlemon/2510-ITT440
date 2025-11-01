# Comprehensive Web Application Performance Testing & Analysis
---

### STUDENT NAME : NUR ARIF ASYRAF BIN ZAHARI
### ITT440 - INDIVIDUAL ASSIGNMENT
### GROUP : M3CS2554B
---

# 🔍 Stress Testing on DummyJSON using Artillery
---

## Introduction

The assignment demands Artillery execution of a stress test on DummyJSON API to evaluate its operational stability when facing high traffic volumes. The test evaluates API performance under heavy traffic conditions to detect rate limit violations that result in HTTP 429 errors and assesses its recovery time after traffic decreases. The test evaluates API scalability through performance metrics which include response time and data processing capacity and error frequency during warm-up, high load and recovery phases.

---

## Objectives

- To evaluate the performance and stability of the DummyJSON API under different load conditions.
- To observe how the API responds during warm-up, sustained high load, and recovery phases.
- To identify potential performance bottlenecks or timeout issues under heavy traffic.
- To measure response times, throughput, and error rates for performance analysis.

---

## Tool & Test Selection Justification

<p align="center">
<img width="500" height="243" alt="1_p4IQfjORMIMZtN8SJRjzcA" src="https://github.com/user-attachments/assets/9bcc62c7-bf15-4428-a6d8-d43b25c77ad2" />    

## Performance Testing Tool (Artillery)

The experiment used Artillery because this open-source tool enables simple testing framework designed for HTTP, WebSocket, and API-level testing. Stress testing through YAML script execution. The tool delivers precise measurements of response times and errors while Built-in Cloud dashboard for reporting which is Artillery Cloud generates visual performance graphs for better analysis.

---

<p align="center">
<img width="500" height="497" alt="image" src="https://github.com/user-attachments/assets/51d8c870-99b9-4708-ba60-9dffb25ca339" />

## Target Web Application (DummyJson)

The experiment used DummyJSON because it offers a free stable fake REST API that performs well for performance testing. The API generates realistic data about products and users which enables Artillery to perform simulations of actual API operations. The API generates stable responses which make it perfect for studying system performance and stability during high-stress situations.

---

## Test Environment Setup

| **Component**          | **Details**                                                                        |
| ---------------------- | ---------------------------------------------------------------------------------- |
| **Environment**        | Windows 11 operating system                                                        |
| **Testing Framework**  | Artillery v2.0.26                                                                   |
| **Configuration File** | `stress_test.yml`                                                                  |
| **Execution Method**   | `artillery run stress_test.yml --record --key a9_x5xh12axy495k0pmfhng64nkpf3u2kti` |
| **Target Endpoint**    | [DummyJSON API](https://dummyjson.com) – REST API for fake data testing            |
| **Test Category**      | Stress Test                                                                        |
| **Test Duration**      | 3 minutes, 6 seconds                                                               |
| **Load Pattern**       | Warm-up → Sustained High Load → Recovery                                           |
| **Reporting Platform** | Artillery Cloud Dashboard                                                          |

Test Run URL : https://app.artillery.io/otv0ucti84aw9

---

## Hypothesis Application's Performance

The DummyJSON API will maintain operational stability at normal usage levels but will start to show delayed responses and HTTP 429 rate-limiting errors when handling large numbers of users. The API will experience rising latency and server throttling timeouts when request numbers exceed its maximum processing threshold. The API performance will return to normal after load reduction during the recovery phase because the system failure is not the cause of performance degradation under stress.

---

## Test Plan

| **Phase**                     | **Duration** | **Arrival Rate (Users/sec)** | **Description**                                                                                                            |
| ----------------------------- | ------------ | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Warm-up Phase**             | 30 seconds   | 20 users/sec                 | Begins with moderate virtual user traffic to prepare the DummyJSON API for consistent load testing.                        |
| **Sustained High Load Phase** | 120 seconds  | 150 users/sec                | Applies continuous heavy virtual user traffic to test the API’s stability, response time, and error handling under stress. |
| **Recovery Phase**            | 30 seconds   | 50 users/sec                 | Gradually reduces the number of virtual users to observe how the API performance stabilizes after intense usage.           |

---

## Test Result Summary

| Metric                                  | Result       | Observation                               |
| --------------------------------------- | ---------------- | ------------------------------------------------------------------------------------------- |
| **Total Requests**                      | 100,500          | High number of requests                           |
| **Request Users Rate**                        | 534 users/sec      | Steady high throughput                            |
| **HTTP (200+201) Responses**                  | 73,730  | Majority of requests succeeded      |
| **HTTP 429 Responses**                  | 26,770           | Significant rate-limit errors        |
| **Error Rate (4xx)**                    | 26.7%            | A notable portion of requests failed           |
| **Min Response Time**             | 2 ms             | Some requests were extremely fast |
| **Max Response Time**             | 2,574 ms         | Some requests experienced very high latency       |
| **Median Response Time**          | 22.9 ms          | Typical response time is low                       |
| **95th Percentile** | 290.1 ms         | Most requests completed within acceptable time            |
| **99th Percentile** | 415.8 ms         | Worst-case requests were slower            |
| **Virtual Users Created**               | 20,100           | Large number of users simulated                        |
| **Virtual Users Completed**             | 20,100           | All simulated users completed successfully                     |
| **Virtual Users Failed**                | 0                | No test script errors occurred.                                    |

---

## Performance Summary Observation

### Throughput

- Request Rate: 534 requests/sec
- Total Requests: 100,500
- Observation: High throughput shows the API can handle continuous heavy load.

### Error Rate

- HTTP 2xx Responses: 73,730 (73.4%)
- HTTP 429 Responses (Rate-Limit): 26,770 (26.7%)
- Observation: 27% of requests failed due to throttling, indicating the server limits concurrent requests under stress.

## Raw Data Presentation

<img width="1378" height="566" alt="image" src="https://github.com/user-attachments/assets/cb400c17-8603-4e81-abbe-ba8a2c60ff3d" />
The evaluation consisted of three distinct stages which included Warm-up followed by Sustained Load and then Recovery. The system maintained fast response times throughout the Warm-up period while the load continued to rise. The system maintained 600–900 req/s performance during the Sustained phase while keeping latency at a low level. The system restored its performance to normal levels during Recovery which demonstrated its ability to maintain stability and recover from stress.

---

<img width="1379" height="376" alt="image" src="https://github.com/user-attachments/assets/ebb36622-577c-4923-9283-d6341676d0a6" />
The test system processed 100.5K requests which resulted in fast successful responses with median 23 ms response times and 95% of responses under 290 ms and a maximum response time of 2.5 seconds. The system returned 200/201 responses for 73% of requests but produced 26.7K (26.7%) rate-limit errors which indicated excellent performance with only occasional throttling during high traffic conditions.

## Overall Observation

- The API sustains high throughput efficiently.
- Most responses are fast, but the server triggers rate limiting under heavy load.
- Tail latency indicates some requests may experience delays at peak stress.

---

## Interpretation and Bottlenecks

| **Section**                   | **Description**                                                                                                                                                                                                                                                                                                               |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Interpretation of Results** | The system maintained stable throughput and low response times during the test. Average and 95th percentile response times were within acceptable limits, showing the API handled concurrent users efficiently. Minor response spikes occurred at peak load, indicating brief latency under stress.                           |
| **Identified Bottlenecks**    | The occurrence of HTTP 429 errors and increased response times at peak load suggest rate limiting or resource exhaustion. The bottleneck likely comes from limited server capacity or concurrency handling. Improving rate limit settings, scaling server resources, or enhancing load balancing could mitigate these issues. |

---

## Recommendations For Further Testing

- Optimize its rate limiting mechanism to process multiple requests simultaneously before it starts throttling.
- Upgrade load balancing implementation to distribute traffic equally across all servers and protect against single server overload.
- Optimize atabase performance optimization through improved indexing and query optimization and data caching techniques.
- - Needs additional server resources including CPU power and memory capacity and extra instances to boost its request processing abilities.
- Use continuous monitoring tools to track performance data which helps identify performance bottlenecks as they occur.
- System requires scheduled load and stress testing to verify new improvements while ensuring ongoing system stability.

---

## Conclusion

The system operated with high stability while handling maximum capacity by processing large amounts of data without significant system failures. The system processed most requests at fast speeds but showed occasional delayed responses and rate limit messages when handling maximum capacity. The API will achieve improved reliability and consistency in future high-load situations through enhanced scalability and rate optimization and resource management improvements.

---
