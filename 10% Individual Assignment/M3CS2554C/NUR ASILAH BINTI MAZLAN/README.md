# Stress Testing on QuickPizza Using Grafana K6

## Table of Contents
1. [Abstract](#abstract)
2. [Introduction](#1-introduction)
3. [Hypothesis](#2-hypothesis)
4. [Tool Selection and Justification](#3-tool-selection-and-justification)
5. [Test Environment Setup](#4-test-environment-setup)
6. [Methodology and Execution](#5-methodology-and-execution)
7. [Results and Raw Data](#6-results-and-raw-data)
8. [Analysis and Interpretation](#7-analysis-and-interpretation)
9. [Recommendations and Best Practices](#8-recommendations-and-best-practices)
10. [Conclusion](#9-conclusion)
11. [Reflection](#10-reflection)
12. [Video Demonstration](#11-video-demonstration)

## **Abstract**

## 1. Introduction
<p align="justify">
Performance of web applications is fundamentally important to user’s pleasure and operational reliability. As applications scale, they need to be able to withstand increased traffic without sacrificing responsiveness or stability. Stress testing is one type of non-functional testing that observes how an application performs under extreme conditions. For example, the load will be gradually increased until the system is near or has exceeded its expected limits.
<p align="justify">
For purposes of the experiment, the QuickPizza demo website was chosen as the target system. The demo site provided static and dynamic content such as menu listings, news pages, and login forms. Thus, it was fitting for replicating realistic browsing and transaction activity. Grafana Cloud K6 is an open-source, cloud-based performance testing platform which was used to assess the website’s reaction as the number of simulated users increased. 

## 2. Hypothesis
<p align="justify">
The expectation was that the QuickPizza website would be stable and responsive under a moderate user load roughly for about 75 virtual users. However, we do expect to see some slight increases in response time and potential request failures as we push towards 100 concurrent users. The bottlenecks were expected to be in the higher latency for pages that needed server-side processing, but it was hoped that the static pages would continue to respond without issue. 

## 3. Tool Selection and Justification

### 3.1 Why Grafana Cloud K6
<p align="justify">
The reason why I chose Grafana Cloud K6 is because it provides a fully cloud-based environment. It allows users to run and monitor performance tests from their browser without having to install local command-line tools. Local command line tools can complicate the setup process and lead to platform dependency on either Windows or macOS.
  
### 3.2 Comparison with Other Tools
<p align="justify">
Unlike other tools like Apache JMeter or Locust, Grafana Cloud K6 puts an emphasis on simplicity and real time visualization. The scripting uses JavaScript which provides flexibility and simplicity for beginners. The dashboards automatically plot important metrics like response time, throughput, and failure rate, making it easy to visualize performance trends. 
<p align="justify">
For this effort, the test was run entirely through the Grafana Cloud K6 web platform instead of in a local Visual Studio Code or Windows Command Prompt environment. The decision to perform the test in the cloud allowed for easier monitoring, cloud-managed execution, and instant graph visualization. 

## 4. Test Environment Setup
<p align="justify">
The Performance menu was utilized in Grafana Cloud K6 to carry out the stress test. A specific project named QuickPizza-StressTest was created for this purpose. The execution environment was set to be hosted in the Columbus load zone to use balanced request distribution and reliable sampling of the results.
<p align="justify">
The maximum virtual users was set to 100, which is the upper limit for the plan offered by Grafana Cloud. While this limit constrained the possible load testing of the service at an extreme level, it was sufficient for determining performance trends and potential bottlenecks.

The JavaScript-based K6 test script defined a gradual user ramp-up pattern to simulate real world browsing behaviour. The stages were:

- Ramp to 50 users in 1 minute
- Increase to 75 users in the next minute
- Peak at 100 users for the final 2 minutes
This configuration enabled controlled load escalation and sustained stress conditions, revealing how performance evolved at each stage.


## 5. Methodology and Execution
//pic of script here
The script simulates a typical user flow visiting the homepage, reading a news section, checking contact details, and then attempting a login. This utilized intentionally invalid credentials to simulate authentication handling under load.

Test execution was conducted by writing the script into the Grafana Cloud K6 Script Editor and clicking ‘Run Test’. Real time metrics were served on the Grafana dashboards showing total requests, the failure rate, and response duration.

### 5.1 Test Configuration Summary

| **Parameter** | **Configuration** |
|----------------|-------------------|
| Test Type | Stress Test |
| Tool Used | Grafana Cloud K6 |
| Total Duration | 4 minutes |
| Virtual Users (VU) Range | 50 → 75 → 100 |
| Thresholds | p(95) < 2000 ms, failure rate < 5% |
| Endpoints Tested | `/`, `/news.php`, `/contacts.php`, `/login` |

### 5.2 Script Snippet


## 6. Results and Raw Data
//pic here
<p align="justify">
After performing the stress test on Grafana Cloud K6, a comprehensive array of performance metrics was generated. The platform automatically presented the output using numerous visualization and analysis panels such as Graph, Cloud Insights, HTTP Summary, Thresholds, and Profile. All of these panels together, show how the QuickPizza test site performed when put under a gradually increasing load.

### 6.1 Graph Overview
//pic here
<p align="justify">
The chart depicts the path of the virtual users (VUs/0 as they ramped from 50 to 75 and finally peaked at 100 over the course of four minutes. As the VUs increased, requests per second (RPS) also increased but levelled off at approximately 682 RPS. Through the entire testing process, the average and 95th percentile (P95) response times remained comfortably under 3.65 ms. The P95 confirms stable performance even during maximum VU ramp up.

### 6.2 Cloud Insights Summary
//pic here
<p align="justify">
The Cloud Insights panel of Grafana gave a succinct overview of system health and performance. It reported 100% tests completed with no serious degradation of service. It showed VU scaling smoothly and a little deviation in latency. Values summarized included mean response time, throughput, and error rate which were all acceptable values.

### 6.3 Threshold Evaluation
//pic here
| **Metric** | **Threshold Condition** | **Observed Result** | **Status** |
|-------------|--------------------------|----------------------|-------------|
| HTTP Request Duration (p95) | < 2000 ms | ~2.49 ms | ✅ Passed |
| HTTP Failure Rate | < 5 % | ~0.01 % | ✅ Passed |

Both defined thresholds were satisfied, indicating that the system maintained the targeted performance level throughout the test.

### 6.4 HTTP Summary
//pic here
<p align="justify">
The HTTP summary indicates that all requests were successfully completed except for one request. One request failed when attempting to authenticate using the | `/login` | endpoint. The failure was deliberate as an invalid credential was used.

### 6.5 Key Observations

- Peak load: **100 virtual users**
- Average throughput: **~689 requests/second**
- 95th percentile response time: **2.49 ms**
- Failed requests: **1 (HTTP 403 on /login)** – expected
- Both thresholds passed ✅

//delete later
To conclude an observation, QuickPizza showed stable operation and fast responses across the various endpoints. The Cloud Insights health indicator was green throughout the testing session, which confirmed no resource exhaustion or queuing of requests. All numeric thresholds were met and with only one failed HTTP request, it is confirmed that error-handling logic was also functioning as intended during load. 

## 7. Analysis and Interpretation
<p align="justify">
The collected data confirms that the QuickPizza demo site performed reliably under stress. As virtual users increased, there was no significant rise in latency or failure rate. The system maintained efficient throughput and quickly responded to all GET requests.

### 7.1 Response Time Stability
<p align="justify">
The graph showed that response times maintained a flat trend line which leads us to believe the web server operated with consistent processing capacity. Even under peak load, the P95 value of 3.65 ms held far below 4 seconds, showcasing an efficient backend processing capability.

### 7.2 Throughput and Scalability Capability
<p align="justify">
Throughput followed the number of users ramped and held a steady state at 682 RPS approximately. No sharp spikes or dips inferred that QuickPizza performed well at handling concurrency and Grafana’s load generators load balanced effectively over the test period. 

### 7.3 Failure and Error Handling
<p align="justify">
The one failed HTTP 403 request observed was not unexpected from the /login endpoint confirming authentication logic was acting in the intended mode rather than exhibiting a performance error. The Logs tab confirmed no connection timeouts nor any unexpected 5xx server errors occurred. 

### 7.4 Resource Utilization Perspective
<p align="justify">
Since the test occurred in Grafana’s cloud environment, CPU and memory usage at the server were not available as the major perspective. However, there were no latency spikes or throttling behaviour that would indicate that the requested infrastructure occurred within safe ranges. 

### 7.5 Insights from Grafana's Analysis Panel
<p align="justify">
The Analysis tab in Grafana aggregated the run to be “Healthy”, with all thresholds listed as “Passed”. Average request time and data transfer remain unchanged and confirm that the system can sustain moderate to heavy traffic.

## 8. Recommendations and Best Practices
- **Increase Test Duration:** Extend test duration beyond four minutes to capture long-term stability trends.  
- **Scale Beyond 100 VUs:** Upgrade Grafana Cloud plan for more extensive stress evaluation.  
- **Improve Login Simulation:** Use valid credentials to test actual authentication load.  
- **Add Resource Monitoring:** Integrate backend CPU and memory metrics for complete system visibility.  
- **Implement Continuous Testing:** Automate recurring stress tests after major code updates to ensure consistent performance.


## 9. Conclusion


## 10. Reflection


## 11. Video Demonstration
A short walkthrough video showcasing the test execution, configuration steps, and the result visualization is available on : 

