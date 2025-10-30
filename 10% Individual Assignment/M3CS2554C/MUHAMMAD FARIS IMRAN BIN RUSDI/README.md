# 🧪 Website Stress Testing Using Artillery on Linux

## 1. Introduction: Stress Testing

Stress testing is a type of performance testing used to evaluate how a website or web application behaves under extreme conditions such as heavy traffic, limited server resources, or unexpected spikes in requests.
The goal is to determine the **maximum capacity**, **stability**, and **reliability** of the system before it goes live.

By conducting stress tests, developers can:

* Identify **bottlenecks** and performance limits.
* Improve **server configurations** and **code efficiency**.
* Ensure the system remains **stable and responsive** under high load.

---

## 2. Tool Used: Artillery (on Linux)

**Artillery** is a modern, open-source load testing tool used to simulate real-world traffic for APIs, websites, and backend systems.
It is written in Node.js and can generate a large number of HTTP, WebSocket, or Socket.io requests efficiently.


## 3. Features of Artillery

| Feature                       | Description                                          |
| ----------------------------- | ---------------------------------------------------- |
| 🧩 **Scenario-based testing** | Define multiple user flows using YAML or JSON files. |
| 🚀 **High scalability**       | Can generate thousands of virtual users.             |
| 📊 **Detailed reports**       | Provides JSON or HTML summaries of test results.     |
| ⚙️ **Protocol support**       | Supports HTTP, HTTPS, WebSocket, and Socket.io.      |
| ⏱ **Custom timings**          | Control request rates, delays, and durations.        |
| 🧠 **Integration ready**      | Works with CI/CD pipelines and cloud testing.        |

---

## 4. Target Website

The test will target a simple web application hosted online or locally (e.g., `http://`
This helps evaluate:

* **Response time (latency)**
* **Requests per second (RPS)**
* **Error rate under load**


---



