#  Web Performance Analysis : GitHub Repository Load Speed Using GTMetrix

####  STUDENT NAME : NUR IMAN SHAZREEN BINTI MOHD HAZLEE
####  ITT440 - INDIVIDUAL ASSIGNMENT 
####  GROUP : M3CS2554C

---
## Introduction
This report documents the performance analysis of a publicly hosted GitHub repository page (https://github.com/NurImanShazreen/Individual-Assignment-ITT440.git) using the GTMetrix web performance auditing tool. The primary goal of this analysis is to establish a performance baseline, identify existing inefficiencies, and recommend actionable strategies for optimization. The test was conducted on **October 31 2025**, from the **Seattle, WA, USA** test server location.

---
## Objectives
The core objectives of this performance analysis are:

 1. To evaluate the overall load speed and efficiency of the target GitHub repository page using industry-standard metrics, including Google's Core Web Vitals. 
 2. To establish a quantifiable performance baseline by determining the **Performance Score** and **Structure Score**.
 3. To identify and interpret specific performance indicators such as **LCP, TBT, CLS, and TTI**.
 4. To pinpoint structual and content-related bottlenecks, such as slow asset delivery or inefficient code practices, by analyzing the GTMetrix Structure Audits.
 5. To provide a concise summary of findings and initial recommendations for performance improvement. 

---
### What is a Load Speed?
Load speed or web performance is a measure of how quickly a web page's content becomes fully visible and interactive to the user. It encompasses several key phases, starting from the moment a user requests a URL until the page is visually stable and able to respond reliably to user inputs. High load speed translates directly into a better User Experience (UX).

Key metrics, particularly the **Core Web Vitals (LCP, FID/TBT, CLS)**, are used by tools like GTMetrix to measure 3 aspects of UX: loading, interactivity, and visual stability.

---
### Tool Selection Justification
|Feature | Description |
|---------|------------|
|**User-centric Metrics** | Clear scoring based on metrics that reflect the actual user experience. |
|**Actionable Diagnostics** | Detailed structure audits, complete with **Impact Levels** (Low, Medium, High) and specific potential savings, allowing for targeted optimization efforts. |
|**Waterfall Chart** | A visua breakdown of every single resource request (CSS, JS, images), crucial for identifying specific slow-loading files. | 

---
### Test Environment Setup
|Parameter | Configuration | Justification |
|----------|---------------|---------------|
|**Tested URL** | https://github.com/NurImanShazreen/Individual-Assignment-ITT440.git | The specific target page URL |
|**Test Server Location** | Seattle, WA, USA | Used as the initial baseline test environment. A more representative location is recommended for future tests targeting an Asian audience to account for realistic network latency. |
|**Browser** | Chrome (Version 125.0.0.0) | Standard test browser, reflecting the most common modern user agent. |
|**Connection Speed** | Unthrottled (Simulated) | Measures performance under ideal network conditions to isolate server and code inefficiencies. | 

---
### Methodology
|Step | Description |
|-----|-------------|
|**Baseline test Execution** | The target URL was submitted to GTMetrix with the specified environment settings. |
|**Data Extraction and Categorization** | The resulting report data was systematically extracted and categorized into 3 groups: **Overall Scores, Performance Metrics(Core Web Vitals)** and **Structural Audits**. |
|**Interpretation** | Each metric and audit finding was interpreted against accepted industry thresholds to determine teh grade (**Good, OK, Poor**) and identify the areas requiring the most urgent attention. |

---
### Performance Data Analysis 
The performance analysis provided the following key results:

**8.1 Overall Scoring**
|Score/Metric | Value | Interpretation |
|-------------|-------|----------------|
|**Performance Score** | B (86%) | Good performance, but indicates room for optimization to achieve an 'A' grade. |
|**Structure Score** | 92% |Excellent structure and adherence to best practices, suggesting the performance issues are minor and specific. | 
|**Fully Loaded Time** | 2.4s | The total time for the page to completely stop all activity, it is a good overall result. |
|**Total Page Size** | 1.17 MB | A moderate size, dominated by JavaScript (931KB). |
|**Total Page Requests** | 121 | A relatively high number of file requests, which can increase latency overhead. |

**8.2 Core Web Vitals (User Experience Metrics)**
|Metric | Value | Threshold (GTMetrix Goal) | Status |
|-------|-------|---------------------------|--------|
|**Largest Contenful Paint (LCP)** | 1.1s | &le; 1.2s | Good |
|**Total Blocking Time** | 250ms | &le; 150ms | Needs Improvement |
|**Cumulative Layout Shift** | 0.01 | &le; 0.1 | Good | 

---


