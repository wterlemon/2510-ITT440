# 🔥 *Endurance Testing of ChatGPT using JMeter*

<img width="150" height="174" alt="logo jmeter" src="https://github.com/user-attachments/assets/d7592b5b-5432-40fc-a210-f899c9628e7a" />

#### 🧑‍🎓 STUDENT NAME : NUR EZZATY BINTI HUSIN
#### 📝 ITT440 - INDIVIDUAL ASSIGNMENT
#### 👥 GROUP : M3CS2554A

---
### 🎓 Introduction
Performance testing checks how a website performs under heavy or long-term use. For this assignment, I chose **ChatGPT** as the web app and focused on Endurance Testing — testing how well the system runs continuously over time. I used **Apache JMeter** to simulate the test and created simulated results since real **ChatGPT** servers cannot be tested.

---

### 🤔 What is Endurance Test?
Endurance Testing tests the ability of your software to perform under expected user traffic over a long period of time.
- The user traffic is high over a long period of time.
- Possibility in real-life

---
### 🧠 Objectives
- To simulate a continuous number of virtual users interacting with the ChatGPT web interface over an extended period.
- To observe the system’s response time, throughput, and error rate.
- To identify potential memory leaks, performance degradation, or slowdowns that may appear after long usage.
- To analyze the results and give recommendations for better performance and stability.

---
### 🧪 Tool Selection
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
| **Virtual Users** (Threads) |	10 |
| **Ramp-up Period** | 5 minutes |

The test simulates 10 virtual users continuously sending requests to ChatGPT over a period of 1 hour. This setup represents a medium load that stays constant for a long duration to observe if the system can maintain stable performance

---
### 📋 Test Scenario and Procedure

---
### 📈 Simulated Test Results
| **Metric** |**Average Value**	| **Observation** |
|------------|----------|----------|
| **Average Response Time** |	 |	 |
| **Peak Response Time** |	 |	 |
| **Throughput** |	 |	 |
| **Error Rate** |	 |	 |
| **CPU Utilization (Client Machine)** |	 |	 |
| **Memory Utilization (Client Machine)** |	 |	 |

---
### 🚧 Bottlenecks and Recommendations

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

  
