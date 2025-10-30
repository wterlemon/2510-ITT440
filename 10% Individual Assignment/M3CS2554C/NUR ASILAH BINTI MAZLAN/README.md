# Stress Testing on QuickPizza Using Grafana K6

## Table of Contents
1. [Abstract](#abstract)
2. [Introduction](#1-introduction)
3. [Hypothesis](#2-hypothesis)
4. [Tool Selection and Justification](#3-tool-selection-and-justification)
5. [Test Environment Setup](#4-test-environment-setup)
6. [Methodology and Execution](#5-methodology-and-execution)
7. [Results and Raw Data](#6-results-and-raw-data)
8. [Analysis and Interpretation](#7-analysis-and-interpretation)
9. [Recommendations and Best Practices](#8-recommendations-and-best-practices)
10. [Conclusion](#9-conclusion)
11. [Reflection](#10-reflection)
12. [Video Demonstration](#11-video-demonstration)

## **Abstract**

<p align="justify">
## 1. Introduction
Performance of web applications is fundamentally important to user’s pleasure and operational reliability. As applications scale, they need to be able to withstand increased traffic without sacrificing responsiveness or stability. Stress testing is one type of non-functional testing that observes how an application performs under extreme conditions. For example, the load will be gradually increased until the system is near or has exceeded its expected limits.

For purposes of the experiment, the QuickPizza demo website was chosen as the target system. The demo site provided static and dynamic content such as menu listings, news pages, and login forms. Thus, it was fitting for replicating realistic browsing and transaction activity. Grafana Cloud K6 is an open-source, cloud-based performance testing platform which was used to assess the website’s reaction as the number of simulated users increased. 
</p>

## 2. Hypothesis
The expectation was that the QuickPizza website would be stable and responsive under a moderate user load roughly for about 75 virtual users. However, we do expect to see some slight increases in response time and potential request failures as we push towards 100 concurrent users. The bottlenecks were expected to be in the higher latency for pages that needed server-side processing, but it was hoped that the static pages would continue to respond without issue. 

## 3. Tool Selection and Justification

### 3.1 Why Grafana Cloud K6

### 3.2 Comparison with Other Tools

## 4. Test Environment Setup


## 5. Methodology and Execution


## 6. Results and Raw Data

### 6.1 Graph Overview

### 6.2 Cloud Insights Summary

### 6.3 Threshold Evaluation

### 6.4 HTTP Summary

## 7. Analysis and Interpretation


## 8. Recommendations and Best Practices


## 9. Conclusion


## 10. Reflection


## 11. Video Demonstration

