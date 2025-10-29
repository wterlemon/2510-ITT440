# Web Application Soak Testing with Vegeta

## 📋 Assignment Details
- **Course:** 2510-ITT440
- **Assessment:** 1 (10%)
- **Tool:** Vegeta
- **Target Website:** HTTPBin.org
- **Test Type:** Soak Testing (Endurance Testing)
- **Duration:** 15 minutes

## 🎯 Project Overview
This project demonstrates a 15-minute soak test on HTTPBin.org using Vegeta load testing tool. Soak testing helps identify performance degradation, memory leaks, and stability issues under sustained load over an extended period.

## 🛠️ Tools & Technologies
- **Load Testing Tool:** Vegeta v12.11.0
- **Target Platform:** HTTPBin.org
- **Test Duration:** 15 minutes
- **Load Intensity:** 4 requests per second
- **Total Requests:** ~3,600

## 📊 Test Configuration

<img width="1887" height="603" alt="image" src="https://github.com/user-attachments/assets/fee216a4-0ab7-40f3-8e61-8da5895c906e" />




### Vegeta Command
```bash
vegeta attack -targets httpbin_optimized.txt -rate 4 -duration 1m -timeout 30s -output optimized_soak.bin


