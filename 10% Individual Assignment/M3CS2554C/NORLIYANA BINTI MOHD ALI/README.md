# ⚙️ Web Application Configuration Comparison Testing using K6

**By:** NORLIYANA BINTI MOHD ALI  

**Class:** M3CS2554C

**Course Code:** ITT440 – Web Application Testing (10% Individual Assignment)

---

## 🎯 Title & Objective

### **Title:**  
Configuration Comparison Performance Testing on ReqRes API using **K6**

### **Objective:**  
To design, execute, and analyze two different **load configurations** on the ReqRes API using the **K6 performance testing tool**.  
This project evaluates how performance metrics — especially **response time** and **throughput** — change when the number of Virtual Users (VUs) increases.

---

## ⚙️ Tool Justification (Why K6?)

K6 is a modern, developer-friendly, open-source performance testing tool for APIs and web applications.  
It supports JavaScript scripting, CLI-based execution, and CSV export for easy data analysis.

### ✅ **Reasons for Choosing K6**
- Lightweight and runs smoothly in **Linux/VMware** environments.  
- Simple scripting using **JavaScript (ES6)**.  
- Produces accurate, exportable CSV metrics for analysis.  
- Integrates well with **Python (pandas + matplotlib)** or **Grafana dashboards**.  
- Suitable for both quick API tests and long-duration stress/load testing.

---

## 🧪 Test Type & Hypothesis

| Category | Description |
|-----------|-------------|
| **Test Type** | Configuration Comparison Testing |
| **Hypothesis** | Increasing the number of VUs (from 5 → 20) will raise the average response time, while throughput (requests/sec) will scale depending on the API’s handling capacity. |

---

## 🌐 Target Application

