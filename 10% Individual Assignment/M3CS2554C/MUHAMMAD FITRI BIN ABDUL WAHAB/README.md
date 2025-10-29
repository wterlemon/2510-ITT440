# 🧪 ITT440 - Web Application Performance Testing & Analysis  
## Title: Load Testing of FakeStoreAPI Using K6  

### 👤 Author  
**Name:** MUHAMMAD FITRI BIN ABDUL WAHAB  
**Student ID:** 2025172963
**Course:** ITT440 – Web Application Performance Testing  
**Institution:** UiTM Kampus Jasin 

---

## 🎯 1. Objective  

The purpose of this project is to perform a **Load Test** on a public web application using **K6**, a modern and developer-friendly load testing tool.  
The target system is [FakeStoreAPI](https://fakestoreapi.com/), an open REST API that simulates an online store.  

This test aims to evaluate:
- Response time under concurrent requests  
- System throughput (requests per second)  
- Error rate and performance stability  

---

## ⚙️ 2. Tool Selection Justification  

### 🔸 Why Grafana K6?  
Grafana K6 was selected due to its simplicity, lightweight setup, and developer-friendly scripting language (JavaScript).  
Compared to other tools, K6 offers:
- Easier scripting and execution from the command line  
- Faster performance with minimal resource usage  
- Built-in metrics summary and Grafana integration for visualization  

---

## 🌐 3. Target Web Application  

**Application:** [FakeStoreAPI](https://fakestoreapi.com/)  
**Description:** A free online API for testing and prototyping e-commerce applications.  
**Sample Endpoint Used:**  
`https://fakestoreapi.com/products`

---

## 🧰 4. Test Environment Setup  

| Component | Description |
|------------|-------------|
| **Operating System** | Windows 11 |
| **Tool** | K6 v0.52.0 |
| **Connection** | Broadband Internet |
| **Target URL** | `https://fakestoreapi.com/products` |

### 🔧 Installation Steps
1. Download and install K6  
   - **Windows (Chocolatey):**  
     ```bash
     choco install k6
     ```
   - **Linux (Debian/Ubuntu):**  
     ```bash
     sudo apt install k6
     ```
2. Verify installation  
   ```bash
   k6 version
