# 🚀 Web Application Configuration Comparison Testing using K6

**By:** NORLIYANA BINTI MOHD ALI
<br>

**Class:** M3CS2554C
<br>

**Course Code:** ITT440 (10% Individual Assignment)

---

## 🎯 Title & Objective

**Title:** Configuration Comparison Performance Testing on ReqRes API using K6

**Objective:**
To design, execute, and analyze two different load configurations on the **ReqRes API** using the **K6 performance testing tool**.
This test aims to compare system performance, focusing on response time and throughput between **low** and **high** virtual user configurations.

---

## ⚙️ Tool Justification (Why K6)

K6 is a modern, open-source performance testing tool for APIs and web applications. It supports scripting in JavaScript, outputs results to CSV for analysis, and integrates well with visualization tools like Python and Grafana.

**Reasons for choosing K6:**

* **Lightweight and CLI-based** (perfect for Linux environments).
* Simple **JavaScript scripting** for flexibility.
* Provides **accurate and exportable** performance metrics.
* Works smoothly in **Kali Linux on VMware**.

---

## 🧪 Test Type & Hypothesis

**Test Type:** Configuration Comparison Testing

**Hypothesis:**
When increasing the number of virtual users (VUs) from **5 to 20**, the **response time** of the ReqRes API will increase, and the **throughput (requests per second)** will change depending on server capacity.

---

## 🌐 Target Application Description

