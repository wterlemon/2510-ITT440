# MUHAMMAD HAZIQ BIN AZMAN
# 🧪 Soak Test Report – BlazeDemo using Locust

## 📋 Test Overview

**Objective:**  
To evaluate the performance and stability of the BlazeDemo website under continuous load using **Locust**.

**Test Type:**  
Soak Test (30 minutes continuous load)

**Tool Used:**  
[Locust](https://locust.io)

**Target URL:**  
https://blazedemo.com

**Script Used:**  
`blazedemo_soak.py`

---

## ⚙️ Test Configuration

| Parameter | Value |
|------------|--------|
| Number of Users | 50 concurrent users |
| Spawn Rate | 2 users/second |
| Duration | 30 minutes |
| Host | `https://blazedemo.com` |
| Request Types | `GET` (Home, ChooseFlight, SearchFlights), `POST` (Purchase) |

---

## 📈 Results Summary

### Locust Dashboard (After 30 Minutes)

![Locust Results](ae990588-556d-4b7c-99e1-6b7c3211410c.png)

| Metric | Value |
|--------|--------|
| Total Requests | 13,707 |
| Average Response Time | **328.95 ms** |
| 95th Percentile | **360 ms** |
| Maximum Response Time | **1915 ms** |
| Current RPS | **18.2 requests/sec** |
| Failure Rate | **0%** |

---

## ⏱ Before vs After 30 Minutes

| Metric | Initial (First 5 Min) | After 30 Min | Observation |
|--------|------------------------|---------------|--------------|
| Active Users | 10–50 | 50 | Load maintained steadily |
| Avg Response Time | ~320 ms | ~329 ms | Very stable |
| 95th Percentile | ~350 ms | ~360 ms | Minor increase, acceptable |
| Max Response Time | ~1000 ms | ~1900 ms | Slight spike, still tolerable |
| Requests per Second | 5–10 RPS | ~18 RPS | Stable throughput |
| Failures | 0% | 0% | Excellent reliability |

---

## 🔍 Analysis

### Before the Test (0–5 minutes)
- Users gradually ramped up from 0 to 50.  
- RPS increased steadily as load built up.  
- Response times stabilized around 300 ms.  
- No failures were observed — the system handled the initial load smoothly.

### After 30 Minutes
- Performance remained **consistent and stable**.  
- Average response time stayed below 350 ms.  
- RPS maintained at 18/sec with no drops.  
- No failed requests or timeouts occurred.  
- The system showed **no performance degradation** over time.

---

## ✅ Conclusion

The BlazeDemo application successfully withstood **30 minutes of sustained load** from 50 concurrent users without performance issues.

**Key Takeaways:**
- Stable average response times (~330 ms)
- 0% error rate
- Consistent throughput
- No signs of memory or performance degradation

**Verdict:**  
✅ The system is **stable, scalable, and reliable** under continuous usage.

---

## 🧰 Example Command Used

```bash
locust -f blazedemo_soak.py --host https://blazedemo.com

