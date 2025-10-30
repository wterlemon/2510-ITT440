# 🚀Web App performance Stress Testing Using Apache JMeter
BY: SITI NUR INSYIRAH BINTI HISHAMUDIN<br>
STUDENT ID: 2025128335<br>
GROUP: M3CDCS2554C<br>

## 📌What Is Performance Testing?

Performance testing is one of the most important parts to do after finishing development of a website such as load testing, stress testing, spike testing, and endurance testing. This performance testing helps to measure and identify the weakness of the website thus it will improve user experience and satisfaction when using the website. In addition, performance testing can also help to identify how the website performs under high traffic scenarios in order to know how the website responds or what are issues that the website faces in certain testing scenarios.
<br>

## 🧐What are the focuses of this test?

This test focuses on stress testing that will verify the stability of the website under extreme load conditions which determine what and when is the limitation of the website. Besides that, by doing stress tests we are able to identify the failure or breaking point of a library book management that is built with several languages like PHP, HTML, and CSS. 

In addition, in this test it will measure several important metric measurements such as response time, throughput, resource utilization performance, and error detection when running the test on the website within specified time.

The objective of this stress test is to evaluate the performance of the website under a high number of users in some period of time or in other word when website is experiencing high-traffic (load), identify bottlenecks of the website, and suggest the best way to optimize the situation according to industry environment.
<br>

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
<br> 

## 🧪 Test Environment & Configuration

**1️⃣ Test Environment**

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
| **Resource Utilization Tool** | Performance Monitor |
| **Browser** | Chrome 14.1 |
<br>

**2️⃣ JMeter Configuration**

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
| **Example Full path** | localhost/LBM/loginLibrary.php |

<br>

## 🔍Methodology

This stress test has several scenarios or stages that were conducted in order to determine and identify when the performance of this website starts to drop, overload or in a bottleneck that leads to error. Each of the stages was tested and run three times to get overall and accurate results of the stress test for each of the stages with different number of users (thread). All of the pages are tested for both admin and user pages that are important to simulate realistic user behavior, from login pages to pages that contain create, read, update, and delete (CRUD) and lastly logout pages. The table below shows details of each stage. 

ℹ️ <ins> **Test Scenario** </ins>
- Number of stages: 12
- Each stage was tested 3 times and data were combined to get the accurate results of the stage.
- Sequence of pages tested: <br>1. Login Admin <br>
				         2. Login User <br>
         3. Manage Book <br>
                                                        4. Borrowing <br>
         5. Logout Admin <br>
         6. Logout User	<br>

<div align="center">

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

</div>
<br>

There are some important key metrics to be measures in this stress test such as average response time (ms), throughput (s), error rate (%), percentile 90th and 95th response time.

| Metric | Explanation |
|------------|----------|
| **Average Response Time** | The total time elapsed from when a client sends a request to a server until the client receives the complete response from that server. |
| **Throughput** | Number of requests or transactions a system processes per second under simulated workloads. |
| **Percentile 90th** | Response time below which 90% of all request fall. |
| **Percentile 95th** | Response time below which 95% of all request fall. |
| **Error** | Number of request that is failed or did not receive a response |

<br>

ℹ️ <ins> **Baseline Test** </ins>

Before starting to run the stress test for each stage, a baseline test will be done with 300 users within 50 seconds to ensure that the connection is stable and all of the components in good condition.

## 📈Raw Data
<p align="center">
<img width="514" height="270" alt="Screenshot 2025-10-29 204453" src="https://github.com/user-attachments/assets/d123442b-4b73-49d8-bf48-b3cd00fff208" /> </p>

<p align="center">
<img width="514" height="270" alt="Screenshot 2025-10-29 121214" src="https://github.com/user-attachments/assets/aa2960c0-eb8f-45d6-83be-2b15b6810c45" />
</p>

<p align="center">
<img width="514" height="270" alt="image" src="https://github.com/user-attachments/assets/35e1a282-5e67-4ddc-a415-2e5471af6445" /> </p>

<p align="center">
<img width="550" height="270" alt="Screenshot 2025-10-29 210913" src="https://github.com/user-attachments/assets/85b1e1ae-8f40-4a5f-96ca-db6002c94f78" /> </p>

## 📝Result
<div align="center">

