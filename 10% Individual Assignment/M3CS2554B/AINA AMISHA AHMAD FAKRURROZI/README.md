### Evaluating QuickPizza’s Scalability with Grafana K6
---
### Name: Aina Amisha Binti Ahmad Fkarurrozi
### Matrice No: 2024541935
### Class: M3CS2554B
---

## 🔧 Tool Selection
- **Tool**: Grafana K6
- **Reason**: Lightweight, scriptable, CLI-based, ideal for automated performance testing

## 🌐 Target Application
- **URL**: https://quickpizza.grafana.com
- **Justification**: Public, stable, and ethically safe for testing

## 🎯 Hypothesis
QuickPizza’s web application will maintain a 95th percentile response time below 500 milliseconds and a request failure rate below 1% when subjected to 200 shared iterations across 10 virtual users within a 10-second window.

## 🧪 Test Setup
Tool: K6 by Grafana
Scenario: shared-iterations

## ⚙️ Test Environment
- **System**: Windows 11
- **K6 Version**: v1.3.0
- **Script Location**: `stress-test.js`

## 📈 Stress Test Configuration
```javascript
export const options = {
  scenarios: {
    example_scenario: {
      executor: 'shared-iterations',
      startTime: '10s',
      gracefulStop: '5s',
      vus: 10,
      iterations: 200,
      maxDuration: '10s',
    }
  }
};

```
## 🖥️ CLI Output
<img width="1892" height="667" alt="image" src="https://github.com/user-attachments/assets/6921ceb7-bee5-4490-a0ed-8547f77a6a18" />

## 📈 Metrics to Observe
| **Metric** |	**Expected Threshold** |
|------------|-------------------------|
|Response Time (p95)	| < 500 ms |
|HTTP Request Failures	| < 1% |
|Checks Passed	| 100% |
|Data Received/Sent	| Reasonable bandwidth |

## 📊 Results Summary
| 📊 **Metric**             | **Value**            |
|--------------------------|----------------------|
| Method                   | GET                  |
| Status                   | 200 OK               |
| Total Requests (Count)   | 300                  |
| Minimum Response Time    | 310 ms               |
| Average Response Time    | 1.75 s               |
| Standard Deviation       | 0.89 s               |
| 95th Percentile (p95)    | 2.99 s               |
| 99th Percentile (p99)    | 3.20 s               |
| Virtual Users (VUs)      | 10                   |
| Scenario                 | default              |

## 🔍 Interpretation
QuickPizza handled the load efficiently with no failures.

Response times stayed within acceptable limits.

The system is ready for moderate traffic spikes.

## 🛠️ Recommendations

## 🎥 Video Walkthrough

