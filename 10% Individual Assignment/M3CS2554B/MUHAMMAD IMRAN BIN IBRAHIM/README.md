# MUHAMMAD IMRAN BIN IBRAHIM

<img width="900" height="700" alt="K6_software_logo svg" src="https://github.com/user-attachments/assets/0d9ea5f2-686b-4115-944c-9ed9631744f5" />

## Introduction to Performance Testing with k6

| **Section**                         | **Description**                                                                                                                                                                                                                       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 💡 **What is Performance Testing?** | Performance testing is the process of evaluating how a system behaves under specific workload conditions. It helps identify bottlenecks, measure response times, and ensure your application can handle expected traffic.             |
| ⚙️ **What is k6?**                  | k6 is an open-source, developer-centric performance testing tool developed by Grafana Labs. It’s designed for testing the performance of APIs, microservices, and websites.           

## Objective 

Why We Do Performance Testing

| **Category**                | **Details**                                                  |
| --------------------------- | ------------------------------------------------------------ |
| 🎯 **Main Goals**           |                                                              |
| 1️⃣                         | Find how many users your website can handle                  |
| 2️⃣                         | Make sure your website doesn't crash when many people use it |
| 3️⃣                         | Check if your website loads fast enough                      |
| 4️⃣                         | Find problems before real users do                           |
| 🔍 **What We Want to Know** |                                                              |
| 1️⃣                         | How fast does your website load?                             |
| 2️⃣                         | Can 100 people use it at the same time?                      |
| 3️⃣                         | What happens when 1000 people visit?                         |
| 4️⃣                         | Does it work the same way every time?                        |
| 🧩 **What We Find**         |                                                              |
| 1️⃣                         | Slow pages that need fixing                                  |
| 2️⃣                         | Parts that break under heavy load                            |
| 3️⃣                         | How much traffic your site can handle                        |
| 4️⃣                         | When you need better servers                                 |

## 🧰 Test Environment Overview

| Component                   | Tool / Platform                                                   | Purpose                                                        |
| --------------------------- | ----------------------------------------------------------------- | -------------------------------------------------------------- |
| 💻 **Load Generator**       | **K6 running on Kali Linux (VirtualBox)**                         | Used to simulate multiple virtual users and send HTTP requests |
| 📊 **Monitoring Dashboard** | **Grafana** + **InfluxDB**                                        | Collects and visualizes K6 test metrics in real-time           |
| 🌍 **Target System**        | Your **web application / API** (status = 200 OK for all requests) | The app being tested, hosted locally or remotely               |
| 🧩 **Data Source**          | InfluxDB v1.x (`http://localhost:8086`)                           | Stores K6 output metrics for Grafana visualization             |
| 🧱 **Host Machine**         | Likely Windows 10 (VirtualBox host)                               | Runs both Grafana (via browser) and Kali VM for load testing   |



## Result of load Test where the number of users ramps up (Table)

| Section | Metric | Result | Explanation |
|---------|--------|--------|-------------|
| **Scenario** | Virtual Users (VUs) | 20 max | Tested with up to 20 concurrent users |
| | Test Duration | 1 minute 41 seconds | Included ramp-up and graceful stop periods |
| **Thresholds** | Status Check | 100% passed (1022/1022) | All response status checks returned 200 |
| | HTTP Requests Failed | 0.00% | No failed requests - system remained stable |
| **Total Results** | Checks | 1,022 total (100% passed) | All validations succeeded during the test |
| | HTTP Requests | 2,044 total | Total number of requests made to the server |
| | Requests per Second | 20.16 req/s | Consistent request rate throughout the test |
| **HTTP Performance** | Average Duration | 283.18 ms | Mean response time for all requests |
| | Minimum Time | 12.26 ms | Fastest recorded response time |
| | Maximum Time | 8.6 s | Slowest recorded response time |
| | 90th Percentile | 664.73 ms | 90% of requests completed within this time |
| | 95th Percentile | 1.12 s | 95% of requests completed within this time |
| | Median Time | 160.22 ms | Middle value of all response times |
| **Execution** | Iterations Completed | 1,022 | Total number of test cycles executed |
| | Iterations per Second | 10.08 iter/s | Rate of test iterations |
| | Iteration Duration | 1.58 s average | Average time per complete test cycle |
| | VUs Range | 1 to 20 users | Virtual users scaled during the test |
| **Network** | Data Received | 3.8 MB (37 kB/s) | Total data downloaded from server |
| | Data Sent | 114 kB (1.1 kB/s) | Total data uploaded to server |
| **Cloud** | Grafana Dashboard | Available online | Full results at provided Grafana Cloud URL |

## Result of load Test where the number of users ramps up (Graph)

![Screenshot 2025-11-01 135811](https://github.com/user-attachments/assets/ac34b07e-99c3-4b13-9712-38170125a2c9)


## Result of Stress Test (Table)




| 🔹 Section              | 📊 Metric            | 📈 Result                    | 💬 Explanation                                                      |
| ----------------------- | -------------------- | ---------------------------- | ------------------------------------------------------------------- |
| **👥 Scenario**         | Virtual Users (VUs)  | **90 max**                   | You tested with up to 90 users at the same time.                    |
|                         | Test Duration        | **≈ 20 min 30 sec**          | Includes ramp-up and graceful stop (smooth ending).                 |
| **🎯 Thresholds**       | `http_req_duration`  | ✅ p(95) = **282.25 ms**      | 95% of requests finished under 0.3 seconds ⚡ (Excellent speed).     |
|                         | `http_req_failed`    | ✅ **0.00%**                  | No failed requests at all — stable and reliable 💪                  |
| **📊 Total Results**    | Checks               | ✅ 56,902 total (100% passed) | All response checks succeeded! 🎉                                   |
|                         | Requests Sent        | **227,608 total**            | That’s how many HTTP requests were made during the test.            |
| **🌐 HTTP Performance** | Average Duration     | **143.98 ms**                | Each request took about 0.14 seconds on average ⚡                   |
|                         | Min / Max Time       | **11.25 ms / 2.43 s**        | Fastest request = 11 ms, slowest = 2.4 s (still under threshold 👍) |
|                         | p(90) / p(95)        | **275 ms / 282 ms**          | 90% and 95% of requests were very quick 🚀                          |
| **⚙️ Execution**        | Iterations Completed | **28,451**                   | Total test loops executed by all VUs.                               |
|                         | Iteration Duration   | **~2.3 s avg**               | Each “user loop” lasted about 2 seconds.                            |
|                         | Active VUs           | **90 constant**              | Held steady load throughout test 🧍‍♂️🧍‍♀️🧍‍♂️                    |
| **📡 Network**          | Data Received        | **403 MB (335 kB/s)**        | That’s how much data the test got from the server.                  |
|                         | Data Sent            | **11 MB (8.8 kB/s)**         | Outgoing requests from your test script.                            |


## Result of Stress Test (Graph)




![Screenshot 2025-11-01 133907](https://github.com/user-attachments/assets/92f2db85-f68e-482f-9f75-f0450f739807)
