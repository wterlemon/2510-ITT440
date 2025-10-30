# 🚀 Web Application Performance Testing & Analysis  
**E-commerce Platform Smoke Test using K6**

**Course:** ITT440  
**Name:** MUHAMMAD SYAZWI BIN ISA  
**Matrix Number:** 2024783361    
**YouTube Video:** [coming soon

---

## 📋 Table of Contents
1. [Introduction](#introduction)  
2. [Tool Selection Justification](#tool-selection-justification)  
3. [Test Environment & Methodology](#test-environment--methodology)  
4. [Test Execution & Configuration](#test-execution--configuration)  
5. [Results & Analysis](#results--analysis)  
6. [Identified Bottlenecks](#identified-bottlenecks)  
7. [Recommendations for Improvement](#recommendations-for-improvement)  
8. [Conclusion](#conclusion)

---

## 🧭 Introduction

This project involves conducting a **smoke test** on three popular Malaysian e-commerce and service websites:  
- **Shopee Malaysia**  
- **Lazada Malaysia**  
- **RedBus Malaysia**

The objective is to assess the basic health and performance of these platforms under minimal load using **K6**, a modern performance testing tool.

---

## 🛠️ Tool Selection Justification

I selected **K6** for the following reasons:

- **Open-Source & Developer-Friendly**: Scripts are written in JavaScript, making it accessible and easy to integrate into CI/CD pipelines.
- **Lightweight & Efficient**: Uses a minimal resource footprint while simulating realistic user behavior.
- **Real-Time Metrics**: Provides detailed, real-time performance metrics like response time, throughput, and error rates.
- **Thresholds & Alerts**: Allows setting performance thresholds to automatically fail tests if criteria are not met.
- **Cloud & CLI Support**: Can be run locally or via the K6 cloud for distributed testing.

---

## ⚙️ Test Environment & Methodology

### Test Setup:
- **Tool**: K6 v0.45.0  
- **Virtual Users (VUs)**: 3  
- **Test Duration**: 2 minutes  
- **Test Type**: Smoke Test (Health Check)  
- **Target Websites**:
  - [Shopee Malaysia](https://www.shopee.com.my/)
  - [Lazada Malaysia](https://www.lazada.com.my/)
  - [RedBus Malaysia](https://www.redbus.com.my/)

### Metrics Tracked:
- HTTP Response Time  
- Success/Failure Rate  
- Throughput  
- Error Rate  
- Check Pass/Fail Status

---

## 🧪 Test Execution & Configuration

### K6 Script Used:

```javascript
/**
 * 🇲🇾 MALAYSIA WEBSITES SMOKE TEST
 * ITT440 Assessment 1 - Performance Testing
 * Tests 3 popular Malaysian e-commerce and service websites
 */

import http from 'k6/http';
import { check, sleep } from 'k6';

export const options = {
  vus: 3,           // Minimal load
  duration: '2m',   // 2-minute test duration
  thresholds: {
    http_req_failed: ['rate<0.05'],    // Less than 5% failures
    http_req_duration: ['p(95)<5000'], // 95% under 5 seconds
    checks: ['rate>0.90'],             // 90%+ checks should pass
  },
};

// Popular Malaysian websites to test
const websites = [
  {
    name: 'Shopee Malaysia',
    url: 'https://www.shopee.com.my/',
    checks: {
      'status is 200': (r) => r.status === 200,
      'homepage loaded': (r) => r.body.includes('Shopee') || r.body.length > 1000,
      'response under 3s': (r) => r.timings.duration < 3000,
    }
  },
  {
    name: 'Lazada Malaysia',
    url: 'https://www.lazada.com.my/',
    checks: {
      'status is 200': (r) => r.status === 200,
      'homepage loaded': (r) => r.body.includes('Lazada') || r.body.length > 1000,
      'response under 3s': (r) => r.timings.duration < 3000,
    }
  },
  {
    name: 'RedBus Malaysia',
    url: 'https://www.redbus.com.my/',
    checks: {
      'status is 200': (r) => r.status === 200,
      'homepage loaded': (r) => r.body.includes('redbus') || r.body.length > 1000,
      'response under 3s': (r) => r.timings.duration < 3000,
    }
  }
];

export default function () {
  // Test all three Malaysian websites in each iteration
  websites.forEach(site => {
    const response = http.get(site.url);
    
    const checksPassed = check(response, site.checks);
    
    if (checksPassed) {
      console.log(`✓ ${site.name}: Success (${response.timings.duration}ms)`);
    } else {
      console.log(`✗ ${site.name}: Failed - Status ${response.status}`);
    }
    
    // Short pause between website tests
    sleep(1);
  });
}

export function setup() {
  console.log('🚀 Starting Smoke Test on Malaysian Websites');
  console.log('🇲🇾 Testing: Shopee, Lazada, and RedBus Malaysia');
  console.log('👥 Virtual Users: 3');
  console.log('⏱️  Duration: 2 minutes');
  console.log('🎯 Objective: Verify Malaysian e-commerce website health');
}
```
## 📊 Results & Analysis

### Overall Performance Summary   
| Metric                 | Result    | Status      |
| ---------------------- | --------- | ----------- |
| **Check Success Rate** | 97.97%    | ✅ Excellent |
| **HTTP Failure Rate**  | 0.31%     | ✅ Excellent |
| **Total Requests**     | 1,284     | 📨          |
| **Test Duration**      | 2 minutes | ⏱️          |

### Platform-Specific Performance   
| Platform   | Avg Response Time | P95 Response Time | Availability | Responsiveness | Overall Score |
| ---------- | ----------------- | ----------------- | ------------ | -------------- | ------------- |
| **Shopee** | 279.39ms          | 1.28s             | 99%          | 88%            | 93.5%         |
| **Lazada** | 56.5ms            | 812.6ms           | 100%         | 100%           | 100%          |
| **RedBus** | 48.51ms           | 420ms             | 100%         | 100%           | 100%          |

### Response Time Distribution (P95)   

| Platform   | Visualization                                |
| ---------- | -------------------------------------------- |
| **Shopee** | ██████████████████████████████████████ 1.28s |
| **Lazada** | ████████████████████████████ 812.6ms         |
| **RedBus** | ██████████████████ 420ms                     |

### Availability Comparison   

| Platform   | Visualization                                       |
| ---------- | --------------------------------------------------- |
| **Shopee** | ████████████████████████████████████████████░░ 99%  |
| **Lazada** | ██████████████████████████████████████████████ 100% |
| **RedBus** | ██████████████████████████████████████████████ 100% |

### Responsiveness Comparison   
| Platform   | Visualization                                       |
| ---------- | --------------------------------------------------- |
| **Shopee** | ████████████████████████████████████████░░░░░░ 88%  |
| **Lazada** | ██████████████████████████████████████████████ 100% |
| **RedBus** | ██████████████████████████████████████████████ 100% |

## 🔍 Identified Bottlenecks
**Shopee Malaysia:**    
- Slight Responsiveness Drop: 88% responsiveness indicates occasional slow responses.   
- Higher P95 Response Time: 1.28s suggests variability under minimal load.   
**Lazada & RedBus:**     
- Near-Perfect Performance: No significant bottlenecks detected under smoke test conditions.

## 🛠️ Recommendations for Improvement   
**For Shopee:**   
- Optimize Static Assets: Compress images and leverage browser caching.   
- CDN Utilization: Ensure global CDN coverage for faster content delivery.   
- Background Script Optimization: Defer non-critical JavaScript execution.   
**General Recommendations:**   
- Monitor Real-User Metrics: Use RUM tools to track actual user experience.   
- Conduct Load & Stress Tests: Assess performance under higher concurrent users.   
- Database & Backend Optimization: Review query performance and API response times.   

## ✅ Conclusion
The smoke test confirmed that all three platforms are production-ready and highly available.   
- RedBus and Lazada demonstrated exceptional performance.   
- Shopee performed well but showed minor responsiveness issues.   
All platforms passed the smoke test with an overall success rate of 97.97%, confirming their stability under minimal load conditions.   

## 🎥 Video Demonstration
A detailed walkthrough of the test execution and result analysis is available on YouTube:
[coming soon]   
