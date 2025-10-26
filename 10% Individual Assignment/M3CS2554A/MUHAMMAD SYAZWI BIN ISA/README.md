# ITT440 - Web Application Performance Testing

**Name:** [MUHAMMAD SYAZWI BIN ISA]  
**Matrix No:** [2024783361]  
**Tool:** k6  
**Test Type:** Spike Test  


## 📊 Executive Summary

This project demonstrates web application performance testing using **k6** to conduct a **Spike Test** on the JSONPlaceholder API. The test successfully simulated a sudden traffic surge to evaluate the API's performance under stress conditions.

## 🛠 Tools and Technologies

| Component | Technology |
|-----------|------------|
| **Testing Tool** | k6 v0.45.0 |
| **Application Under Test** | JSONPlaceholder REST API |
| **Test Type** | Spike Test |

## 🎯 Test Objectives

- Evaluate API response under sudden load spikes
- Measure response time degradation  
- Identify system breaking points
- Analyze error rates during traffic surges

## 📈 Test Configuration

### Load Pattern (Spike Test)
```javascript
export const options = {
  stages: [
    { duration: '1m', target: 100 },   // Rapid ramp-up
    { duration: '30s', target: 100 },  // Sustained peak
    { duration: '30s', target: 0 },    // Cool-down
  ],
};
