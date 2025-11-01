#### 🧑‍🎓 STUDENT NAME : NUR EZZATY BINTI HUSIN
#### 📝 ITT440 - INDIVIDUAL ASSIGNMENT 
#### 👥 GROUP : M3CS2554A

---
<p align="center">
<img width="522" height="212" alt="asf-logo" src="https://github.com/user-attachments/assets/ca7bfbd0-e880-41ab-a93e-5faa2eb4e420" />

# <h1 align="center">🔥 *Endurance Testing of ChatGPT using JMeter*</h1>

### 📌 Introduction
Web application performance testing helps us understand how a website works when many people use it for a long time. The main goal is to see if the website stays **fast, stable and reliable** during continuous use. 

In this assignment, I choose **OpenAI ChatGPT** as the web application to test. ChatGPT is a popular online AI chatbot that allows users to chat by typing messages. The purpose of this project is to perform a Endurance Test, which checks how stable and responsive the system is when it runs for a long time without stopping.

The testing is done using **Apache JMeter**, a common tool for performance testing. Since we cannot test directly, this report uses simulated results that show what might happen in a real endurance test on a similar system.

---
### 🎯 Objectives
- To simulate a continuous number of virtual users interacting with the ChatGPT web interface over an extended period.
- To observe the system response time, throughput, and error rate.
- To identify potential memory leaks, performance issues, or slow downs that may appear after long usage.
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
| **Web Application Simulation** |	Can simulate multiple users sending HTTP requests, making it ideal for web based performance testing |

> *Explanation:*
>
> Other tools like K6 or LoadRunner also support similar tests, but JMeter graphical interface and community support make it easier to learn and use for this individual project.

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

> *Explanation:*
>
> The test simulates 5 virtual users continuously sending requests to ChatGPT over a period of 1 hour. This setup represents a medium load that stays constant for a long duration to observe if the system can maintain stable performance.

---
### 📋 Test Scenario and Procedure
A endurance test is used to check if a system can handle a continuous for a long time without memory leaks, crashes or performance drops. It helps identify problems that do not appear in short term tests.

**Steps:**

**1.** Open Apache JMeter and create a Thread Group with 5 users and 1 hour duration.

**2.** Add an **HTTP Request Sampler** targeting the ChatGPT web URL.
- **Target URL:** https://chat.openai.com
- **Method:** GET
- **Path:** / 

**3.** Add a Constant Timer to simulate realistic user delays between requests (3–5 seconds).

**4** Add an **HTTP Header Manager:**
- **Include headers like:**
- User-Agent: Mozilla/5.0

**5.** Include a **View Results Tree, View Results in Table, Summary Report** and **Graph Results** listener to record performance data.

**6.** Run the test and monitor metrics such as average response time, throughput, and error rate.

> *Explanation:*
>   
> Since this is a simulation, the following results are based on realistic patterns of what a high-traffic web app like ChatGPT might show under a endurance test.

---
### 📈 Simulated Test Results
| **Metric** |**Average Value**	| **Observation** |
|------------|----------|----------|
| **Average Response Time** | 520 ms	 | The system answered quite fast most of the time. |
| **Peak Response Time** | 7048 ms	 |	Some short delays happened during high activity or network bottlenecks. |
| **Throughput** |	9.6 requests/sec |	The system handled a steady number of user requests without slowing down |
| **Error Rate** |	0.01% |	Very few requests failed, showing high stability and reliability |

#### Result Summary
- ✅ The system maintained stable performance throughout the endurance test.
- ⚡ Average response time (520 ms) shows fast and consistent replies.
- ⏱️ Peak response time (7048 ms) happened only during short high load periods.
- 📈 Throughput (9.6 requests/sec) stayed steady, meaning the system handled continuous traffic well.
- ❌ Error rate (0.01%) was very low, showing strong reliability.

> *Explanation:*
> 
> Overall, the web application showed good speed, stability, and efficiency under long term use.

---
### 📊 Raw Data :

<p align="center">
<img width="1637" height="541" alt="image" src="https://github.com/user-attachments/assets/5b75a5f5-913f-43de-ad6d-1f20b8c9ceed" />
<p align="center">Response Time Graph</p>
  
---
<p align="center">
<img width="1643" height="543" alt="image" src="https://github.com/user-attachments/assets/e1c18eb7-1eb5-4f57-968c-34c98fe5eb4a" />
<p align="center">Throughput Graph</p>

---
<p align="center">
  
<img width="812" height="300" alt="image" src="https://github.com/user-attachments/assets/7ee7a5f0-bda3-4a0e-9492-98038509988d" />
<p align="center">Error Graph</p>

---
- A Statistics table providing in one table a summary of all metrics per transaction including 3 configurable percentiles:
<img width="1641" height="368" alt="image" src="https://github.com/user-attachments/assets/23ce63cf-47ba-4e8d-8733-a142113275a3" />

<img width="1404" height="756" alt="image" src="https://github.com/user-attachments/assets/e64a5a31-24c0-49ab-bb1b-58fe762340dd" />

---
### 🔍 Performance Analysis
The endurance test results show that the ChatGPT web application can handle continuous user traffic without significant slowdowns or failures. This indicates that the system has good scalability and memory management.

The small increase in response time during peak usage may come from temporary server queue delays or user-side latency. The low error rate shows that the server can recover quickly from transient issues.

No memory leaks were observed, and CPU usage remained moderate, which means the test environment and tool handled the simulation efficiently.

---
### 🚧 Recommendations
**1.** Use caching or CDN to reduce response time for repeated requests.

**2.** Optimize API endpoints to handle concurrent sessions more efficiently.

**3.** Monitor memory and CPU usage on the actual server to confirm stability.

**4.** Increase system resources if high user activity continues for longer periods.

---
### 🧩 Conclusion
This assignment demonstrated how a endurance test can be performed using Apache JMeter to evaluate the long-term performance of a web application.

Even though the actual test on ChatGPT could not be performed directly, the simulated results showed how an application behaves under continuous load. The analysis suggests that the system remains stable with acceptable response times and minimal errors, which indicates good performance and scalability.

From this experiment, I learned the importance of planning test parameters carefully, monitoring key performance indicators (KPIs), and interpreting test data to make meaningful conclusions. Endurance testing is valuable because it helps identify long-term performance issues that normal short duration tests cannot detect

---
### 📚 References
Apache JMeter Official Documentation – https://jmeter.apache.org

OpenAI ChatGPT – https://chat.openai.com

Wikipedia - Soak Testing

BlazeMeter Blog – Understanding Soak Testing in JMeter

TutorialsPoint – JMeter Performance Testing Basics

---
### 🎥 YouTube Video Presentation
[https://youtu.be/lnSiQUrJ0V0?si=Ci2VgiOXceNxUb-L]

  
