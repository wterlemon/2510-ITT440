# SITI NUR INSYIRAH BINTI HISHAMUDIN
## 📌What Is Performance Testing?

Performance testing is one of the most important parts to do after finishing development of a website such as load testing, stress testing, spike testing, and endurance testing. This performance testing helps to measure and identify the weakness of the website thus it will improve user experience and satisfaction when using the website. In addition, performance testing can also help to identify how the website performs under high traffic scenarios in order to know how the website responds or what are issues that the website faces in certain testing scenarios.

## What are the focuses of this test?

This test focuses on stress testing that will verify the stability of the website under extreme load conditions which determine what and when is the limitation of the website. Besides that, by doing stress tests we are able to identify the failure or breaking point of a library management system that is built with several languages like PHP, HTML, and CSS. 

In addition, in this test it will measure several important metric measurements such as response time, throughput, resource utilization performance, and error detection when running the test on the website within specified time.

The objective of this stress test is to evaluate the performance of a library management system website under a high number of users in some period of time or in other word when website is experiencing high-traffic (load), identify bottlenecks of the website, and suggest the best way to optimize the situation according to industry environment.


## ⚙️Tool Selection
<p align="center">
<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/cbb86a49-6bba-42a7-a9ad-043101588a56" />
</p>

| Feature | Description |
|----------|--------------|
| **Easy to Use** | Apache JMeter has a user-friendly graphical interface, especially useful for new users to explore and learn how to use the tool. It’s also ideal for those who prefer visual, graphical results. |
| **Variety of Built-In Tools** | Include many extensions and built-in tools helpful for beginners, such as PerfMon, the HTML Dashboard Generator, and Docker extensions. |
| **Free Open Source Tool** | A free, open-source performance testing tool. It requires no license or trial, making it cost-effective for newcomers in performance testing. |
| **Wide Range of Protocol Types** | JMeter supports various protocols like HTTP and HTTPS for web applications. It can simulate real-world scenarios using thread groups that users can configure themselves. |
| **Detailed Report Function** | JMeter provides multiple reporting options (e.g., Summary Report, Response Time Graph, Aggregate Report). Data can be saved in multiple formats such as `.jmx`, `.jtl`, and `.csv`. |

## 🧪 Test Environment & Configuration

**Test Environment**<br>
Below are testing environment for this stress test:

| Component | Details |
|------------|----------|
| **Application** | Visual Studio Code |
| **Language** | PHP 8.2, HTML, CSS |
| **Database** | phpMyAdmin |
| **Web Server** | Apache 2.4 |
| **Hosting** | XAMPP |
| **Operating System** | Windows 11 (64-bit) |
| **Hardware** | Intel Core i3, 8GB RAM |
| **Tool** | Apache JMeter 5.6 |
| **Browser** | Chrome 14.1 |
<br>

**⚙️ JMeter Configuration**

The test plan for stress testing using JMeter was configured as below.

| **Components** | **Details** |
|----------------|----------------------------|
| **Number of Stage Tests** | 12 |
| **Thread Groups** | Admin & User |
| **Number of Users** | 500 – 6000 |
| **Ramp-Up Period (s)** | 60 – 180 |
| **Loop Count** | 1 |
| **Server Path URL** | `localhost/LBM` |
| **Page Request Tested Paths** | 1. `/loginLibrary.php`<br>2. `/loginUser.php`<br>3. `/borrowing.php`<br>4. `/listBookLibrary.php`<br>5. `/logoutLibrary.php`<br>6. `/ogoutLibrary.php` |
| **Config Elements** | 1. HTTP Header Manager<br>2. HTTP Cookies Manager |
| **Delay Timer (ms)** | 3000 ms |
| **Listeners** | 1. Simple Data Writer<br>2. Aggregate Report<br>3. View Results Tree |
| **Built-in Tools** | Generate HTML Report |

## Methodology

