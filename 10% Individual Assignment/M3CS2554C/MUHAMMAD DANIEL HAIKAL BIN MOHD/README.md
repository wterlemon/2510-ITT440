# 🧪 WordPress Load Test using BlazeMeter

## 📖 Overview
This project demonstrates a basic **load testing** process on a WordPress website using **BlazeMeter (based on Apache JMeter)**.  
The goal of this test is to analyze how a WordPress site performs under different user loads — focusing on response time, throughput, and error rate.

---

## ⚙️ Test Configuration

| Parameter | Details |
|------------|----------|
| **Tool Used** | BlazeMeter  |
| **Test Type** | URL Test |
| **Target Website** | [https://wp-themes.com/twentytwentyfour/](https://wp-themes.com/twentytwentyfour/) |
| **Number of Virtual Users (VU)** | 10 |
| **Test Duration** | 5 minutes |
| **Location** | Asia Southeast (Singapore, Google) |
| **Ramp-up Time** | Default (BlazeMeter handles automatically) |

---

## 🎯 Test Objectives
- Measure the average response time of the WordPress site.  
- Observe throughput (hits per second).  
- Check for any failed requests or errors during high load.  
- Analyze server behavior during multiple simultaneous connections.

---

## 📊 Test Results

> 📌 *Add your BlazeMeter result screenshots or charts below.*

### 🔹 Summary Report
| Metric | Result |
|---------|---------|
| **Max Users** | `10` |
| **Average Throughput (Hits/s)** | `27.03` |
| **Error Rate** | `0%` |
| **Average Response Time** | `336.32 ms` |
| **90th Percentile Response Time** | `363 ms` |
| **Average Bandwidth** | `3.17 MiB/s` |

🖼️ *Paste summary chart screenshot here*  
`![Summary Chart](./images/summary_chart.png)`

---

### 🔹 Timeline Report (Response Time vs Load)
🖼️ *Paste graph image here*  
`![Timeline Graph](./images/timeline_graph.png)`

---

### 🔹 Request Statistics
🖼️ *Paste chart here if you have request-level details*  
`![Request Stats](./images/request_stats.png)`

---

## 🧠 Analysis
- The average response time stayed below **400 ms**, which indicates that the website handled 10 users efficiently.  
- There were **no errors**, showing good server stability.  
- Throughput (hits per second) remained consistent, meaning the site could sustain the simulated traffic.  
- Overall performance was **stable and responsive** under the given test conditions.

---

## 🚀 Conclusion
The BlazeMeter test results show that the selected WordPress site performs well under a moderate load of 10 virtual users.  
For future improvements, you can:
- Increase the number of users to test scalability.  
- Try running tests from multiple regions.  
- Include login or comment interactions to simulate real user behavior.

---

## Video Demo
