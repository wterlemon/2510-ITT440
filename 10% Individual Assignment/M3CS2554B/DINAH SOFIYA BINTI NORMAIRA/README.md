# DINAH SOFIYA BINTI NORMAIRA
Web Application Performance Testing & Analysis Using K6 on Shopist.io
Prepared by:

Name: Dinah Sofiya binti Normaira
Matric No:2024789121
Class: M3CS2554B

1. Introduction

In the modern digital landscape, website performance is a crucial factor that determines user experience and reliability. A slow or unstable website can cause user dissatisfaction, revenue loss, and poor credibility.

This project aims to perform a Spike Test on Shopist.io
, an e-commerce demo website, using K6, an open-source load testing tool developed by Grafana Labs.

The objective of this spike test is to:

Evaluate how Shopist.io behaves when experiencing sudden traffic surges.

Measure performance metrics such as response time, throughput, and error rate.

Identify performance bottlenecks and propose optimization recommendations.

2. Tool Selection: K6
2.1 Overview

K6 is a modern open-source load testing tool written in Go and uses JavaScript for test scripting. It is lightweight, fast, and designed for both developers and testers to run performance and stress tests effectively.

2.2 Why K6?
Criteria	K6 Advantage
Developer Friendly	Uses JavaScript, easy to script realistic test scenarios.
Lightweight & Fast	Built in Go, uses minimal system resources.
Detailed Metrics	Measures latency, throughput, and errors in real time.
Scalable	Supports distributed testing and cloud execution via Grafana Cloud.
Open Source	Free, actively maintained, and works cross-platform (Windows, Linux, macOS).

K6’s simplicity, flexibility, and developer-oriented design make it an excellent choice for academic and real-world performance analysis.

3. Hypothesis

“The Shopist.io website is expected to perform well under normal user activity, but during a sudden spike of hundreds of concurrent users, response times will increase significantly, and some requests may fail due to server overload or rate limiting.”

This hypothesis will be evaluated during the spike test scenario.

4. Test Environment & Setup
4.1 System Configuration
Component	Details
Operating System	Windows 11 (64-bit)
Processor	Intel Core i3
RAM	8 GB
Tool	K6 v1.3.0
Target Website	https://shopist.io

Test Type	Spike Test
Duration	~1 minute
4.2 Installation Steps



4.3 K6 Spike Test Script



5. Test Scenario & Methodology
🎯 Spike Test Objective:

To observe how Shopist.io handles sudden surges of users, simulating viral or flash-sale traffic conditions.

Parameter	Value
Users (VUs)	Up to 200
Ramp-Up Duration	10 seconds
Spike Duration	30 seconds
Ramp-Down Duration	10 seconds
Total Duration	~50 seconds
Target URL	https://shopist.io/

During this test, K6 rapidly increases virtual users to 200 within 10 seconds, holds the spike, and then reduces the load back to 0.

6. Key Metrics Measured
Metric	Description
Response Time (ms)	Time taken for server to respond to HTTP requests.
Request Rate (RPS)	Number of requests handled per second.
Error Rate (%)	Percentage of failed requests.
Throughput	Total data sent and received during the test.
95th Percentile	Ensures 95% of responses are below target response time.

7. Test Results & Observations



📊 Sample Summary (Example):





📌 Key Observations

✅ Stable Load Handling: Shopist.io responded well up to ~150 concurrent users.
⚠️ Increased Latency: 95th percentile response time exceeded 2 seconds after 180 users.
🚫 Minor Failures: 0.01% failure rate due to timeouts during peak load.
📈 Throughput: 204 requests/second sustained during the spike phase.

8. Analysis of Findings
Observation	Possible Cause	Recommendation
Slow response during peak load	Server CPU or connection saturation	Use CDN caching or scalable backend servers.
Timeout errors after 180 users	Backend overload	Implement load balancing or auto-scaling.
Increased latency (p95 > 2s)	Insufficient concurrent request handling	Optimize database queries and reduce blocking calls.
🧩 Conclusion of Analysis:

Shopist.io remained stable for moderate user traffic but experienced latency and minor failures during extreme spikes. The system demonstrates good resilience but may require backend optimization for sudden load bursts.

9. Recommendations

Enable Caching: Reduce redundant data requests.

Use a CDN (Content Delivery Network): Improve response times globally.

Increase Server Resources: Scale horizontally to handle sudden spikes.

Optimize Frontend & Images: Reduce overall page load time.

Continuous Monitoring: Integrate Grafana or Prometheus for real-time performance insights.

10. Conclusion

This project demonstrated the use of K6 to evaluate web performance under spike load conditions.
The test confirmed that Shopist.io can handle moderate spikes effectively but struggles with high concurrency levels, as reflected in increased latency and small error rates.

These findings validate the hypothesis and emphasize the importance of scalability and caching strategies in modern web systems.

11. 🎥 Video Demonstration
“Spike Performance Testing on Shopist.io Using K6”


12. References

Grafana Labs. (2024). K6 Documentation. https://grafana.com/docs/k6

Shopist Demo Store. https://shopist.io

IEEE Software Engineering Practices (2024). Performance Testing Fundamentals.

Atlassian Engineering Blog (2023). How to Conduct Load and Spike Tests Effectively.
