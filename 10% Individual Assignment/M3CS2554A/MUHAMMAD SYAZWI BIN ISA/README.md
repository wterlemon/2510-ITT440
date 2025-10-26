# ITT440 - Web Application Performance Testing

**Name:** [MUHAMMAD SYAZWI BIN ISA]
**Matrix No:** [2024783361]
**Tool:** k6
**Test Type:** Spike Test

## 1. Introduction
A brief overview of performance testing and why it's important.

## 2. Tools and Application Under Test
- **Testing Tool:** k6 (explain why you chose it)
- **Application Under Test:** JSONPlaceholder API (`/posts` endpoint)

## 3. Objective
The goal of this spike test is to evaluate how the JSONPlaceholder API handles a sudden and massive increase in user traffic.

## 4. Test Scenario and Script
Explain the test scenario. Include your k6 script here in a code block.

## 5. Results
Present the key results in a table:

| Metric                | Value  |
| --------------------- | ------ |
| Average Response Time | 450ms  |
| Max Response Time     | 5.2s   |
| Request Failure Rate  | 2.1%   |
| Total Iterations      | 58,450 |

## 6. Analysis and Conclusion
Analyze the results. What do the numbers tell you? Did the system cope well with the spike? What would be the potential impact on real users?
(Example: "The 2.1% failure rate and high max response time indicate that the API's infrastructure is not elastic enough to handle sudden traffic spikes, which would lead to a poor user experience.")
