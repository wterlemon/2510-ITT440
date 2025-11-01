# 🧪 Comprehensive Web Application Performance Testing & Analysis  
**Tool:** Apache JMeter  
**Student Name:** MOHAMAD NABIL IKHWAN BIN AMSIN
**Course:** ITT440  
**Submission Date:** WEEK 4

---

## 🎯 Objective  
To design, execute, and critically analyze a **performance test plan** for a web application using **Apache JMeter**, demonstrating the ability to interpret key performance indicators (KPIs) and communicate technical findings effectively.

---

## 🧰 1. Tool Selection & Justification  
### 🛠 Why Apache JMeter?
Apache JMeter was selected for the following reasons:
- **Free & Open Source** – Widely adopted in academia and industry.  
- **Supports Multiple Protocols** – HTTP(S), FTP, JDBC, and more.  
- **GUI & CLI Support** – Easy for beginners, yet powerful for automation.  
- **Rich Reporting** – Built-in listeners for throughput, latency, and error visualization.  
- **Integration Ready** – Works well with CI/CD tools (e.g., Jenkins, GitHub Actions).

---

## 🌐 2. Target Web Application  
**Target:** `https://example.com`  
> *(Replace this with your approved public web application.)*  

### Hypothesis  
> Under increasing concurrent user load, the web application will maintain an average response time below **1.5 seconds** until **50 users**, after which server response time and error rate will increase significantly.

---

## ⚙️ 3. Environment Setup  

### 🧩 Prerequisites
- **Java JDK 8+**  
- **Apache JMeter 5.6+**  
- **Stable Internet Connection**

### 💻 Installation Steps
1. Download **Apache JMeter** from: [https://jmeter.apache.org/download_jmeter.cgi](https://jmeter.apache.org/download_jmeter.cgi)  
2. Extract the archive and navigate to the `bin` folder.  
3. Run JMeter:  
   ```bash
   jmeter.bat     # For Windows
   ./jmeter.sh    # For macOS/Linux

