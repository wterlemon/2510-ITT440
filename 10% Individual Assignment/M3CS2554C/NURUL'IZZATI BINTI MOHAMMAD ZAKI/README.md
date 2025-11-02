🎯 Performance Testing of JSONPlaceholder API Using Artillery

Name: Nurul’Izzati binti Mohammad Zaki
Student ID: 2025395205
Class: M3CS2554c

🎥 Demo Video: Watch on YouTube

🧭 Overview

This project focuses on performing load testing on the JSONPlaceholder API using Artillery, an open-source performance testing tool.
The goal is to evaluate the stability, response time, and throughput of the API when exposed to different levels of user load.

🧪 Hypothesis

The JSONPlaceholder API will remain stable and responsive under increasing load, with an average response time below 500 milliseconds and only minor latency spikes during heavy load.

⚙️ Tool Selection and Justification

Chosen Tool: Artillery (Node.js-based load testing framework)

Reasons for Choosing Artillery
Justification	Description
🎯 Ease of use	Simple YAML-based configuration files
📊 Detailed metrics	Provides latency percentiles, response time, and request rate
☁️ Cloud visualization	Supports Artillery Cloud for live reporting
💻 Lightweight	Runs easily on most local systems
🧩 Industry relevance	Commonly used in CI/CD and API testing

Artillery is widely trusted in the software industry and provides realistic simulations of user traffic while producing clear and detailed reports.

🧩 Test Environment Setup
Component	Description
Operating System	Windows 10
Node.js Version	v18
Artillery Version	v2.x
Target URL	https://jsonplaceholder.typicode.com
🧱 Test Configuration (Scenario Design)

Each virtual user (VU) performs the following actions:

Step	Action	Endpoint	Method
1	Retrieve a post	/posts/1	GET
2	Retrieve a user	/users/1	GET
3	Create a post	/posts	POST
4	Wait time	1 second	—
📈 Load Phases
Phase	Duration	Arrival Rate	Ramp To	Description
Low Load	30s	2 users/sec	5 users/sec	Light traffic baseline
Moderate Load	60s	5 users/sec	10 users/sec	Normal user activity
Heavy Load	90s	10 users/sec	15 users/sec	Stress-level testing
🧰 Test Execution Commands
Step 1: Run test and save results locally
artillery run jsonplaceholder-load-test.yml -o results/test_output.json


✅ Saves results to the results folder for local analysis.

Step 2: Upload test results to Artillery Cloud for graph reporting
npx artillery run --record --key a9_0tq4lp6lw0dzc98nrnt4toupnc982ng0 --output "results/jsonplaceholder-load-test-report.json" jsonplaceholder-load-test.yml


✅ Uploads data to Artillery Cloud for visualization and also stores the JSON report locally.

📊 Test Summary
Metric	Result
Total Duration	3 minutes 6 seconds
Total Requests Sent	5,040
Completed Requests	5,040
Failed Requests	0
Average Request Rate	44 requests/sec
Average Response Time	126.1 ms
95th Percentile	320.6 ms
99th Percentile	415.8 ms
Error Rate	0%
Virtual Users	1,680
📉 Data Analysis
🔹 Throughput

Increased steadily from 20 req/sec (low load) to 48 req/sec (heavy load).

The API handled higher traffic efficiently without errors.

🔹 Response Time
Metric	Value
Minimum	3 ms
Mean	126.1 ms
Median (p50)	67.4 ms
95th Percentile	320.6 ms
99th Percentile	415.8 ms
Maximum	1,070 ms

95% of requests completed in under 0.3 seconds, indicating strong stability and responsiveness.

🔹 HTTP Status Codes
Status Code	Count	Meaning
200	3,360	Successful GET requests
201	1,680	Successful POST requests
Errors	0	No failed requests
📉 Graph Interpretation (Artillery Cloud)

The following graphs were obtained from Artillery Cloud.

Metric	Graph Description
Request Rate	Gradually increases across phases, showing smooth user ramp-up.
Response Time (p95)	Slight increase during heavy load but remains consistent overall.
Virtual Users	Steady rise in VUs showing consistent load generation.

🖼️ Insert your Artillery Cloud screenshots here:

![Artillery Cloud Graph 1](results/artillery-graph-1.png)
![Artillery Cloud Graph 2](results/artillery-graph-2.png)

🧠 Interpretation and Discussion

The API remained stable and responsive throughout the test.

There were no failed requests or performance drops.

Even under heavy load, response times stayed under 500 ms for most requests.

Small latency spikes above 1 second appeared rarely (only at p99 level).

Overall, JSONPlaceholder demonstrated excellent performance and stability.

⚠️ Identified Bottlenecks
Observation	Impact
Minor latency spikes at high load	Minimal impact on user experience
Limited backend visibility	Could not measure server CPU/Memory due to public API restrictions
Network variability	Small response time differences due to global server distance
🧭 Recommendations and Test Plan Justification
Recommendations for Real-World Scenarios

Use caching and CDNs to reduce load on backend servers.

Integrate monitoring tools such as Prometheus or Grafana to observe resource usage.

Perform additional tests like stress and soak tests to discover system limits.

Test from multiple regions to measure global latency and network behavior.

Test Plan and Tool Justification
Aspect	Explanation
Test Plan Design	Gradual user ramp-up from low to heavy load to simulate real usage and avoid sudden spikes.
Tool Choice	Artillery was selected for its reliability, percentile-based reporting, and cloud integration.
Industry Relevance	Artillery follows best practices aligned with ISO/IEC 25010 and ISTQB testing standards.
Empirical Results	Consistent throughput, low latency, and zero errors validate the accuracy of the test design.

By following these practices, developers can ensure stable, optimized, and scalable applications even before deployment.

🏁 Conclusion

The load testing performed on JSONPlaceholder using Artillery successfully validated the hypothesis.
The API remained stable under all load phases, completing 5,040 requests with zero errors and maintaining an average response time of 126 ms.

This demonstrates that:

JSONPlaceholder is capable of handling high traffic efficiently.

Artillery is an excellent open-source tool for realistic load testing.

Overall, this project confirms that performance testing using Artillery is effective, reliable, and essential for evaluating API stability and scalability.