<table style="border-collapse: collapse; width: 95%; border: 1px solid #555; border-radius: 10px; overflow: hidden;">
  <thead style="background-color:#222; color:#fff;">
    <tr>
      <th style="border: 1px solid #555; padding: 8px;">Stage</th>
      <th style="border: 1px solid #555; padding: 8px; width: 150px;">Number of Users</th>
      <th style="border: 1px solid #555; padding: 8px;">Metric</th>
      <th style="border: 1px solid #555; padding: 8px;">Observations</th>
    </tr>
  </thead>
  <tbody>
    <!-- Stage 1–3 -->
    <tr style="background-color:#333; color:#fff;">
      <td rowspan="4" style="border: 1px solid #555; padding: 8px;">1 – 3</td>
      <td rowspan="4" style="border: 1px solid #555; padding: 8px;">500 – 1500</td>
      <td style="border: 1px solid #555; padding: 8px;">Average Response Time</td>
      <td style="border: 1px solid #555; padding: 8px; text-align:left;">
        • Login/Logout &lt; 5%<br>
        • Borrow Book (User) &lt; 4%<br>
        • Manage Book (Admin) 5–8% (higher)
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Success Request Response Time (P90 & P95)</td>
      <td style="border: 1px solid #555; padding: 8px;">
		  • P90–P95 decrease ≤ 2%<br>
		  • Manage Book +5% from P90</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Throughput</td>
      <td style="border: 1px solid #555; padding: 8px;">Increases as users increase</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Resource Utilization</td>
      <td style="border: 1px solid #555; padding: 8px;">CPU 35–45%</td>
    </tr>
    <!-- Stage 4–5 -->
    <tr style="background-color:#333; color:#fff;">
      <td rowspan="4" style="border: 1px solid #555; padding: 8px;">4 – 5</td>
      <td rowspan="4" style="border: 1px solid #555; padding: 8px;">2000 – 2500</td>
      <td style="border: 1px solid #555; padding: 8px;">Average Response Time</td>
      <td style="border: 1px solid #555; padding: 8px; text-align:left;">
       • Login Admin +0.08 ms, User +0.3 ms<br>
       • Logout Admin +0.11 ms, User +0.01 ms<br>
       • Manage Book +0.56 ms<br>
       • Borrow Book +0.19 ms
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Success Request Response Time (P90 & P95)</td>
      <td style="border: 1px solid #555; padding: 8px;">Manage Book ↑</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Throughput</td>
      <td style="border: 1px solid #555; padding: 8px;">↓ 0.27% (all pages)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Resource Utilization</td>
      <td style="border: 1px solid #555; padding: 8px;">CPU 41–44.1%</td>
    </tr>
    <!-- Stage 6–7 -->
    <tr style="background-color:#333; color:#fff;">
      <td rowspan="4" style="border: 1px solid #555; padding: 8px;">6 – 7</td>
      <td rowspan="4" style="border: 1px solid #555; padding: 8px;">3000 – 3500</td>
      <td style="border: 1px solid #555; padding: 8px;">Average Response Time</td>
      <td style="border: 1px solid #555; padding: 8px; text-align:left;">
        • Login ↑ at stage 6, ↓ at stage 7<br>
        • Manage Book ↑ then ↓ at stage 7<br>
        • Borrow stable<br>
        • Logout Admin +0.01 ms, User ↓
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Success Request Response Time (P90 & P95)</td>
      <td style="border: 1px solid #555; padding: 8px;">P90/P95 ↓ (Login & Manage Book)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Throughput</td>
      <td style="border: 1px solid #555; padding: 8px;">↓ at Stage 7</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Resource Utilization</td>
      <td style="border: 1px solid #555; padding: 8px;">
		  • CPU ↑ stage 6, slight ↓ stage 7<br>
		  • Privilege &gt; 25%</td>
    </tr>
    <!-- Stage 8–9 -->
    <tr style="background-color:#333; color:#fff;">
      <td rowspan="4" style="border: 1px solid #555; padding: 8px;">8 – 9</td>
      <td rowspan="4" style="border: 1px solid #555; padding: 8px;">4000 – 4500</td>
      <td style="border: 1px solid #555; padding: 8px;">Average Response Time</td>
      <td style="border: 1px solid #555; padding: 8px; text-align:left;">
        • Login 4000 → 500 ms<br>
        • Manage Book 14 → 8 ms<br>
        • Borrow 5.49% → 3.9%<br>
        • Logout ↑ stage 8, ↓ &gt; 0.01 ms stage 9
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Success Request Response Time (P90 & P95)</td>
      <td style="border: 1px solid #555; padding: 8px;">P90/P95 ↑ (Login, Manage Book, Borrow)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Throughput</td>
      <td style="border: 1px solid #555; padding: 8px;">Increased</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Resource Utilization</td>
      <td style="border: 1px solid #555; padding: 8px;">
		  • CPU 42–45%<br>  
		  • Privilege &gt; 25%</td>
    </tr>
    <!-- Stage 10 -->
    <tr style="background-color:#333; color:#fff;">
      <td rowspan="5" style="border: 1px solid #555; padding: 8px;">10</td>
      <td rowspan="5" style="border: 1px solid #555; padding: 8px;">5000</td>
      <td style="border: 1px solid #555; padding: 8px;">Average Response Time</td>
      <td style="border: 1px solid #555; padding: 8px;">
		  • ↑ Increase sharply (Login, Borrow, Manage Book)<br>
		  • Logout Admin stable</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Error Rate</td>
      <td style="border: 1px solid #555; padding: 8px;">
        • Login Admin 1.01%, User 1.07%<br>
        • Manage Book 0.10%, Borrow 0.11%<br>
        • Logout 0% error but ↑ Response Time & P90/P95
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Success Request Response Time (P90 & P95)</td>
      <td style="border: 1px solid #555; padding: 8px;">P90/P95 ↑ except Logout Admin</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Throughput</td>
      <td style="border: 1px solid #555; padding: 8px;">Increased</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Resource Utilization</td>
      <td style="border: 1px solid #555; padding: 8px;">
		• CPU 43%<br> 
		• Privilege &gt; 25%</td>
    </tr>
    <!-- Stage 11 -->
    <tr style="background-color:#333; color:#fff;">
      <td rowspan="5" style="border: 1px solid #555; padding: 8px;">11</td>
      <td rowspan="5" style="border: 1px solid #555; padding: 8px;">5500</td>
      <td style="border: 1px solid #555; padding: 8px;">Average Response Time</td>
      <td style="border: 1px solid #555; padding: 8px;">
       • Login ↑ to 12,000 ms<br>
       • Manage Book/Borrow ↑ to 700 ms<br>
       • Logout ↑ to 200 ms
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Error Rate</td>
      <td style="border: 1px solid #555; padding: 8px;">
        • Login 16–17%<br> 
		• Manage Book & Borrow 6%<br> 
		• Logout &lt; 3%
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Success Request Response Time (P90 & P95)</td>
      <td style="border: 1px solid #555; padding: 8px;">P90/P95 ↑ (all pages)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Throughput</td>
      <td style="border: 1px solid #555; padding: 8px;">Increased</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Resource Utilization</td>
      <td style="border: 1px solid #555; padding: 8px;">
		  • CPU 55%<br> 
		  • Privilege 32%</td>
    </tr>
    <!-- Stage 12 -->
    <tr style="background-color:#333; color:#fff;">
      <td rowspan="5" style="border: 1px solid #555; padding: 8px;">12</td>
      <td rowspan="5" style="border: 1px solid #555; padding: 8px;">6000</td>
      <td style="border: 1px solid #555; padding: 8px;">Average Response Time</td>
      <td style="border: 1px solid #555; padding: 8px;">
       • Login ↑ to 12,000 ms<br>
       • Manage Book/Borrow ↑ to 1900 ms<br>
       • Logout ↑ to 700 ms
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Error Rate</td>
      <td style="border: 1px solid #555; padding: 8px;">
       • Login ≈ 18%<br> 
       • Manage Book/Borrow 7–8%<br> 
	   • Logout ≈ 4%
      </td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Success Request Response Time (P90 & P95)</td>
      <td style="border: 1px solid #555; padding: 8px;">P90/P95 ↑ (all pages)</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Throughput</td>
      <td style="border: 1px solid #555; padding: 8px;">Increased</td>
    </tr>
    <tr>
      <td style="border: 1px solid #555; padding: 8px;">Resource Utilization</td>
      <td style="border: 1px solid #555; padding: 8px;">
		  • CPU ↑ 93.8%<br> 
		  • Privilege ↑ 40.16%</td>
    </tr>

  </tbody>
