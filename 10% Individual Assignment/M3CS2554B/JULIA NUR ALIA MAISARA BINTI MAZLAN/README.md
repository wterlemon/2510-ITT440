# JULIA NUR ALIA MAISARA BINTI MAZLAN
# 🧩 ITT440 – Web Application Load Testing using Locust

### **Tool:** Locust (Python-based Load Testing Framework)  
### **Target Site:** [BooksToScrape](https://books.toscrape.com)  
### **Date:** October 2025  

---

## 🏷️ Title & Introduction

### **Title:**  
**Web Application Load Performance Testing of BooksToScrape Using Locust**

### **Introduction:**  
Performance testing plays an essential role in determining how well a web application responds under concurrent user activity. This project applies **Locust**, an open-source Python-based tool, to simulate multiple users accessing the **BooksToScrape** website simultaneously.  

By observing how the site reacts to controlled network traffic, this project explores core networking programming concepts such as request handling, latency, and throughput. The activity is designed for **ITT440 (Networking Programming)** to develop skills in analyzing how web applications perform under varying load conditions.

---

## 🎯 Objective

1. To configure and execute a load test using Locust.  
2. To simulate multiple user connections to the BooksToScrape web application.  
3. To monitor response times, request rates, and overall performance stability.  
4. To relate load testing outcomes to networking programming concepts such as latency, concurrency, and data throughput.

---

## ⚙️ Tool & Target Site Selection

### **Tool: Locust**  
Locust is a **Python-based, open-source load testing tool** that allows testers to simulate user traffic and measure system performance under different network loads. It provides a web-based interface for configuring, executing, and monitoring real-time results.

Key features include:
- Written in Python with simple user behavior scripting.  
- Real-time results with response time and throughput metrics.  
- Scalable testing for small or large user simulations.  

### **Target Website: BooksToScrape**  
[BooksToScrape](https://books.toscrape.com) is a public demo e-commerce site used for automation and testing purposes. It is a safe and legal platform for practicing web performance testing as it mimics a real-world online bookstore with multiple categories and pages.

---

## 🧠 Test Plan & Configuration

**Test Environment:**
- **Operating System:** Windows 10  
- **Python Version:** 3.13  
- **Locust Version:** 2.42.0  
- **Network Connection:** Stable Wi-Fi  
- **Browser for Dashboard:** Google Chrome  

**Test Script File:** `bookstore_performance_test.py`

```python
# Bookstore Load Performance Testing Script
# Author: Julia Nur Alia Maisara Mazlan
# Subject: ITT440 - Networking Programming

from locust import HttpUser, task, between

class BookStoreClient(HttpUser):
    wait_time = between(2, 5)

    @task(4)
    def open_homepage(self):
        self.client.get("/")

    @task(2)
    def explore_category(self):
        self.client.get("/catalogue/category/books/travel_2/index.html")

    @task(2)
    def open_book_info(self):
        self.client.get("/catalogue/a-light-in-the-attic_1000/index.html")

    @task(1)
    def navigate_next_page(self):
        self.client.get("/catalogue/page-2.html")

    @task(1)
    def quick_search(self):
        self.client.get("/catalogue/category/books_1/index.html")

