# Name : MUHAMMAD HAZIQ BIN AZMAN  
## Matric No : 2024752489   
## Class : M3CS2554A
# 🧪 BlazeDemo Soak Test using Locust

---

## 📘 1. Introduction

Modern web applications must perform reliably under continuous user activity.  
This project evaluates the **performance, stability, and endurance** of the [BlazeDemo](https://blazedemo.com) web application using **Locust**, a Python-based performance testing framework.

The goal is to analyze how the application behaves under **sustained load** and identify any performance degradation, latency spikes, or failure points during a 30-minute soak test.

---

## 🎯 2. Hypothesis

> It is hypothesized that BlazeDemo will maintain **stable performance** with consistent response times and no critical failures under a continuous load of **50 concurrent users** for **30 minutes**, although minor latency spikes may occur due to backend or network factors.

This hypothesis sets the performance expectation before the soak test execution.

---

## 🦗 3. Tool Selection & Justification

### **Selected Tool:** [Locust](https://locust.io)

Locust was chosen as the performance testing tool due to its **flexibility**, **real-time monitoring**, and **Python-based scripting** capabilities.

| Feature | Description |
|----------|--------------|
| 🐍 **Python-based scripting** | Enables easy customization of user scenarios using Python. |
| 📊 **Real-time dashboard** | Provides live feedback on metrics such as response time, throughput, and failure rate. |
| ⚙️ **Lightweight & scalable** | Supports distributed load generation across multiple systems. |
| 🌐 **Web-based UI** | Interactive web interface for controlling and monitoring tests. |
| 💡 **Open Source** | Freely available, widely adopted by developers and QA engineers. |

### **Comparison with Alternatives**

| Tool | Pros | Cons |
|------|------|------|
| **Apache JMeter** | Mature, feature-rich, supports multiple protocols | GUI-heavy, less scripting flexibility |
| **K6** | Lightweight, modern scripting (JavaScript) | Lacks built-in UI for live test monitoring |
| **Artillery** | Simple YAML configuration | Limited dashboard and reporting features |

✅ **Conclusion:** Locust offers the best balance between **usability**, **scalability**, and **visual feedback**, making it ideal for this test.

---

## ⚙️ 4. Test Configuration

| Parameter | Value |
|------------|--------|
| 🧍 Number of Users | 50 concurrent users |
| 🚀 Spawn Rate | 2 users/second |
| ⏱ Duration | 30 minutes |
| 🌍 Host | `https://blazedemo.com` |
| 🔁 Request Types | `GET` (Home, ChooseFlight, SearchFlights), `POST` (Purchase) |

---

## 📊 5. Locust Dashboard Results

### 📸 Detailed Request Breakdown (After 30 Minutes)
<img width="1446" height="387" alt="image" src="https://github.com/user-attachments/assets/73439766-09bd-43f4-832e-31a6893e1d27" />   






| Type | Endpoint | # Requests | # Fails | Avg (ms) | Min (ms) | Max (ms) | Avg Size (bytes) | RPS | Failures/s |
|------|-----------|------------|----------|-----------|-----------|-----------|------------------|-----|-------------|
| GET | ChooseFlight | 5,230 | 0 | 328.98 | 289 | 1,317 | 6,432 | 2.91 | 0 |
| GET | Home | 13,181 | 0 | 323.66 | 282 | 1,915 | 4,474 | 7.32 | 0 |
| POST | Purchase | 2,676 | 0 | 330.41 | 291 | 1,367 | 6,432 | 1.49 | 0 |
| GET | SearchFlights | 10,463 | 0 | 323.63 | 284 | 1,847 | 6,962 | 5.81 | 0 |
| **Aggregated** | — | **31,550** | **0** | **325.10** | **282** | **1,915** | **5,789.75** | **17.53** | **0** |

---

### 🔎 Endpoint Performance Analysis

- **Home Page (GET)** — Handled the highest number of requests (13,181) with a low average latency of **~323 ms**.  
- **SearchFlights (GET)** — Slightly higher average request time (**~324 ms**) but consistent throughput.  
- **ChooseFlight (GET)** — Stable average of **~329 ms** with no failures.  
- **Purchase (POST)** — Heavier payload (~6.4 KB) but maintained fast response (**~330 ms**) and 0% failure rate.  
- **Aggregate Throughput:** ~17.5 requests/second, showing steady sustained performance.  
- **Failure Rate:** 0% — all endpoints responded successfully.

✅ This confirms that all request types — static (GET) and dynamic (POST) — performed reliably throughout the 30-minute soak test.

---

## ⏱ 6. Before vs After 30 Minutes

| Metric | Initial (0–5 min) | After 30 min | Interpretation |
|--------|--------------------|---------------|----------------|
| 👥 Active Users | 10 → 50 | 50 | Load ramped up smoothly and remained steady |
| ⚡ Avg Response Time | ~320 ms | ~329 ms | System maintained stable response times |
| 📊 95th Percentile | ~350 ms | ~360 ms | Slight increase, within acceptable range |
| 🔺 Max Response Time | ~1,000 ms | ~1,900 ms | Minor spikes but system recovered quickly |
| 🔁 Throughput (RPS) | 5–10 RPS | ~18 RPS | Throughput consistent over time |
| ❌ Failures | 0% | 0% | No errors — high reliability maintained |

---

## 🔍 7. Interpretation & Analysis

### 🟢 **Initial Phase (0–5 Minutes)**
- Gradual user ramp-up from 0 to 50 concurrent users.  
- Response times stabilized around **300–320 ms**, showing efficient ramp-up handling.  
- No errors or crashes occurred.  

### 🔵 **Sustained Load Phase (After 30 Minutes)**
- The system maintained **consistent performance** throughout the test.  
- **Average response time** stayed below **350 ms**, indicating stable resource usage.  
- **95th percentile** values confirm a uniform user experience.  
- **0% failures** prove excellent backend reliability.  
- Occasional **response spikes (~1900 ms)** may result from short server-side queueing or garbage collection.

### 🧠 **Interpretation Summary**
- 🟩 **Stable performance:** Consistent response times with minimal fluctuation.  
- 🟩 **Zero failure rate:** Every request succeeded.  
- 🟨 **Minor latency spikes:** Non-critical and within expected tolerance.  
- 🟩 **Excellent endurance:** No degradation or instability detected.

---

## ✅ 8. Conclusion

The **BlazeDemo** web application successfully sustained a **30-minute soak test** under **50 concurrent users** with **0% failure rate**.

### 🏁 Key Takeaways
- ✅ **Stable Average Response Time:** ~330 ms  
- ✅ **Consistent Throughput:** ~18 RPS  
- ✅ **Zero Errors:** 0% failure rate  
- ✅ **High Reliability:** Maintained stability for entire test duration  

> **Final Verdict:**  
> BlazeDemo is **stable, scalable, and resilient** under continuous user load, with no performance degradation over time.

---

## 💡 9. Suggestions for Improvement

Although BlazeDemo performed strongly, the following optimizations could further enhance scalability and resilience:

### 🧰 **1. Optimize Server-Side Response Handling**
- Investigate occasional **response spikes (~1900 ms)**.  
- Review backend logs for potential **database delays** or **memory issues**.  
- Implement caching (e.g., Redis, Memcached).

### 💾 **2. Improve Database Efficiency**
- Optimize SQL queries and indexing.  
- Enable connection pooling to handle concurrent requests efficiently.

### 🌐 **3. Content Delivery Optimization**
- Use **CDN** for static assets.  
- Enable **HTTP/2** or **gzip compression**.

### 📈 **4. Extended Endurance Testing**
- Run longer soak tests (2–4 hours).  
- Monitor **CPU**, **RAM**, and **database utilization** over time.

### 🧪 **5. Gradual Load Scaling**
- Incrementally increase concurrent users (100 → 200 → 500).  
- Identify performance degradation thresholds.

### 🔒 **6. Application Monitoring**
- Implement **APM tools** like New Relic, Datadog, or Elastic APM.  
- Track **response times**, **memory usage**, and **error logs** continuously.

---

## 🧰 10. Locust Command Used

```bash
locust -f blazedemo_soak.py --host https://blazedemo.com
```

---
## ✅ 11. Report
<img width="1447" height="757" alt="image" src="https://github.com/user-attachments/assets/e461b7ea-d636-41ff-80d1-01678b822494" />   

---

## 📘 12. YouTube Link   
https://youtu.be/tZyY7CANCKE
