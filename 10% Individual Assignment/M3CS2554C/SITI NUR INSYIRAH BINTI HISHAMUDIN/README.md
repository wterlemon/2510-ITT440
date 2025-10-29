# SITI NUR INSYIRAH BINTI HISHAMUDIN
# 📌What Is Performance Testing?

Performance testing is one of the most important parts to do after finishing development of a website such as load testing, stress testing, spike testing, and endurance testing. This performance testing helps to measure and identify the weakness of the website thus it will improve user experience and satisfaction when using the website. In addition, performance testing can also help to identify how the website performs under high traffic scenarios in order to know how the website responds or what are issues that the website faces in certain testing scenarios.

# What are the focuses of this test?

# ⚙️Tool Selection

<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/cbb86a49-6bba-42a7-a9ad-043101588a56" />

| Feature | Description |
|----------|--------------|
| **Easy to Use** | Apache JMeter has a user-friendly graphical interface, especially useful for new users to explore and learn how to use the tool. It’s also ideal for those who prefer visual, graphical results. |
| **Variety of Built-In Tools** | Include many extensions and built-in tools helpful for beginners, such as PerfMon, the HTML Dashboard Generator, and Docker extensions. |
| **Free Open Source Tool** | A free, open-source performance testing tool. It requires no license or trial, making it cost-effective for newcomers in performance testing. |
| **Wide Range of Protocol Types** | JMeter supports various protocols like HTTP and HTTPS for web applications. It can simulate real-world scenarios using thread groups that users can configure themselves. |
| **Detailed Report Function** | JMeter provides multiple reporting options (e.g., Summary Report, Response Time Graph, Aggregate Report). Data can be saved in multiple formats such as `.jmx`, `.jtl`, and `.csv`. |

# 🧪 Test Environment & Configuration

** Test Environment**
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

# Methodology

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




