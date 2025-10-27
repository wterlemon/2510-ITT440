# AINA AMISHA AHMAD FAKRURROZI
```markdown
# 📊 Load Testing on Wikipedia using Grafana K6

**Name:** AINA AMISHA BINTI AHMAD FAKRURROZI
**Matrix ID:** 2024541935
**Class:** M3CS2554B  

---

## 🧠 Introduction

This performance testing project was conducted using **Grafana K6**, a modern open-source load testing tool built for developers. The goal was to evaluate the performance and stability of the **Wikipedia homepage** under simulated user load. K6 was chosen for its scripting flexibility, CLI-based execution, and ability to export results in JSON format for further analysis.

The test simulated virtual users accessing the Wikipedia homepage using a simple GET request. Metrics such as request count, response time, and error rate were collected and exported for visualization and reporting.

---

## 🎯 Objectives

- Evaluate the performance and responsiveness of Wikipedia under simulated load  
- Measure key metrics: request count, response time, error rate, and throughput  
- Export and convert test results into CSV and HTML formats for analysis  
- Demonstrate the use of K6 scripting, CLI execution, and result processing  
- Showcase integration with tools like Node.js and json2csv for data transformation

---

## 🛠️ Tool and Target Site Selection

| Category              | Description                                                                 |
|-----------------------|------------------------------------------------------------------------------|
| Tool Name             | Grafana K6                                                                  |
| Test Type             | Load Test                                                                    |
| Runtime Environment   | Node.js v22.2.1                                                              |
| Target Website        | [Wikipedia](https://www.wikipedia.org)                                      |
| Reason for Selection  | Stable, high-traffic, publicly accessible site for real-world performance testing |

---

## ⚙️ Test Setup and Configuration

| Configuration Item         | Details                        |
|----------------------------|--------------------------------|
| Protocol Used              | HTTPS                          |
| Server Name or IP          | www.wikipedia.org              |
| HTTP Method                | GET                            |
| Path                       | /                              |
| Virtual Users              | 5                              |
| Duration                   | 10s                            |
| Output Format              | JSON                           |
| Export Tools               | Node.js, json2csv              |
| Result Conversion          | CSV and HTML                   |

The test script was written in JavaScript and executed using the K6 CLI. It simulated five virtual users sending GET requests to the Wikipedia homepage for 10 seconds. The results were saved in `results.json`, then converted to `results.csv` and `results.html` using Node.js scripts.

---

## 🚀 Test Execution Steps

| Step | Description |
|------|-------------|
| 1    | Install K6 and Node.js on Windows |
| 2    | Write K6 test script (`script.js`) targeting Wikipedia |
| 3    | Run test using `k6 run script.js --out json=results.json` |
| 4    | Install `json2csv` using `npm install json2csv` |
| 5    | Create `convert.js` to transform JSON to CSV |
| 6    | Create `convert-html.js` to transform JSON to HTML |
| 7    | Run `node convert.js` and `node convert-html.js` to generate visual outputs |
| 8    | Analyze results using Excel or browser |

---

## 📈 Sample Test Results

| Metric               | Value          | Description |
|----------------------|----------------|-------------|
| Total Requests       | 1200           | Number of HTTP requests sent during the test |
| Avg Response Time    | 2153 ms        | Average time per request |
| Min Response Time    | 608 ms         | Fastest response |
| Max Response Time    | 6002 ms        | Slowest response |
| Error Rate           | 0%             | No failed requests |
| Throughput           | 1.2 req/sec    | Requests handled per second |
| Avg Bytes            | 1040.2 bytes   | Average size of response |

---

## 🧠 Interpretation and Bottlenecks

- All requests completed successfully with **0% error**
- Average response time of **2.15s** indicates stable performance
- Maximum response time of **6s** suggests occasional latency
- Throughput of **1.2 req/sec** confirms consistent handling of load
- JSON output enabled flexible post-processing and visualization

---

## 🛠️ Recommendations

- Use caching to reduce repeated request latency  
- Optimize server-side logic for better scalability  
- Consider CDN integration for global performance improvements  

---

## ✅ Conclusion

This test demonstrates that **Grafana K6** is an effective tool for simulating user load and analyzing web performance. The Wikipedia homepage remained stable and responsive under the configured load, and the exported results provided clear insights into system behavior. The integration with Node.js and conversion tools allowed for flexible reporting and visualization.

---

## 🎥 Demonstration Video

Watch the full test execution and result analysis on YouTube:  
🔗 
```

---
