
<p align="center">
  <img src="https://openweathermap.org/themes/openweathermap/assets/img/logo_white_cropped.png" alt="OpenWeatherMap Logo" width="200"/>
</p>

<h1 align="center">🌤️ API Testing with Postman & OpenWeatherMap</h1>

## 📘 INTRODUCTION
This project focuses on API testing using **Postman** with the **OpenWeatherMap API**, emphasizing both functional and performance validation. The primary goal is to ensure that the weather data retrieval endpoint operates reliably under varying conditions. In addition to verifying response codes and data integrity, this project includes a **load testing component with 3 different stages of Load Test (Medium, Stres and Light)**, where multiple requests are executed in quick succession to evaluate the API’s stability and responsiveness under simulated traffic.

These tests are intended to measure average response times, find possible bottlenecks, and verify that the API can withstand repeated calls without experiencing performance deterioration.  This method sheds light on the API's scalability and preparedness for practical use cases where reliable performance and high availability are essential.

## 🎯 OBJECTIVE
- To perform automated API testing using Postman.
- To evaluate the reliability and response time of the OpenWeatherMap API.
- To ensure the returned data (status code 200 and response body) is accurate and consistent.
- To try with different API Key, different places and different purpose of load test (Medium, Stress and Light).

## 🛠️ TOOL & TARGET SITE SOLUTION
**Tool:** Postman  
**Target Site:** [OpenWeatherMap API](https://openweathermap.org/api)

OpenWeatherMap uses RESTful APIs to deliver real-time weather data.  Because of its automated test runner, comprehensive reporting features, and user-friendly interface, Postman was chosen as the testing tool.

## 📋 TEST SCENARIOS
1. Send GET request with valid latitude and longitude.
2. Check if response status is 200.
3. Measure average response time.
4. Repeat test for multiple iterations to check consistency.
5. Use different API key.<br>

   <img width="587" height="231" alt="image" src="https://github.com/user-attachments/assets/f5310651-c76e-4e4e-8077-12291f0a0640" /><br>


## 🧪 TEST PLAN & CONFIGURATION
- **Request Method:** GET  
- **Endpoint:** `https://api.openweathermap.org/data/2.5/weather`  
- **Parameters:** (Depends on place that we want to test. Make sure we knows the longitude and latitude)<br>
  For examples: Bemban, Melaka
  - `lat = 2.3`  
  - `lon = 102.4`  
  - `appid = 5ca69bc7f64a124d9c9180f120a23a01` - you need to get your own API key 
- **Iterations:** 10
- **Delay:** 1000 ms
- **Assertions:** Verify `Status Code = 200`

## 📊 RESULTS (with charts)
| Iteration | Status | Response Time (ms) | Response Size (B) |
|-----------|--------|---------------------|--------------------|
| 1         | ✅ PASS | 41                  | 807                |
| 2         | ✅ PASS | 40                  | 807                |
| 3         | ✅ PASS | 34                  | 807                |
| 4         | ✅ PASS | 257                 | 807                |
| 5–10      | ✅ PASS | ~65 avg             | 807                |

**Average Response Time:** 65 ms  
**Total Iterations:** 10  
**All Tests Passed (100%)**

## 📈 Throughput
Throughput helps measure how many requests the API can handle per second during a load test. It's a key performance metric in API testing.

**Example:**
- Total Requests: 10
- Total Duration: 14.118 seconds


```
Throughput = 10 / 14.118 ≈ 0.71 requests/sec
```

This means the API handled approximately **0.71 requests per second** during the test. Higher throughput indicates better performance and scalability.

## 🧪 ANOTHER TEST PLAN & CONFIGURATION 
- **Parameters:**<br>
  For examples: Kuala Lumpur
  - `lat = 3.1390`  
  - `lon = 101.6869`  
  - `appid = 617863b3b7a29220c7ecc9dee6700327`
- **Iterations:** 10
- **Delay:** 1000 ms
- **Assertions:** Verify `Status Code = 200`


## 📌 Analysis & Discussion
- All requests returned a `200 OK` status, confirming successful communication with the API.
- Response times were stable, with minor variation due to network latency.
- The consistent response size (807 B) indicates structured and reliable JSON output.

## 💡 Recommendations
- Implement Postman monitors for real-time API uptime tracking.
- Expand testing with invalid parameters (negative test cases).
- Automate collection runs via CI/CD for continuous testing.

## ✅ Conclusion
The OpenWeatherMap API demonstrated strong reliability and stability throughout all test iterations. Each request returned a successful `200 OK` status, confirming that the endpoint is functioning as intended. Response times were consistently within acceptable limits, with only minor fluctuations attributed to network latency. The uniform response size and structured JSON output further validate the integrity and predictability of the data provided by the API.

Overall, these results indicate that the OpenWeatherMap API is well-suited for real-time weather data retrieval in production environments. Its performance under repeated requests suggests that it can handle moderate traffic without degradation in speed or accuracy. For future improvements, integrating automated monitoring and expanding negative test cases will enhance robustness and ensure continued reliability under diverse conditions.

## 🔗 References
- [OpenWeatherMap API Documentation](https://openweathermap.org/api)
- [Postman Learning Center](https://learning.postman.com/)

## ▶️ Embedded YouTube Video Link
[Click here to watch the demo](https://www.youtube.com/)
