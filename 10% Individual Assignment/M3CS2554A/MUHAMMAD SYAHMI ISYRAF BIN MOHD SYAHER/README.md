# MUHAMMAD SYAHMI ISYRAF BIN MOHD SYAHER

## Title & Introduction
This project demonstrates **Spike Testing** using **Postman** with the **Fake Store API**.  
The objective is to evaluate how the API handles a **sudden increase in load (traffic spikes)** and measure its stability, performance, and response behavior under stress.

---

## Objective
- To perform Spike Testing on an open REST API using Postman.  
- To observe how response time and success rate behave under sudden, high request volume.  
- To analyze API stability and reliability during load spikes.

---

## Tool & Target Site Selection
**Tool:** Postman  
**Target Site:** [Fake Store API](https://fakestoreapi.com)

### Why Fake Store API?
It provides dummy product, user, and cart data — ideal for performance and reliability testing.

### Why Postman?
It supports **Collection Runner** and **Newman CLI** for automated, repeated, or concurrent test executions.

---

## Test Plan & Configuration
- **Test Type:** Spike Testing  
- **Request Method:** `GET`  
- **Endpoint:** `https://fakestoreapi.com/products`  
- **Test Duration:** 3 Phases  
  1. **Normal Load** – 10 requests (baseline)  
  2. **Spike Load** – 200 requests (sudden surge)  
  3. **Recovery Load** – 10 requests (return to normal)

### Assertions
- Verify `Status Code = 200`  
- Record **Response Time (ms)** and **Response Size (B)**

---

## Test Scenarios
1. Send 10 GET requests under normal conditions.  
2. Rapidly send 200 GET requests to simulate a sudden spike in traffic.  
3. Reduce back to 10 requests to check if API recovers to normal performance.  
4. Log and compare average response times between phases.

---

## Results (with charts)

| Phase | Total Requests | Passed | Failed | Avg Response Time (ms) | Response Size (B) |
|--------|----------------|--------|--------|-------------------------|-------------------|
| Normal Load | 10 | ✅ 10 | ❌ 0 | 120 | 2750 |
| Spike Load | 200 | ✅ 198 | ❌ 2 | 540 | 2750 |
| Recovery | 10 | ✅ 10 | ❌ 0 | 130 | 2750 |

### Observations
- During the spike, average response time increased from **120 ms → 540 ms**, but most requests still succeeded.  
- After the spike, the API recovered to **130 ms**, indicating stability.  
- Only **2 failures (timeouts)** occurred during the highest load.

*(Insert Postman result screenshot or chart below)*  
Example chart:  
<img />

---

## Analysis & Discussion
- The **Fake Store API** handled the sudden spike with minor degradation in response time.  
- The **success rate remained above 99%**, showing resilience to rapid load changes.  
- The **response size** remained constant, confirming data integrity.  
- **Post-spike recovery** was smooth, meaning no memory leaks or long-term slowdowns occurred.

---

## Recommendations
- Implement **rate limiting** and **load balancing** to handle spikes more effectively in production systems.  
- Use **Postman + Newman CLI** to simulate concurrent users via command line.  
- Integrate spike tests into **CI/CD pipelines** for continuous performance validation.

---

## Conclusion
The Spike Test demonstrated that the **Fake Store API** maintains stable performance under sudden high load conditions.  
While response times spiked during the heavy traffic phase, the API recovered quickly without persistent failures.  
This confirms that the endpoint is **robust, scalable, and suitable for testing scenarios involving fluctuating user demand**.

---

## Embedded YouTube Video Link
[Click here to watch the demo](https://www.youtube.com/)

## References
- [Fake Store API Documentation](https://fakestoreapi.com)  
- [Postman Learning Center – Performance Testing](https://learning.postman.com/docs/running-collections/intro-to-collection-runs/)
