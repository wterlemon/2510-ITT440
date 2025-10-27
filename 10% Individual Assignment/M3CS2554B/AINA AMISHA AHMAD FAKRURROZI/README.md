### Wikipedia Stress Test with Grafana K6
---
### Name: Aina Amisha Binti Ahmad Fkarurrozi
### Matrice No: 2024541935
### Class: M3CS2554B
---
# Wikipedia Stress Test with Grafana K6

## 🔧 Tool Selection
- **Tool**: Grafana K6
- **Reason**: Lightweight, scriptable, CLI-based, ideal for automated performance testing

## 🌐 Target Application
- **URL**: https://en.wikipedia.org/wiki/Main_Page
- **Justification**: Public, stable, and ethically safe for testing

## 🎯 Hypothesis
> Wikipedia will maintain stable response times up to 100 virtual users, but may show increased latency or minor failures beyond that threshold.

## 🧪 Test Types Executed
- Stress Test ✅
- Load Test ⏳
- Soak Test ⏳

## ⚙️ Test Environment
- **System**: Windows 11
- **K6 Version**: v1.3.0
- **Script Location**: `stress-test.js`

## 📈 Stress Test Configuration
```javascript
import http from 'k6/http';
import { check, sleep } from 'k6';

const options = {
  stages: [
    { duration: '30s', target: 50 },
    { duration: '1m', target: 100 },
    { duration: '30s', target: 200 },
    { duration: '1m', target: 0 },
  ],
  thresholds: {
    http_req_duration: ['p(95)<500'],
    http_req_failed: ['rate<0.01'],
  },
};

export default function () {
  let res = http.get('https://en.wikipedia.org/wiki/Main_Page');
  check(res, {
    'status is 200': (r) => r.status === 200,
    'body size > 10KB': (r) => r.body.length > 10_000,
  });
  sleep(1);
}

```
## 🖥️ CLI Output
<img width="1200" height="916" alt="image" src="https://github.com/user-attachments/assets/ed17ee76-3818-4d55-b07b-4bbd4e2a42a8" />

Figure 1: CLI output from K6 stress test on Wikipedia


## 📊 Results Summary
Metric	Value
Total HTTP Requests	1
Checks Passed	2 / 2 (100%)
Checks Failed	0
Data Received	243 kB
Data Sent	12 kB
Virtual Users (VUs)	1
Max VUs	1
Response Time (avg)	324.18 ms
Response Time (p95)	324.18 ms
HTTP Request Failures	0.00%
## 🔍 Interpretation
Stability: The Wikipedia main page responded successfully with a 200 status code and passed all checks, indicating stable behavior under minimal load.

Latency: The average response time of ~324 ms is well within acceptable limits for public web applications.

Reliability: No failed requests were recorded, suggesting strong availability and fault tolerance at this load level.

Scale Limitation: With only 1 virtual user and 1 request, this test does not yet simulate stress conditions. It serves as a functional baseline.

## 🛠️ Recommendations

## 🎥 Video Walkthrough

