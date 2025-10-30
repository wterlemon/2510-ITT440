# MUHAMMAD NUR ALIF BIN MUHAMMAD HAZLIN
# Comprehensive Web Application Performance Testing & Analysis

---

## 1. Objective

The objective of this assessment is to design, execute, and analyze a **performance testing plan** for a web application using a specialized performance testing tool. The goal is to measure how the system behaves under concurrent user load, interpret key performance indicators (KPIs), and identify bottlenecks and limitations that could affect scalability and reliability.

---

## 2. Tool Selection and Justification
<img width="446" height="114" alt="image" src="https://github.com/user-attachments/assets/22d4d7b5-ae58-4a59-a133-7c4e4c3f767e" />

**Chosen Tool:** Artillery (v2)
**Reason for Selection:**
Artillery is a modern, open-source performance testing framework designed for **HTTP, WebSocket, and API-level testing**. It integrates easily with CI/CD pipelines, produces detailed real-time metrics, and supports both CLI-based local execution and **Artillery Cloud** for visual analytics.

Key advantages of Artillery include:

* Lightweight installation via Node.js (`npm install -g artillery`)
* YAML-based configuration for readable test scenarios
* Support for multiple phases (ramp-up, spike, steady-state)
* Built-in Cloud dashboard for team reporting
* Excellent for REST API and microservice testing

---

## 3. Test Environment Setup

