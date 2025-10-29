# Web Application Configuration Comparison Testing using K6

**By:** NORLIYANA MOHD ALI

**Class:** M3CS2554C

**Course Code:** ITT440 (10% Individual Assignment)

---

## 🎯 Title & Objective

**Title:** Configuration Comparison Performance Testing on ReqRes API using K6

**Objective:**
To design, execute, and analyze two different load configurations on the ReqRes API using the **K6 performance testing tool**.
This test aims to compare system performance, focusing on response time and throughput between **low** and **high** virtual user configurations.

---

## ⚙️ Tool Justification (Why K6)

K6 is a modern, open-source performance testing tool for APIs and web applications.
It supports scripting in JavaScript, outputs results to CSV for analysis, and integrates well with visualization tools like Python and Grafana.

**Reasons for choosing K6:**

* Lightweight and CLI-based (perfect for Linux environments).
* Simple JavaScript scripting for flexibility.
* Provides accurate and exportable performance metrics.
* Works smoothly in **Kali Linux on VMware**.

---

## 🧪 Test Type & Hypothesis

**Test Type:** Configuration Comparison Testing

**Hypothesis:**
When increasing the number of virtual users (VUs) from **5 to 20**,
the **response time** of the ReqRes API will increase,
and the **throughput (requests per second)** will change depending on server capacity.

---

## 🌐 Target Application Description

**Target URL:** [https://reqres.in](https://reqres.in)

**Description:** ReqRes is a free, public REST API designed for testing and front-end prototyping.
It provides endpoints for simulating typical API responses for GET and POST requests.

---

## 🧩 Test Scripts (JavaScript Files)

### 🔹 `k6_low.js` (Low Configuration)

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

### 🔹 `k6_high.js` (High Configuration)

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

## 💻 Execution Environment (Kali Linux + VMware)

All commands were executed inside **Kali Linux (VMware)** terminal.

### Installation:

```bash
sudo apt update
sudo apt install -y k6 python3 python3-pip
pip install pandas matplotlib
```

---

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

| Command                  | Description                                | Output                                      |
| ------------------------ | ------------------------------------------ | ------------------------------------------- |
| `--vus`                  | Number of virtual users                    | 5 or 20                                     |
| `--duration`             | Duration of test                           | 30 seconds                                  |
| `--out csv=`             | Export metrics to CSV                      | `k6_low_results.csv`, `k6_high_results.csv` |
| `python3 k6_analysis.py` | Analyze both CSV files and generate charts | PNG charts                                  |

---

## 📊 Analysis Script (Python)

### `k6_analysis.py`

This Python script automatically reads the two CSV files, cleans the data, compares metrics, and creates two visual charts:

* `response_time_chart_fixed.png`
* `throughput_chart_fixed.png`

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

---

## 📈 Sample Output Charts

**Response Time Comparison**
![response\_time\_chart\_fixed.png](https://github.com/user-attachments/assets/example-response.png)

**Throughput Comparison**
![throughput\_chart\_fixed.png](https://github.com/user-attachments/assets/example-throughput.png)

---

## 🧠 Analysis & Discussion

* Increasing from **5 VUs** to **20 VUs** caused higher average response time.
* Throughput improved but eventually stabilized due to API limits.
* ReqRes API handled load consistently without failure.
* Data visualizations confirmed stable but throttled (HTTP 429) responses at higher loads.

---

## 💡 Recommendations

1. Try longer test durations (1–5 minutes) for more stable averages.
2. Increase users gradually (e.g., 10, 50, 100 VUs).
3. Integrate results with Grafana or InfluxDB for live dashboards.
4. Avoid excessive hits to public APIs; use custom endpoints for realistic testing.

---

## 🏁 Conclusion

The **ReqRes API** maintained stable performance during **K6 configuration comparison testing** on **Kali Linux (VMware)**.
The analysis showed predictable response time growth under heavier load, proving the test environment and tool configuration worked successfully.

---

## 🎥 YouTube Demo Link

📺 *(Insert your demo link here)*

---

## 🧾 References

* [K6 Official Documentation](https://k6.io/docs/)
* [ReqRes API Documentation](https://reqres.in/)
* [Pandas Documentation](https://pandas.pydata.org/docs/)
* [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)
