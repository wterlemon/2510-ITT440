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
// Include your script here or link to it