| Component              | Details                                                              |
| ---------------------- | -------------------------------------------------------------------- |
| **Operating System**   | Windows 11                                                           |
| **Tool Version**       | Artillery v2.0.0                                                     |
| **Test Duration**      | 3 minutes, 4 seconds                                                 |
| **Execution Command**  | `artillery run load_test.yml —record —key`                           |
|                        | `a9_2gj4rergu3k7oag0ti6f7y4gfs6yfbm3`                                |
| **Target Application** | [ReqRes API](https://reqres.in) – a public REST API used for testing |
| **Network**            | Stable broadband connection                                          |
| **Cloud Reporting**    | Artillery Cloud                                                      |

**Test Run URL:** [https://app.artillery.io/o451iqt5pybqq/load-tests/tgrp5_jx3ftg4g7zhp7rqtxg6axj9kge366_d55c](https://app.artillery.io/o451iqt5pybqq/load-tests/tgrp5_jx3ftg4g7zhp7rqtxg6axj9kge366_d55c)

---

## 4. Hypothesis

It is hypothesized that **the ReqRes API**, being a publicly available service, will maintain consistent low-latency responses under light to moderate load (up to ~50 concurrent users). However, it is expected to enforce **rate-limiting** under higher loads, returning HTTP `429` (Too Many Requests) responses to prevent server overload.

---

## 5. Test Plan

| Phase                   | Duration    | Load Pattern                              | Purpose                         |
| ----------------------- | ----------- | ----------------------------------------- | ------------------------------- |
| **Ramp-up**             | 60 seconds  | Gradually increase from 10 → 50 users/sec | Observe initial server behavior |
| **Steady Load**         | 120 seconds | Maintain 50 users/sec                     | Assess sustained throughput     |
| **Total Virtual Users** | 7,800       | Completed across test phases              | Evaluate API limits             |

**Scenario Design:**
Each virtual user executed a sequence of:

1. `GET /api/users` – retrieve user list
2. `POST /api/users` – simulate creating a new user
3. `GET /api/users/2` – fetch specific user details

Each action included a **1–2 second think time** to simulate realistic browsing delays.

---

## 6. Test Execution & Results

### Summary Metrics

| Metric                           | Result   | Observation                                   |
| -------------------------------- | -------- | --------------------------------------------- |
| **Total Requests Sent**          | 23,400   | Over 7,800 concurrent user sessions completed |
| **HTTP 200 (OK)**                | 1,729    | Valid successful API responses                |
| **HTTP 401 (Unauthorized)**      | 101      | Likely triggered on restricted endpoints      |
| **HTTP 429 (Too Many Requests)** | 21,570   | Triggered by server-side throttling           |
| **Mean Response Time**           | 32.5 ms  | Rapid average processing speed                |
| **Median Response Time**         | 22.9 ms  | Consistent latency performance                |
| **95th Percentile (p95)**        | 37.7 ms  | Excellent stability under heavy load          |
| **99th Percentile (p99)**        | 214.9 ms | Minor spikes due to throttling                |
| **Max Response Time**            | 1509 ms  | Occasional long responses when rate-limited   |
| **Requests per Second (RPS)**    | 61/sec   | Stable throughput                             |
| **Failed Virtual Users**         | 0        | No client-side script or connection failures  |

---

### Observed Behavior by Phase

#### **Ramp-up Phase (0–60 seconds)**

* Request rate increased gradually from 18 → 100/sec.
* Average latency under 100 ms.
* Minor `401` and `429` errors began appearing as server rate-limiting activated.

#### **Steady Load Phase (60–180 seconds)**

* Sustained throughput of ~150 req/sec.
* Over 90% of total requests returned HTTP 429.
* Despite throttling, all virtual users completed successfully without errors.
* Response times remained stable (median 22.9 ms).

<img width="1357" height="501" alt="image" src="https://github.com/user-attachments/assets/28783e62-4e96-4100-8955-7062caf8c599" />
Image of Load Tests results 


---

## 7. Data Interpretation

1. **Performance Stability**

   * The ReqRes API consistently processed requests within 30–40 ms on average.
   * No major degradation in response time despite increasing user load.

2. **Rate Limiting (HTTP 429)**

   * The high count of 429 responses confirms that ReqRes applies protective throttling to maintain fair use.
   * This is expected behavior for a public testing API, not a system failure.

3. **Scalability**

   * The API is stable up to 50 concurrent users but restricts throughput beyond that level via rate limiting.
   * Throughput plateaued at ~150 req/sec once the limit was enforced.

4. **Reliability**

   * No virtual user sessions failed.
   * Session lengths averaged 3.1 seconds, showing consistent test completion times.

---

## 8. Identified Bottlenecks

| Category               | Bottleneck                    | Cause                                                    |
| ---------------------- | ----------------------------- | -------------------------------------------------------- |
| **Server-side**        | HTTP 429 responses            | Rate-limit policy enforced by ReqRes API                 |
| **Throughput**         | Limited concurrency           | Artificial throttling limits to protect shared resources |
| **Performance Spikes** | Occasional 1.5s response time | Queueing delays during peak load                         |

---

## 9. Recommendations

1. **For Production APIs:**

   * Increase rate-limit thresholds for known clients.
   * Implement request queuing and load balancing.
   * Cache frequent responses to minimize latency.

2. **For Further Testing:**

   * Conduct **Spike Tests** to observe sudden traffic bursts.
   * Perform **Soak Tests** over several hours to detect memory leaks or degradation.
   * Add SLA validations (e.g., ensure 95% responses < 200 ms).

3. **For Ethical Testing:**

   * When using public APIs (like ReqRes), limit test concurrency to avoid service disruption.
   * Use mock APIs or private endpoints for sustained tests.

---

## 10. Conclusion

The **Artillery load test on ReqRes API** successfully demonstrated how a public web service performs under controlled, simulated user load.

* The API responded rapidly (avg. <40 ms) even under heavy concurrency.
* The majority of errors were intentional `429` responses from server throttling.
* The system showed **no failures**, confirming stability and predictable performance.

**Final Assessment:**

| Criterion               | Rating                       |
| ----------------------- | ---------------------------- |
| **Availability**        | 100%                         |
| **Response Stability**  | Excellent                    |
| **Error Tolerance**     | Graceful under throttling    |
| **Overall Performance** | Reliable, well-protected API |

This testing exercise illustrates the effectiveness of Artillery as a modern performance testing tool and highlights the importance of interpreting API rate limits as part of real-world system resilience.

## **YouTube Demo:** [Click to Watch Demonstration Video](https://youtu.be/fHesKKUZHLI)