This stress test has several scenarios or stages that were conducted in order to determine and identify when the performance of this website starts to drop, overload or in a bottleneck that leads to error. Each of the stages was tested and run three times to get overall and accurate results of the stress test for each of the stages with different number of users (thread). All of the pages are tested for both admin and user pages that are important to simulate realistic user behavior, from login pages to pages that contain create, read, update, and delete (CRUD) and lastly logout pages. The table below shows details of each stage. 

**Test Scenario**
- Number of stage: 12
- Each stage was tested 3 times and data were combined to get the accurate results of the stage.
- Sequence of pages tested: <br>1. Login Admin <br>
				         2. Login User <br>
         3. Manage Book <br>
                                                        4. Borrowing <br>
         5. Logout Admin <br>
         6. Logout User	<br>

| Stage | Number of Users | Duration (s) |
|:------:|:----------------:|:-------------:|
| 1 | 500 | 60 |
| 2 | 1000 | 60 |
| 3 | 1500 | 90 |
| 4 | 2000 | 90 |
| 5 | 2500 | 120 |
| 6 | 3000 | 120 |
| 7 | 3500 | 150 |
| 8 | 4000 | 150 |
| 9 | 4500 | 180 |
| 10 | 5000 | 180 |
| 11 | 5500 | 180 |
| 12 | 6000 | 180 |

There are some important key metric measures that are looked out in this test such as average response time (ms), throughput (s), error rate (%), percentile 90th and 95th response time. 

**Baseline Test**

Before starting to run the stress test for each stage, a baseline test will be done with 300 users within 50 seconds to ensure that the connection is stable and all of the components in good condition.

## Raw Data
<p align="center">
<img width="600" height="450" alt="Screenshot 2025-10-29 121214" src="https://github.com/user-attachments/assets/aa2960c0-eb8f-45d6-83be-2b15b6810c45" />
</p>

## Result
upcoming

### Type of Bottlenecks Observed

As the user thread at stage 10 until stage 12 which has 5000 to 6000 users within 180 seconds starts to load longer than usual and the error message below appears for all pages that failed to send the request.

**“Non HTTP response code: org.apache.http.conn.HttpHostConnectException/Non HTTP response message: Connect to localhost:80[localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect”**

**“Non HTTP response code: java.net.BindException/Non HTTP response message: Address already in use: connect”**

The first error message above has a means that the server was too busy to take or make new connections for upcoming new requests. Thus, the server decides to reject the request and that is why at this stage the website shows the error percentage which indicates the failure of requests. Besides that, the web application also takes a longer time to load because the new upcoming request is waiting for the server to process it.

The second error message indicates that the port to run the application is running out as this problem was actually coming from the client side which is the machine that is doing the test.

There are several identified bottlenecks based on the result, error message, and website situation as stated below:


| No. | Type of Bottleneck | Evidence |
|:---:|:--------------------|:----------|
| 1 | **Database Bottleneck** | Slow response to website applications, especially on login pages that handle important user data required for authentication. |
| 2 | **Connection Saturation** | The server cannot accept new incoming connections during the later stages of the test, leading to higher error rates on data-heavy pages such as login pages. New requests are dropped, causing failures. |
| 3 | **Socket/Port Exhaustion** | Connections to localhost on port 80 fail due to the server being unable to handle additional requests. Processor privilege time exceeds 25%, indicating heavy operating system usage. |


## RECOMMENDATIONS BASED ON INDUSTRY BEST PRACTICE

| Area | Recommendation |
|:------|:---------------|
| **Database Saturation** | Use proper indexing on all relevant columns and tables in database queries. This improves data retrieval and searching speed, reducing query execution time. |
| **Web Server** | Increase the maximum number of thread connection pools during high-traffic periods to handle sudden spikes in user load more efficiently. |
| **Server Side** | Optimize server-side code by minimizing synchronous or repetitive function calls. Ensure each session request is unique to reduce backend processing time, especially during login or logout operations. |
| **Caching** | Enable caching at multiple layers — application, database, and browser. This reduces server load and minimizes redundant requests to the backend and database. |

##Video Demonstration



