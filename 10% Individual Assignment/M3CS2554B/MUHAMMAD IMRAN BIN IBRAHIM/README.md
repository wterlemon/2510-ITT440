# MUHAMMAD IMRAN BIN IBRAHIM



## Result of load Test where the number of users ramps up (Table)

## K6 Stress Test Results - 20 VUs

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
