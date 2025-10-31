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

---
### 📈 Simulated Test Results
| **Metric** |**Average Value**	| **Observation** |
|------------|----------|----------|
| **Average Response Time** | 520 ms	 | Generally responsive under load; suitable for moderate traffic |
| **Peak Response Time** | 7048 ms	 |	Some latency spikes observed; may indicate backend or network bottlenecks. |
| **Throughput** |	9.6 requests/sec |	Higher throughput than previous runs; system handled increased load well. |
| **Error Rate** |	0.01% |	Excellent reliability; no failed requests during the test. |
| **CPU Utilization (Client Machine)** |~30–50% (est.)|Moderate usage; system handled the test without performance issues.	 |
| **Memory Utilization (Client Machine)** |	~40–60% (est.)|Within safe limits; no signs of memory leaks during execution.|

#### Result Summary :
<img width="812" height="300" alt="image" src="https://github.com/user-attachments/assets/7ee7a5f0-bda3-4a0e-9492-98038509988d" />

<img width="1641" height="368" alt="image" src="https://github.com/user-attachments/assets/23ce63cf-47ba-4e8d-8733-a142113275a3" />

<img width="1638" height="500" alt="image" src="https://github.com/user-attachments/assets/46d3135b-28fa-40fb-9511-d8ef333038ae" />

<img width="1638" height="540" alt="image" src="https://github.com/user-attachments/assets/7d4c4a40-5d47-4e1e-83fd-688e24bf27f4" />




<img width="1493" height="513" alt="image" src="https://github.com/user-attachments/assets/d8507f24-1b7c-4962-acad-3060c0ab353f" />

<img width="1404" height="756" alt="image" src="https://github.com/user-attachments/assets/e64a5a31-24c0-49ab-bb1b-58fe762340dd" />




---
### 🔍 Performance Analysis

---
### 🚧 Recommendations

---
### ✅ Conclusion
This assignment showed how to use Apache JMeter for a endurance test to evaluate long term web app performance. Although ChatGPT couldn’t be tested directly, simulated results showed stable performance with minimal errors. I learned the importance of setting test parameters, monitoring KPIs, and analyzing results to detect long term issues.

---
### 📚 References
Apache JMeter Official Documentation – https://jmeter.apache.org

OpenAI ChatGPT – https://chat.openai.com

BlazeMeter Blog – Understanding Soak Testing in JMeter

TutorialsPoint – JMeter Performance Testing Basics

---
### 🎥 YouTube Video Presentation
[]

  
