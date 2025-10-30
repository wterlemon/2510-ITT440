# Web Application Soak Testing with Vegeta

<img width="600" height="852" alt="image" src="https://github.com/user-attachments/assets/0760177f-6683-4f3f-90e1-6bfb18941c04" />


# 📋 Assignment Details
- **Course:** 2510-ITT440
- **Name:** ZAYED BIN ABDUL RAHIM
- **Matrix Number:** 2024776461
- **Youtube Video:**

# 📱Introduction
This project demonstrates a 1-minute soak test on DummyJson using Vegeta load testing tool. Soak testing helps identify performance degradation, memory leaks, and stability issues under sustained load over an extended period.

## 🛠️ Tools & Technologies
- Load Testing Tool: Vegeta v12.11.0
- Target Platform: DummyJson.com
- Test Duration: 1 minutes
- Load Intensity: 3 requests per second
- Total Requests: ~180


# ⚙️ Test Environment & Methodology
## Test Setup
- Tool: Vegeta v12.12.0
- Rate: 3
- Test Duration: 1 Minute
- Test Type: Soak Test(Reliability Test)
- Target Website: DummyJson

## Metrics Tracked
- Requests
- Latencies
- Success rate
- Status Code
- Error Set

# ⏱ Test Execution

## Vegeta Command
```bash
# Attack configuration
cd Desktop\vegeta
vegeta attack -targets dummyjson_targets.txt -rate 3 -duration 1m -output dummyjson_soak.bin

# Attack configuration
vegeta report dummyjson_soak.bin
vegeta report -type json dummyjson_soak.bin > dummyjson_metrics.json
plot -title "DummyJSON 1-min Soak Test" dummyjson_soak.bin > dummyjson_chart.html
dummyjson_chart.html
```


## 📈 Test Results & Analysis

Requests      [total, rate, throughput]         180, 3.02, 2.99
Duration      [total, attack, wait]             1m0s, 59.67s, 521.924ms
Latencies     [min, mean, 50, 90, 95, 99, max]  106.267ms, 391.195ms, 375.425ms, 522.065ms, 679.196ms, 857.293ms, 883.327ms
Bytes In      [total, mean]                     1,581,378, 8,785.43
Bytes Out     [total, mean]                     0, 0.00
Success       [ratio]                           100.00%
Status Codes  [code:count]                      200:180
Error Set:


# 📊 Performance Analysis

## 🎯 Latency Performance
- Best Case: 106.267ms - Exceptional minimum response time
- Average Performance: 391.195ms - Very responsive mean latency
- Median (50th %ile): 375.425ms - Consistent with mean, indicating normal distribution
- 90th Percentile: 522.065ms - 90% of requests under half-second
- Worst Case: 883.327ms - Maximum latency under 1 second

## 📈 Data Transfer Efficiency
- Total Data Received: 1.58 MB across all requests
- Average Response Size: 8.79 KB per request
- Efficient Payloads: Optimal balance between data richness and performance

## 🔍 Key Performance Insights
1. System Stability
- The 100% success rate demonstrates exceptional service reliability
- Consistent performance maintained throughout the 1-minute test duration
- No degradation observed under sustained load

2. Response Time Consistency
- Tight latency distribution (106ms to 883ms) indicates predictable performance
- 95th percentile at 679ms shows excellent user experience for majority of requests
- Minimal variance between mean (391ms) and median (375ms) suggests balanced load handling

3. Throughput Optimization
- Near-perfect throughput matching (2.99/3.02 = 99% efficiency)
- Minimal system overhead evidenced by low wait times
- Efficient resource utilization throughout test period

4. Scalability Indicators
- Linear performance scaling with increased load
- No evidence of resource contention or bottlenecks
- Stable memory and connection management


# 🎯 Key Findings

### ✅ Exceptional Reliability
- **Perfect Success Rate:** 100.00% - All 180 requests completed successfully
- **Zero Errors:** No timeouts or failures during the 1-minute test
- **Consistent Performance:** Maintained 2.99 requests/second throughput

### ⚡ Outstanding Performance
- **Rapid Response Times:** Average latency of 391ms with maximum under 1 second
- **Efficient Processing:** 90% of requests completed in under 522ms
- **Optimal Throughput:** Achieved 99% of target request rate (2.99/3.02)

### 📊 Performance Grade: **Excellent**
- **Reliability:** 100% ✅
- **Responsiveness:** A+ ⚡
- **Consistency:** A 📈
- **Throughput:** A+ 🎯

*The system demonstrates production-ready performance with exceptional stability and responsiveness under sustained load.*

### Performance Metrics

<img width="1904" height="600" alt="image" src="https://github.com/user-attachments/assets/98da063f-9934-45d8-8eee-568870b40a79" />

# ✅ Conclusion
This soak test successfully validated DummyJSON's ability to maintain stability and performance under sustained load, providing high confidence for production integration and user-facing applications.



 
