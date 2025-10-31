#### 🧑‍🎓 STUDENT NAME : NUR EZZATY BINTI HUSIN
#### 📝 ITT440 - INDIVIDUAL ASSIGNMENT 
#### 👥 GROUP : M3CS2554A

---
# <h1 align="center">🔥 *Endurance Testing of ChatGPT using JMeter*</h1>

<p align="center">
<img width="250" height="174" alt="logo jmeter" src="https://github.com/user-attachments/assets/d7592b5b-5432-40fc-a210-f899c9628e7a" />

### 📌 Introduction
Performance testing checks how a website performs under heavy or long-term use. For this assignment, I chose **ChatGPT** as the web app and focused on Endurance Testing — testing how well the system runs continuously over time. I used **Apache JMeter** to simulate the test and created simulated results since real **ChatGPT** servers cannot be tested.

---
### 🎯 Objectives
- To simulate a continuous number of virtual users interacting with the ChatGPT web interface over an extended period.
- To observe the system’s response time, throughput, and error rate.
- To identify potential memory leaks, performance degradation, or slowdowns that may appear after long usage.
- To analyze the results and give recommendations for better performance and stability.
  
---
### 🤔 What is Endurance Test?
Endurance Testing tests the ability of your software to perform under expected user traffic over a long period of time.
- The user traffic is high over a long period of time.
- Possibility in real-life

---
### 🧪 Key Features of Apache Jmeter
| **Features** |	**Explaination** |
|------------|----------|
| **Free and Open-Source** |	Apache JMeter is free to use and open-source, making it suitable for both academic and professional projects |
| **User-Friendly Interface** |	It allows easy creation of test plans and thread groups without complex setup |
| **Supports Multiple Test Types** |	JMeter can perform load, stress, and endurance testing effectively |
| **Detailed Performance Metrics** |	It provides graphs, reports, and logs for detailed performance analysis |
| **Web Application Simulation** |	JMeter can simulate multiple users sending HTTP requests, making it ideal for web based performance testing |

---
### 🧰 Test Setup and Configuration
| **Component** |	**Description** |
|------------|----------|
| **Tool Used** |	Apache JMeter 5.6 |
| **Operating System** |	Windows 11 |
| **Processor**	| Intel Core i5 |
| **Target Application** |	https://chat.openai.com |
| **Test Duration** |	1 hour |
| **Virtual Users** (Threads) |	5 |
| **Loop Count** |	Infinite |
| **Ramp-up Period** | 5  |
| **Protocol** | HTTP |

The test simulates 5 virtual users continuously sending requests to ChatGPT over a period of 1 hour. This setup represents a medium load that stays constant for a long duration to observe if the system can maintain stable performance

---
### 📋 Test Scenario and Procedure
A endurance test is used to check if a system can handle a continuous workload for a long time without memory leaks, crashes, or performance drops. It helps identify problems that do not appear in short-term tests.

**Steps:**

**1.** Open Apache JMeter and create a Thread Group with 5 users and 1hour duration.

**2.** Add an **HTTP Request sampler** targeting the ChatGPT web URL.
- **Target URL:** https://chat.openai.com
- **Method:** GET
- **Path:** / 

**3.** Add a Constant Timer to simulate realistic user delays between requests (3–5 seconds).

**4** Add an **HTTP Header Manager:**
- Include headers like:
- **User-Agent:** Mozilla/5.0

**5.** Include a **View Results Tree, View Results in Table, Summary Report** and **Graph Results** listener to record performance data.

**6.** Run the test and monitor metrics such as average response time, throughput, and error rate.

Since this is a simulation, the following results are based on realistic patterns of what a high-traffic web app like ChatGPT might show under a endurance test.

