# MUHAMMAD IMRAN BIN IBRAHIM
## Result of load Test where the number of users ramps up (Table)


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