**Target URL:** [https://reqres.in](https://reqres.in)

**Description:** ReqRes is a free, public REST API designed for testing and front-end prototyping. It provides endpoints for simulating typical API responses for GET and POST requests.

---

## 🧩 Test Scripts (JavaScript Files)

### 🔹 `k6_low.js` (Low Configuration)

```javascript
import http from 'k6/http';
import { sleep } from 'k6';

export const options = {
  vus: 5,        // 5 Virtual Users
  duration: '30s',   // Run for 30 seconds
};

export default function () {
  http.get('[https://reqres.in/api/users?page=2](https://reqres.in/api/users?page=2)');
  sleep(1);
}
````

<img width="1122" height="540" alt="image" src="https://github.com/user-attachments/assets/edc4f5a6-025a-44c7-a484-e6c440a635f1" />

### 🔹 `k6_high.js` (High Configuration)

```javascript
import http from 'k6/http';
import { sleep } from 'k6';

export const options = {
  vus: 20,       // 20 Virtual Users
  duration: '30s',   // Run for 30 seconds
};

export default function () {
  http.get('[https://reqres.in/api/users?page=2](https://reqres.in/api/users?page=2)');
  sleep(1);
}
```

<img width="1243" height="554" alt="image" src="https://github.com/user-attachments/assets/7f4cf914-fa8a-48e3-ab0d-5ddcf9c00265" />

-----

## 📊 Results: Analyze & Compare

| Metric | Low Load (5 VUs) | High Load (20 VUs) | Observation |
| :--- | :---: | :---: | :--- |
| **Avg Response Time** | 46.75 ms | 64.2 ms | Increased by about 17.45 ms (37%) under high load. The service is still fast, but response time is starting to climb. |
| **p(95) Response** | 93.34 ms | 94.1 ms | Remained stable (only a slight increase). This is a good sign, meaning 95% of users still experienced a fast response time, even with $4\times$ the load. |
| **Requests/sec** | 4.72 /s | 18.36 /s | Increased by over $3.8\times$. The system successfully handled significantly higher throughput, closely matching the $4\times$ increase in Virtual Users. |
| **Errors** | 0% | 0% | No failures in either test. The service did not show any signs of reaching a critical error capacity (like a rate limit error 429). |

-----

## 💻 Execution Environment (Kali Linux + VMware)

All commands were executed inside **Kali Linux (VMware)** terminal.

### Installation:

```bash
sudo apt update
sudo apt install -y k6 python3 python3-pip
pip install pandas matplotlib
```

-----

## 🚀 Test Execution Commands

Run each configuration test and export results to CSV:

```bash
# Low configuration test
k6 run --vus 5 --duration 30s --out csv=k6_low_results.csv k6_low.js

# High configuration test
k6 run --vus 20 --duration 30s --out csv=k6_high_results.csv k6_high.js

# Python analysis and chart generation
python3 k6_analysis.py
```

**Explanation:**

| Command | Description | Output |
| :--- | :--- | :--- |
| `--vus` | Number of virtual users | 5 or 20 |
| `--duration` | Duration of test | 30 seconds |
| `--out csv=` | Export metrics to CSV | `k6_low_results.csv`, `k6_high_results.csv` |
| `python3 k6_analysis.py` | Analyze both CSV files and generate charts | PNG charts |

-----

## 📈 Analysis Script (Python)

### `k6_analysis.py`

This Python script automatically reads the two CSV files, cleans the data, compares metrics, and creates two visual charts: `response_time_chart_fixed.png` and `throughput_chart_fixed.png`.

```python
#!/usr/bin/env python3
import pandas as pd
import matplotlib.pyplot as plt
import sys
import os

# --- Configuration ---
LOW_CSV = "k6_low_results.csv"
HIGH_CSV = "k6_high_results.csv"
EXPECTED_COLUMNS = 20  

def read_csv_auto(path):
    if not os.path.exists(path):
        print(f"ERROR: file not found -> {path}")
        sys.exit(1)
    with open(path, 'r') as f:
        header = f.readline().count(',') + 1
        if header != EXPECTED_COLUMNS:
            print(f"WARNING: Header of {path} has {header} columns, expected {EXPECTED_COLUMNS}. Using found count.")
    df = pd.read_csv(path, on_bad_lines='skip') 
    if df.empty:
        print(f"ERROR: CSV file {path} is empty after reading.")
        sys.exit(1)
    print(f"Loaded '{path}' with columns: {list(df.columns)}") 
    return df

def find_col(df, candidates):
    cols = [c for c in df.columns]
    lower = {c.lower(): c for c in cols}
    for cand in candidates:
        if cand.lower() in lower:
            return lower[cand.lower()]
    return None

def normalize(df):
    metric_col = find_col(df, ["metric_name", "metric", "name"])
    timestamp_col = find_col(df, ["timestamp", "time", "t"])
    value_col = find_col(df, ["value", "val", "v"])
    tags_col = find_col(df, ["tags"]) 

    cols_to_select = [metric_col, timestamp_col, value_col]
    new_names = ["metric", "timestamp", "value"]
    if tags_col:
        cols_to_select.append(tags_col)
        new_names.append("tags")
    df = df.loc[:, cols_to_select].copy()
    df.columns = new_names
    df["value"] = pd.to_numeric(df["value"], errors="coerce") 

    sample_series = df["timestamp"].dropna().astype(str)
    if sample_series.empty:
        df["time"] = pd.NaT
    else:
        sample = sample_series.iloc[0]
        try:
            num = float(sample)
            if num > 1e12:
                unit = "ms"
            elif num > 1e9:
                unit = "s"
            else:
                unit = "s"
            df["time"] = pd.to_datetime(df["timestamp"].astype(float), unit=unit, errors="coerce")
        except Exception:
            df["time"] = pd.to_datetime(df["timestamp"], errors="coerce")
    df = df.dropna(subset=["time", "value"])
    return df

def plot_metric(low_df, high_df, metric_name, outpng, ylabel, label_low="Low Config", label_high="High Config"):
    l = low_df[low_df["metric"] == metric_name].copy()
    h = high_df[high_df["metric"] == metric_name].copy()
    if l.empty and h.empty:
        print(f"WARNING: Metric '{metric_name}' not found. Skipping.")
        return
    plt.figure(figsize=(10,5))
    if not l.empty:
        plt.plot(l["time"], l["value"], label=label_low) 
    if not h.empty:
        plt.plot(h["time"], h["value"], label=label_high)
    plt.title(f"k6 Analysis - {metric_name} Comparison")
    plt.xlabel("Time")
    plt.ylabel(ylabel)
    plt.legend()
    plt.grid(True)
    plt.tight_layout()
    plt.savefig(outpng)
    plt.close()
    print(f"Saved chart: {outpng}")

def summarize(df, name):
    print(f"\nSummary for {name}:")
    for m in sorted(df["metric"].unique()):
        if m in ["http_req_duration", "http_reqs"]:
            s = df[df["metric"]==m]["value"]
            print(f"  {m}: mean={s.mean():.2f}, p95={s.quantile(0.95):.2f}, max={s.max():.2f}")

def main():
    low = read_csv_auto(LOW_CSV)
    high = read_csv_auto(HIGH_CSV)
    low_n = normalize(low)
    high_n = normalize(high)
    plot_metric(low_n, high_n, "http_req_duration", "response_time_chart_fixed.png", "Response Time (ms)")
    plot_metric(low_n, high_n, "http_reqs", "throughput_chart_fixed.png", "Requests per second")
    summarize(low_n, "LOW CSV")
    summarize(high_n, "HIGH CSV")

if __name__ == "__main__":
    main()
```

<img width="1226" height="580" alt="image" src="https://github.com/user-attachments/assets/8782025d-dcf6-4d8a-b92c-d13b10f02d9a" />

-----

## 📈 Sample Output Charts

**Response Time Comparison**

<img width="1318" height="652" alt="image" src="https://github.com/user-attachments/assets/52a65c3a-c1f9-4de3-8774-7d9f651d819a" />

**Throughput Comparison**

<img width="1262" height="619" alt="image" src="https://github.com/user-attachments/assets/1d33f42b-2974-4634-94ac-21660d5cf615" />

-----

## 🧠 Analysis & Discussion

  * Increasing from **5 VUs** to **20 VUs** caused a measurable increase in the **average response time**.
  * **Throughput** saw a significant improvement (from $4.72 /s$ to $18.36 /s$), closely matching the $4\times$ load increase, demonstrating good scaling.
  * The **p(95) Response** remained stable, indicating the API is well-optimized and consistent for the majority of users under both loads.
  * The **ReqRes API** handled the load consistently with **0% errors**, showing no critical failures or rate-limiting (HTTP 429) issues during the test.

-----

## 💡 Recommendations

1.  Try longer test durations (1–5 minutes) for more stable averages and to observe long-term performance trends.
2.  Increase virtual users gradually (e.g., 10, 50, 100 VUs) to identify the exact **saturation point** of the API.
3.  Integrate K6 results with **Grafana or InfluxDB** for live, interactive dashboards.
4.  For future realistic testing, consider using custom, private endpoints instead of public APIs to avoid excessive hits.

-----

## 🏁 Conclusion

The **ReqRes API** maintained stable performance during the **K6 configuration comparison testing** executed on **Kali Linux (VMware)**. The analysis confirmed the hypothesis that response time would increase under heavier load, while also demonstrating the system's strong ability to handle significantly higher throughput without generating errors. The test environment and tool configuration worked successfully.

-----

## 🎥 YouTube Demo Link

📺 *(Insert your demo link here)*

-----

## 🧾 References

  * [K6 Official Documentation](https://k6.io/docs/)
  * [ReqRes API Documentation](https://reqres.in/)
  * [Pandas Documentation](https://pandas.pydata.org/docs/)
  * [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)



```
```
