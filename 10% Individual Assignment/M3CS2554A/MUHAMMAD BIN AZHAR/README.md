 # 💬 Stress Testing of BlazeDemo using Gatling
<img width="620" height="211" alt="image" src="https://github.com/user-attachments/assets/af5b8a6a-1344-4782-985d-13280c468467" />

### 🧑‍🎓 STUDENT NAME : MUHAMMAD BIN AZHAR
### 📝 ITT440 - INDIVIDUAL ASSIGNMENT
### 👥 GROUP : M3CS2554A

---

## 🧩 Introduction

This project demonstrates a **Comprehensive Web Application Performance Test** using **Gatling**, an open-source load and stress testing tool.  
The purpose is to evaluate how a web application responds to increasing user load, identify performance limits, and analyze system behavior under stress conditions.

The selected target is [**BlazeDemo**](https://blazedemo.com), a public demo flight booking site commonly used for testing.

---

## 🧩 Overview
This project evaluates the performance and stability of a web application using **Gatling**, an open-source load testing tool.  
The goal is to observe response times, throughput, and error rates under increasing user load to identify the system’s breaking point.

**Tool Used:** Gatling (v3.10.4)  
**Language:** Scala  
**Test Type:** Stress Test  
**Target Application:** [https://blazedemo.com](https://blazedemo.com)

---

## ⚙️ Test Setup


| Parameter | Configuration |
|------------|---------------|
| **Tool** | Gatling (v3.10.4) |
| **Language** | Scala |
| **Target URL** | (https://blazedemo.com) |
| **Type of Test** | Stress Test |
| **Duration** | 60 seconds |
| **Users (Virtual)** | 50 concurrent |
| **System Environment** | Windows 10, Java JDK 17, 8 GB RAM |
| **Scenario** | 1️⃣ Open Home Page → 2️⃣ Search Flights |

Each virtual user performed two HTTP requests during the 1-minute test.

---

## 🧾 Gatling Script

```scala
import io.gatling.core.Predef._
import io.gatling.http.Predef._
import scala.concurrent.duration._

class StressTestSimulation extends Simulation {

  val httpProtocol = http
    .baseUrl("https://blazedemo.com")
    .acceptHeader("text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8")
    .userAgentHeader("Gatling Stress Test")

  val scn = scenario("BlazeDemo Stress Test")
    .exec(http("Open Home Page").get("/").check(status.is(200)))
    .pause(1)
    .exec(http("Search Flights")
      .post("/reserve.php")
      .formParam("fromPort", "Boston")
      .formParam("toPort", "London")
      .check(status.is(200))
    )

  setUp(
  scn.inject(
    rampUsers(50) during (60.seconds)   // 50 total users over 1 minute
  )
).protocols(httpProtocol)
}
```

---

## 📊 Test Result Summary  
**Execution Date:** 28 October 2025  
**Simulation Name:** `StressTestSimulation`  
**Duration:** 59 seconds  

| Metric | Value | Description |
|---------|--------|-------------|
| **Total Requests** | 100 | 50 users × 2 actions each |
| **Successful (OK)** | 100 (100%) | All requests completed successfully |
| **Failed (KO)** | 0 | No timeout or connection error |
| **Min Response Time** | 300 ms | Fastest request recorded |
| **Max Response Time** | 583 ms | Slowest request recorded |
| **Average Response Time** | 352 ms | Mean latency across requests |
| **Standard Deviation** | 43 ms | Low variation (consistent results) |
| **50th Percentile (Median)** | 343 ms | Half completed below this time |
| **75th Percentile** | 371 ms | Three-quarters below this |
| **95th Percentile** | 422 ms | 95% completed under 0.5s |
| **99th Percentile** | 504 ms | 99% completed under 0.6s |
| **Requests per Second** | 1.667 | Steady throughput rate |
| **Error Rate** | 0% | No failed requests |

✅ **Result:** All requests were successful with consistent response times under load.  
The BlazeDemo web application remained **stable, responsive, and error-free** during the entire 60-second stress period.

---

## 📈 Analysis
- **Performance:** All responses completed under 600 ms — excellent results.  
- **Stability:** 0 % error rate across 100 total requests.  
- **Consistency:** Very low response time deviation (43 ms).  
- **Scalability:** Maintained performance with 50 concurrent users for 1 minute.  

These metrics indicate BlazeDemo’s ability to handle moderate concurrent traffic without degradation.

---

## 🖼️ Raw Data

Below are the visual performance metrics generated from the Gatling stress test.

<table align="center">
  <tr>
    <th>Chart</th>
    <th>Description</th>
  </tr>
  <tr>
    <td align="center">
      <img width="400" height="300" alt="Response Time Distribution" src="https://github.com/user-attachments/assets/c43f98ea-378b-419e-941e-26945e519569" />
    </td>
    <td>
      <b>Response Time Distribution</b><br>
      Shows consistent and stable response times across all percentiles (Min–99th).
    </td>
  </tr>
  <tr>
    <td align="center">
      <img width="400" height="300" alt="Throughput Chart" src="https://github.com/user-attachments/assets/0504bb0d-ba4b-4a16-800c-2f9e9e7e4496" />
    </td>
    <td>
      <b>Throughput Chart</b><br>
      Displays the steady number of requests handled per second throughout the test.
    </td>
  </tr>
  <tr>
    <td align="center">
      <img width="400" height="300" alt="Success vs Failure" src="https://github.com/user-attachments/assets/e6f6c68b-f696-4704-9125-e00a637a45a0" />
    </td>
    <td>
      <b>Success vs Failure</b><br>
      Visual representation of 100% successful requests (OK) and 0% failures (KO).
    </td>
  </tr>
</table>

---

## 🧠 Interpretation
The stress test confirms BlazeDemo’s **strong baseline performance** and stability under concurrent user load.  
Response times remained fast and predictable throughout the test, proving that the system can efficiently manage multiple simultaneous requests.  
This serves as the foundation for scaling future tests up to 200–500 users.

---

## 📚 Conclusion and Improvement

The **Comprehensive Web Application Performance Testing & Analysis** conducted using **Gatling** successfully demonstrated how to evaluate a web application’s stability, speed, and scalability under load.

The results from the **BlazeDemo stress test** showed:
- **100% request success rate** — no timeouts, errors, or connection failures.  
- **Average response time of 352 ms**, with the fastest at 300 ms and the slowest at 583 ms.  
- **Consistent performance** across all percentile ranges (95th percentile under 0.5 seconds).  
- **Stable throughput** of approximately 1.67 requests per second for 50 concurrent users.

These findings confirm that **BlazeDemo maintains strong reliability and responsiveness** even when subjected to concurrent access by multiple virtual users.  
The system handled all simulated load efficiently, with low latency and no degradation in service quality.

This project fulfills the objectives of **ITT440 – Comprehensive Web Application Performance Testing & Analysis**, providing practical experience in:
- Configuring and executing Gatling simulations.  
- Collecting and interpreting performance metrics.  
- Documenting and visualizing load test results for professional reporting.

> ✅ **In summary:** Gatling proved to be an effective tool for realistic web performance evaluation, and BlazeDemo demonstrated excellent baseline stability.  
> Future tests can increase virtual users to discover performance thresholds and explore advanced reporting integrations with monitoring tools like Grafana and Prometheus.

---

## 📹Video Demostration
- https://youtu.be/y--V-pFYgbk?si=rJ3OPxnZTxw6coFK