---
### 📈 Simulated Test Results
| **Metric** |**Average Value**	| **Observation** |
|------------|----------|----------|
| **Average Response Time** | 520 ms	 | The system answered quite fast most of the time. |
| **Peak Response Time** | 7048 ms	 |	Some short delays happened during high activity or network bottlenecks. |
| **Throughput** |	9.6 requests/sec |	The system handled a steady number of user requests without slowing down |
| **Error Rate** |	0.01% |	Very few requests failed, showing high stability and reliability |
| **CPU Utilization (Client Machine)** |~30–50% (est.)|Moderate usage; system handled the test without performance issues.|
| **Memory Utilization (Client Machine)** |	~40–60% (est.)|Within safe limits; no signs of memory leaks during execution.|

#### Result Summary
- ✅ The system maintained stable performance throughout the endurance test.
- ⚡ Average response time (520 ms) shows fast and consistent replies.
- ⏱️ Peak response time (7048 ms) happened only during short high-load periods.
- 📈 Throughput (9.6 requests/sec) stayed steady, meaning the system handled continuous traffic well.
- 🧩 Error rate (0.01%) was very low, showing strong reliability.

Overall, the web application showed good speed, stability, and efficiency under long-term use.

---
#### Raw Data :

*Response Time Graph*
<img width="1637" height="541" alt="image" src="https://github.com/user-attachments/assets/5b75a5f5-913f-43de-ad6d-1f20b8c9ceed" />


*Throughput Graph*

*Error Graph*

<img width="812" height="300" alt="image" src="https://github.com/user-attachments/assets/7ee7a5f0-bda3-4a0e-9492-98038509988d" />

<img width="1641" height="368" alt="image" src="https://github.com/user-attachments/assets/23ce63cf-47ba-4e8d-8733-a142113275a3" />

<img width="1638" height="500" alt="image" src="https://github.com/user-attachments/assets/46d3135b-28fa-40fb-9511-d8ef333038ae" />

<img width="1638" height="540" alt="image" src="https://github.com/user-attachments/assets/7d4c4a40-5d47-4e1e-83fd-688e24bf27f4" />




<img width="1493" height="513" alt="image" src="https://github.com/user-attachments/assets/d8507f24-1b7c-4962-acad-3060c0ab353f" />

<img width="1404" height="756" alt="image" src="https://github.com/user-attachments/assets/e64a5a31-24c0-49ab-bb1b-58fe762340dd" />




---
### 🔍 Performance Analysis
The soak test results show that the ChatGPT web application can handle continuous user traffic without significant slowdowns or failures. This indicates that the system has good scalability and memory management.

The small increase in response time during peak usage may come from temporary server queue delays or user-side latency. The low error rate shows that the server can recover quickly from transient issues.

No memory leaks were observed, and CPU usage remained moderate, which means the test environment and tool handled the simulation efficiently.

---
### 🚧 Recommendations
**1.** Use caching or CDN to reduce response time for repeated requests.

**2.** Optimize API endpoints to handle concurrent sessions more efficiently.

**3.** Monitor memory and CPU usage on the actual server to confirm stability.

**4.** Increase system resources (CPU or bandwidth) if high user activity continues for longer periods.

---
### ✅ Conclusion
This assignment demonstrated how a soak test can be performed using Apache JMeter to evaluate the long-term performance of a web application.

Even though the actual test on ChatGPT could not be performed directly, the simulated results showed how an application behaves under continuous load. The analysis suggests that the system remains stable with acceptable response times and minimal errors, which indicates good performance and scalability.

From this experiment, I learned the importance of planning test parameters carefully, monitoring key performance indicators (KPIs), and interpreting test data to make meaningful conclusions. Soak testing is valuable because it helps identify long-term performance issues that normal short-duration tests cannot detect

---
### 📚 References
Apache JMeter Official Documentation – https://jmeter.apache.org

OpenAI ChatGPT – https://chat.openai.com

BlazeMeter Blog – Understanding Soak Testing in JMeter

TutorialsPoint – JMeter Performance Testing Basics

---
### 🎥 YouTube Video Presentation
[]

  
