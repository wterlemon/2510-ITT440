<div align="center">

<div align="center">

# 🧪 Comprehensive Web Application Performance Testing & Analysis  
### Using **Apache JMeter**  

📘 *Individual Assignment — Performance Testing & Analysis*  

💻 **Name:**  
MOHAMAD NABIL IKHWAN BIN AMSIN

🆔 **Student ID:**  
2025394987  

🏫 **Class:**  
M3CDCS2554C  

📚 **Course:**  
ITT440 - Network Programming  

📅 **Submission Date:**  
WEEK 5

</div>

---

## 🎯 Objective  

To design, execute, and critically analyze a **performance test plan** for a web application using **Apache JMeter**, demonstrating skills in interpreting **key performance indicators (KPIs)** such as response time, throughput, and error rate.

---

## 🧰 Tool Selection & Justification  

### 🛠 Why Apache JMeter?

| Feature | Description |
|----------|--------------|
| 💸 **Free & Open Source** | No license cost, community supported |
| 🌐 **Protocol Support** | HTTP(S), JDBC, FTP, SMTP, and more |
| 🧩 **GUI + CLI Options** | Visual setup and script automation |
| 📊 **Built-in Reports** | Real-time graphs and aggregate summaries |
| ⚙️ **Integrations** | Compatible with Jenkins, GitHub Actions, etc. |

> 🧠 *Apache JMeter* is an ideal choice for both beginners and professionals in load and stress testing environments.

---

## 🌐 Target Web Application  

**Target URL:** `https://reqres.in` *(Sample API for testing purposes)*  

### 🧩 Hypothesis  

> “The web application can handle up to **50 concurrent users** with an average response time below **1.5 seconds**. Beyond this threshold, performance degradation and higher error rates are expected.”

---

## ⚙️ Environment Setup  

### 🧩 Prerequisites  

| Requirement | Version |
|--------------|----------|
| Java JDK | 8 or above |
| Apache JMeter | 5.6 or above |
| Internet Connection | Stable |
| OS | Windows / macOS / Linux |

### 🪜 Installation Steps  

```bash
# 1. Download Apache JMeter
https://jmeter.apache.org/download_jmeter.cgi

# 2. Extract and navigate to the 'bin' directory
cd apache-jmeter-*/bin

# 3. Launch JMeter
jmeter.bat     # Windows
./jmeter.sh    # macOS/Linux

# 4. Verify Java installation
java -version