</table>

</div>
<br>

### ➤Type of Bottlenecks Observed

As the user thread at stage 10 until stage 12 which has 5000 to 6000 users within 180 seconds starts to load longer than usual and the error message below appears for all pages that failed to send the request.

***“Non HTTP response code: org.apache.http.conn.HttpHostConnectException/Non HTTP response message: Connect to localhost:80[localhost/127.0.0.1, localhost/0:0:0:0:0:0:0:1] failed: Connection refused: connect”***

***“Non HTTP response code: java.net.BindException/Non HTTP response message: Address already in use: connect”***

The first error message above has a means that the server was too busy to take or make new connections for upcoming new requests. Thus, the server decides to reject the request and that is why at this stage the website shows the error percentage which indicates the failure of requests. Besides that, the web application also takes a longer time to load because the new upcoming request is waiting for the server to process it.

The second error message indicates that the port to run the application is running out as this problem was actually coming from the client side which is the machine that is doing the test.

There are several identified bottlenecks based on the result, error message, and website situation as stated below:

| No. | Type of Bottleneck | Evidence |
|:---:|:--------------------|:----------|
| 1 | **Database Bottleneck** | Slow response to website applications, especially on login pages that handle important user data required for authentication. |
| 2 | **Connection Saturation** | The server cannot accept new incoming connections during the later stages of the test, leading to higher error rates on data-heavy pages such as login pages. New requests are dropped, causing failures. |
| 3 | **Socket/Port Exhaustion** | Connections to localhost on port 80 fail due to the server being unable to handle additional requests. Processor privilege time exceeds 25%, indicating heavy operating system usage. |
<br>