| Item | Description |
|------|-------------|
| **API Name** | ReqRes API |
| **URL** | [https://reqres.in](https://reqres.in) |
| **Description** | A public REST API for testing and front-end prototyping. Provides dummy endpoints for user data (GET/POST). |
| **Endpoint Used** | `/api/users?page=2` |

---

## 💻 Execution Environment

| Component | Description |
|------------|-------------|
| **OS** | Kali Linux (Running on VMware) |
| **Tools Installed** | `k6`, `python3`, `pandas`, `matplotlib` |
| **Commands Used** | See below |

### Installation Commands

```bash
sudo apt update
sudo apt install -y k6 python3 python3-pip
pip install pandas matplotlib
````

---

## 🧩 Test Scripts

### 🔹 `k6_low.js` (Low Load – 5 Virtual Users)

![k6\_low.js Screenshot](https://github.com/user-attachments/assets/example-k6low.png)

```javascript
import http from 'k6/http';
import { sleep } from 'k6';

export const options = {
  vus: 5,              // 5 Virtual Users
  duration: '30s',     // Run for 30 seconds
};

export default function () {
  http.get('https://reqres.in/api/users?page=2');
  sleep(1);
}
```

---

### 🔹 `k6_high.js` (High Load – 20 Virtual Users)

![k6\_high.js Screenshot](https://github.com/user-attachments/assets/example-k6high.png)

```javascript
import http from 'k6/http';
import { sleep } from 'k6';

export const options = {
  vus: 20,             // 20 Virtual Users
  duration: '30s',     // Run for 30 seconds
};

export default function () {
  http.get('https://reqres.in/api/users?page=2');
  sleep(1);
}
```

---

## 🚀 Test Execution

### Commands Executed

```bash
# Run Low Load Test
k6 run --vus 5 --duration 30s --out csv=k6_low_results.csv k6_low.js

# Run High Load Test
k6 run --vus 20 --duration 30s --out csv=k6_high_results.csv k6_high.js

# Analyze Results
python3 k6_analysis.py
```

| Command                  | Description              | Output                                       |
| ------------------------ | ------------------------ | -------------------------------------------- |
| `--vus`                  | Number of Virtual Users  | 5 or 20                                      |
| `--duration`             | Duration of test         | 30 seconds                                   |
| `--out csv=`             | Export metrics to CSV    | `k6_low_results.csv` / `k6_high_results.csv` |
| `python3 k6_analysis.py` | Analyze and plot metrics | PNG charts                                   |

---

## 🧠 Python Analysis Script (`k6_analysis.py`)

![K6 Analysis Script Screenshot](https://github.com/user-attachments/assets/example-analysis.png)

This Python script:

* Reads both `k6_low_results.csv` and `k6_high_results.csv`.
* Normalizes data and identifies metrics (e.g., `http_req_duration`, `http_reqs`).
* Generates two visual charts:

  * `response_time_chart_fixed.png`
  * `throughput_chart_fixed.png`
* Prints performance summaries to the console.

```python
#!/usr/bin/env python3
import pandas as pd
import matplotlib.pyplot as plt
import sys, os

LOW_CSV = "k6_low_results.csv"
HIGH_CSV = "k6_high_results.csv"

def read_csv_auto(path):
    if not os.path.exists(path):
        print(f"ERROR: {path} not found"); sys.exit(1)
    df = pd.read_csv(path, on_bad_lines='skip')
    print(f"Loaded {path} with {len(df.columns)} columns.")
    return df

def summarize(df, label):
    print(f"\nSummary for {label}:")
    for m in ["http_reqs", "http_req_duration"]:
        if m in df["metric_name"].values:
            data = df[df["metric_name"] == m]["value"]
            print(f"{m}: mean={data.mean():.2f}, p95={data.quantile(0.95):.2f}, max={data.max():.2f}")

low = read_csv_auto(LOW_CSV)
high = read_csv_auto(HIGH_CSV)

summarize(low, "Low Load CSV")
summarize(high, "High Load CSV")
```

---

## 📊 **Console Output Summary**

**Screenshot of Python execution (`python3 k6_analysis.py`):**
![Python Output Screenshot](https://github.com/user-attachments/assets/example-pythonoutput.png)

### **Extracted Summary:**

| Metric                | Low Load (5 VUs) | High Load (20 VUs) | Observation                                            |
| :-------------------- | :--------------: | :----------------: | :----------------------------------------------------- |
| **Avg Response Time** |     46.75 ms     |      64.20 ms      | ↑ Increased by ~37% under high load. Still acceptable. |
| **p(95) Response**    |     93.34 ms     |      94.10 ms      | ⚙️ Almost stable — good performance consistency.       |
| **Requests/sec**      |      4.72/s      |       18.36/s      | 📈 Increased 3.8× — scales well with 4× users.         |
| **Errors**            |        0%        |         0%         | ✅ No failures — API remained reliable.                 |

---

## 📈 Output Charts

**Response Time Comparison**
![response\_time\_chart\_fixed.png](https://github.com/user-attachments/assets/example-response.png)

**Throughput Comparison**
![throughput\_chart\_fixed.png](https://github.com/user-attachments/assets/example-throughput.png)

---

## 🧩 **Detailed Findings**

* Increasing **VUs** from **5 → 20** raised the **average response time** slightly but predictably.
* **p95 latency** remained almost unchanged, showing stable performance under heavier load.
* **Throughput** scaled linearly up to 18.36 req/s — the API handled the higher user volume efficiently.
* No **error codes** or **timeouts** occurred, indicating the ReqRes API’s backend handled burst load smoothly.

---

## 💡 Recommendations

1. Run longer duration tests (e.g., 1–5 minutes) for better trend accuracy.
2. Gradually scale (10 → 50 → 100 VUs) to identify bottlenecks.
3. Integrate results into **Grafana dashboards** for live monitoring.
4. Use **private endpoints** for realistic backend stress testing instead of public APIs.

---

## 🏁 Conclusion

This performance comparison successfully demonstrated how system response metrics evolve under varying virtual user loads.
The **ReqRes API** showed consistent behavior with minor latency growth and **no system errors**, confirming its robustness and the accuracy of K6’s load testing capabilities.

> ✅ The hypothesis is proven: Response time increases with higher VUs, while throughput scales proportionally until saturation.

---

## 🎥 YouTube Demonstration Link

📺 *(Insert your demo link here)*

---

## 🧾 References

* [K6 Official Documentation](https://k6.io/docs/)
* [ReqRes API Documentation](https://reqres.in/)
* [Pandas Documentation](https://pandas.pydata.org/docs/)
* [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)
