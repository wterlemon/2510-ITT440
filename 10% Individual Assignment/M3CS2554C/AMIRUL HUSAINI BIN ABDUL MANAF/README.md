# Comprehensive Web Application Performance Testing & Analysis

**NAME:** AMIRUL HUSAINI BIN ABDUL MANAF

**STUDENT ID:** 2025137953

**CLASS:** CDCS2554C

**TITLE:**  LOAD TESTING USING LOCUST TO WEBSITE HTTPS://DUMMYJSON.COM


## **INTRODUCTION TO WEB APPLICATION PERFORMANCE TESTING & ANALYSIS**
<p align="justify">
Web application testing and analysis is a process to evaluate a web application's functionality, performance, security, and usability to find defects and ensure it meets requirements before release. The goal is to identify and fix bugs to provide a seamless user experience and high-quality product, which is achieved through systematic testing and analysis across different environments like browsers and operating systems. </p>

## 💡 Testing Environment & Goal

This experiment was performed in a Linux environment, specifically Kali Linux, which provides a stable and secure platform for running performance testing tools such as Locust.

The main goal of this testing is to assess the performance and stability of the DummyJSON web API under concurrent user load using Locust load testing tool.  

## 🧰 Tool Selection : LOCUST

<img width="500" height="188" alt="image" src="https://github.com/user-attachments/assets/02b93a21-34ec-4e25-b89e-3d1b4e581633" />  

<p align="justify">
Locust is an open-source, Python-based load testing tool designed for performance testing of web applications and APIs. It allows users to define the behavior of virtual users using standard Python code, offering flexibility and extensibility compared to tools relying on graphical user interfaces or domain-specific languages. </p>

## 🔑 Main Features of LOCUST

- Scalability
- Python-based scripting
- Real-time monitoring

## 🚀 Test Environment Setup and Methodology.
<img width="602" height="317" alt="image" src="https://github.com/user-attachments/assets/e38af6f9-c438-4aea-9e9e-7af2bae86841" />

Here, we can input these information:
- number of users
- ramp up (users started per second)
- host
- run time

## 📊 Raw Data Presentation
<img width="602" height="179" alt="image" src="https://github.com/user-attachments/assets/1ca721cb-b481-486f-9f35-132db27810bb" />  

<img width="916" height="721" alt="image" src="https://github.com/user-attachments/assets/1e57b317-6aa0-4595-a8c1-026807ae3091" />

<img width="630" height="164" alt="image" src="https://github.com/user-attachments/assets/8eba9e8a-824a-489c-8574-7145b32eee79" />


This is the web interface of the LOCUST that is easier to run and monitor. 


## 📝 Interpretation of Results and Identified Bottlenecks

### Result Summary Table
| Endpoint        | Avg Time (ms) | 95% Time (ms) | Requests/s | Failures |
|-----------------|---------------|---------------|-------------|-----------|
| /products       |               |               |             |          |
| /products/[id]  |               |               |             |          |
| /posts          |               |               |             |          |


## 📖 Recommendations For Improvement 
<p align="justify"> Although the DummyJSON API demonstrated stable behavior under moderate load, the following recommendations can help enhance performance and scalability if this were a production API: </p>


## Conclusion

To conclude, from the testing I learn about the load testing...very fun lol 🙂