## ✅RECOMMENDATIONS BASED ON INDUSTRY BEST PRACTICE

| Area | Recommendation |
|:------|:---------------|
| **Database Saturation** | Use proper indexing on all relevant columns and tables in database queries. This improves data retrieval and searching speed, reducing query execution time. |
| **Web Server** | Increase the maximum number of thread connection pools during high-traffic periods to handle sudden spikes in user load more efficiently. |
| **Server Side** | Optimize server-side code by minimizing synchronous or repetitive function calls. Ensure each session request is unique to reduce backend processing time, especially during login or logout operations. |
| **Caching** | Enable caching at multiple layers — application, database, and browser. This reduces server load and minimizes redundant requests to the backend and database. |
<br>

## 📃CONCLUSION
Library book management website performance decreases and reaches the critical breaking point when there are 6000 users trying to access it within 180 seconds where the  system also starts to load slower than usual compared to when the number of users is less than 5000. Although the throughput remains stable the system also fails to process the new upcoming request since the server is saturated which also causes operating system percentage in processor privilege to increase more than 25%. 

Furthermore, at the last stage which had 6000 users the average response time for all pages that are tested increases sharply up to 12000 ms which a huge difference compared to the stage before 5000 users and the website application starts to return “This site can’t be reached” also when trying to navigate to other pages as it will take more than 10 seconds to retrieve the website back.

Next, the CPU usage reaches the peak of 93% when there are 6000 users which shows that the CPU is overloaded as there are too many requests that come in a short period of time. The privilege percentage also increased more than 40% that led to usage of the operating system exceeding normal usage. 

The total error rate of the website increases up to 10.06% higher than other stages. Error percentage rate for login pages is up to 18% because these pages required the usage of data from database and backend to process it to get access into the system. Furthermore, managing book and borrowing pages is the second highest percentage of error rate in between 7% to  8% as it also requires the user to fill up form and edit pages like delete or modify data thus these pages will take a lot of time to send and retrieve data from and to the database.

Last but not least, the logout pages have the least error that is below 4% but also have higher average response time up to 11000 ms which indicates that logout pages have trouble within the sessions as it took longer for the server to end each session of the pages.

In summary, this website's critical breaking point is when the number of users is 6000 which the CPU is almost reaching 100% usage that leads the database, backend, and server to crash thus cannot perform efficiently to complete all of the requests to the web server that lead to error.


## ▶️Video Demonstration



