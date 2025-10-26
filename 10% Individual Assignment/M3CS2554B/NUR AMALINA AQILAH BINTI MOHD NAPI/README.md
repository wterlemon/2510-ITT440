### Name:Nur Amalina Aqilah Binti Mohd Napi  
### Matrix ID:2024757479  
### Class:M3CS2554B  
---
### Tittle: Load Testing on Wikipedia using Apache JMeter
---
## Introduction:
This performance testing was conducted using Apache JMeter to examine the speed, stability, and response of the Wikipedia website under a simulated user load. The purpose of the test is to observe the behavior of the website when several users are accessing it at the same time. A test script was created in JMeter with five virtual users, five seconds ramp-up time, and two loops to generate a total of ten requests. The test was targeted at collecting data such as average response time, throughput, and error percentage to achieve the overall performance of the website. This exercise also demonstrates how JMeter components such as Thread Group, HTTP Header Manager, HTTP Request, View Results Tree, and Summary Report are used to measure and analyze web application performance effectively.

---
## Objective:
To evaluate the performance and stability of the Wikipedia website under simulated user load using Apache JMeter.
- To measure key performance metrics such as average response time, minimum and maximum time, and throughput during the test.
- To determine the error rate and verify that the website can handle multiple requests without failure.
- To analyze how the website responds to continuous user access and identify any potential performance bottlenecks.
- To demonstrate the use of Apache JMeter components for conducting web performance testing and analyzing test results effectively.
---
## Tool and Targer Site Selection
| Category | Description |
|---------|-----------|
| Tool Name | Apache JMeter |
| Test Type | Load Test |
| Java Version | OpenJDK Temurin 25 LTS |
| Target Website | Wikipedia — https://www.wikipedia.org|
| Reason for Site Selection | Wikipedia is a stable, high-traffic, and publicly accessible website suitable for testing real-world web performance |

---
## Test Setup and Configuration
| Configuration Item | Details |
|---------|-----------|
| Protocol Used | HTTPS |
| Server Name or IP | www.wikipedia.org |
| HTTP Method | GET |
| Path | /|
| Number of Threads (Users) | 5 |
| Ramp-UP Period (seconds) | 5 |
| Loop Count | 2 |
| Total Samples | 10 requests |
| Header Configuration | User-Agent: Mozilla/5.0 |
| Listeners Used | View Results Tree, Summary Report |

The test setup was configured to simulate a number of users accessing the Wikipedia homepage. The Thread Group was set with five threads and a ramp-up period of five seconds to add users gradually to avoid overloading the server at once. Each thread executed two loops meaning ten HTTP request altogheter. The HTTP Request Sampler used the GET method with the HTTPS protocol to retrieve the Wikipedia main page.
A user-Agent header was added using the HTTP Header Manager to make the requests appear as if they cam from a real browser so that the server would respond normally. Two listeners were added which is Results Tree, to monito the response for each request and Summary report, to collect and display summary performance metrics such as response time, throughput and error rate. This setup provided a good indication of the performance of the website under a light artificial load.

---
## Test Execution Steps
| Step | Description |
|---------|-----------|
| Step 1: Launch JMeter | Apache JMeter was opened and a new Test Plan was created and renamed to “Wikipedia Load Test.” This Test Plan acted as the main container for all testing components.|
| Step 2: Add Thread Group | A Thread Group was added to simulate multiple users accessing the website. The configuration included 5 threads, a ramp-up period of 5 seconds, and 2 loops, resulting in a total of 10 HTTP requests. |
| Step 3: Add HTTP Header Manager | An HTTP Header Manager was added with a header name User-Agent and value Mozilla/5.0. This allowed the requests to appear as if they were coming from a real web browser. |
| Step 4: Add HTTP Request |An HTTP Request sampler was configured with protocol HTTPS, server name www.wikipedia.org, method GET, and path /. This setup directed JMeter to send GET requests to the Wikipedia homepage.|
| Step 5: Add View Results Tree | A View Results Tree listener was included to monitor each request. It displayed detailed information such as response code, response time, and HTML data returned from the server. |
| Step 6: Add Summary Report | A Summary Report listener was added to provide overall performance data including average, minimum, and maximum response time, throughput, and error percentage. |
| Step 7: Execute the Test | The test was executed by clicking the green “Start” button on the JMeter toolbar. The listeners were used to monitor real-time results and verify that all requests were completed successfully. |
| Step 8: Analyze Test Results | After execution, data from the Summary Report was analyzed to evaluate website performance, response stability, and throughput under simulated load conditions. |

---
## Test Result and Analysis
| Metric | Result | Explanation |
|-----------|:------------:|-----------|
| Number of Samples | 10 | Total number of HTTP requests sent to the Wikipedia website during the test. |
| Average Response Time | 2153 ms | The average time taken by the website to respond to each request. |
| Minimum Response Time | 608 ms | The shortest response time recorded during the test. |
| Maximum Response Time | 6002 ms | The longest response time recorded during the test, showing the slowest server response. |
| Standard Deviation | 1637.94 ms | The difference between the fastest and slowest responses, indicating some variation in performance. |
| Error Percentage | 0% | No requests failed during the test, showing the website was stable and reliable. |
| Throughput | 1.2 requests/second | The number of requests the server was able to handle per second. |
| Received KB/sec | 1.21 KB/sec | The average amount of data received from the website every second. |
| Sent KB/sec | 0.12 KB/sec | The average amount of data sent from JMeter to the website every second. |
| Average Bytes | 1040.2 bytes | The average size of the response received from the server. |

Analysis Sumamry:
T
---










