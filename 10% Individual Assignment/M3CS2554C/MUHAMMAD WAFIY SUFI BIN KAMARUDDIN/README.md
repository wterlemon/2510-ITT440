# Analyzing Banking Web Application Stability Through Spike Testing

# Introduction
This report presents the results of spike testing conducted on the Parabank web application — a dummy online banking site used for testing purposes. The goal is to observe how the system handles sudden increases in user load and how it recovers once the traffic drops.
# Objective
- To evaluate system performance during sudden user load spikes.
- To monitor response time, error rate, and recovery time.
- To assess the stability and reliability of the Parabank website.
# Scope

The Spike Test focus on 

- login page perfomance
- checkout process under high load

# Tool Used
| Tool | Purpose |
|-----------|-----------|
| Locust | Load and spike testing tool | 
| Parabank | A dummy banking website for testing |

# Test Summary 200 User
| Time Period  | Number Of User | Response time (ms) | Total request Per Second |
|-----------|-----------|-----------|-----------|
| **11:01 PM - 11:10 PM** | **Ramps up linearly from 0 to ~200 users.** | **Both 50th and 95th percentiles rise linearly, showing the system is getting slower under load** | **- RPS (Green): Stable. - Failures/s (Red): Flat at 0.** |
| 11:10 PM | Reaches the maximum load of ~200 users. | Response times (especially 95th percentile) shoot up to over 2,000 ms (2 seconds).| - Failures/s (Red): Spikes sharply from 0 to over 60 failures/second. |
| 11:10:20 PM – 11:11 PM | Load is held steady at ~200 users. | Response times drop suddenly. This is misleading; it's low because requests are failing instantly, not succeeding quickly.| - Failures/s (Red): Stays high, showing the system is continuously failing and cannot recover under this load. |


