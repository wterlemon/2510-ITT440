# UMMU NADHWA BINTI BAHARUDDIN
*STUDENT NAME: UMMU NADHWA BINTI BAHARUDDIN*

*GROUP: M3CS255 4B*

## Title & Introduction
This project demonstrates API testing using **Postman** with the **OpenWeatherMap API**. The purpose is to verify the functionality and performance of the weather data retrieval endpoint by sending multiple requests and validating response codes, time, and data integrity.

## Objective
- To perform automated API testing using Postman.
- To evaluate the reliability and response time of the OpenWeatherMap API.
- To ensure the returned data (status code 200 and response body) is accurate and consistent.

## Tool & Target Site Selection
**Tool:** Postman  
**Target Site:** [OpenWeatherMap API](https://openweathermap.org/api)

OpenWeatherMap provides real-time weather data via RESTful APIs. Postman is selected as the testing tool due to its user-friendly interface, automated test runner, and detailed reporting features.

## Test Plan & Configuration
- **Request Method:** GET  
- **Endpoint:** `https://api.openweathermap.org/data/2.5/weather`  
- **Parameters:**  
  - `lat=2.3`  
  - `lon=102.4`  
  - `appid=5ca69bc7f64a124d9c9180f120a23a01`  
- **Iterations:** 10  
- **Assertions:** Verify `Status Code = 200`

## Test Scenarios
1. Send GET request with valid latitude and longitude.
2. Check if response status is 200.
3. Measure average response time.
4. Repeat test for multiple iterations to check consistency.

## Results (with charts)
| Iteration | Status | Response Time (ms) | Response Size (B) |
|------------|---------|--------------------|-------------------|
| 1 | ✅ PASS | 41 | 807 |
| 2 | ✅ PASS | 40 | 807 |
| 3 | ✅ PASS | 34 | 807 |
| 4 | ✅ PASS | 257 | 807 |
| 5–10 | ✅ PASS | ~65 avg | 807 |

**Average Response Time:** 65 ms  
**Total Iterations:** 10  
**All Tests Passed (100%)**



<img width="939" height="145" alt="graph" src="https://github.com/user-attachments/assets/161bf509-ff57-449f-bca3-298eb211cd3e" />




## Analysis & Discussion
- All requests returned a `200 OK` status, confirming successful communication with the API.
- Response times were stable, with minor variation due to network latency.
- The consistent response size (807 B) indicates structured and reliable JSON output.

## Recommendations
- Implement Postman monitors for real-time API uptime tracking.
- Expand testing with invalid parameters (negative test cases).
- Automate collection runs via CI/CD for continuous testing.

## Conclusion
The OpenWeatherMap API performed reliably across all test iterations. Response times were within acceptable limits, and no failures occurred. This confirms that the API endpoint is functional, stable, and efficient.

## References
- [OpenWeatherMap API Documentation](https://openweathermap.org/api)
- [Postman Learning Center](https://learning.postman.com/)

## Embedded YouTube Video Link
[Click here to watch the demo](https://www.youtube.com/)
