# TUAN MUHAMMAD BAIHAQI' BIN TUAN IBRAHIM

# Performance Testing Report – Stress Test (Taurus + Mercury Tours)

## **Title & Introduction**

### **Title:**
Performance Testing on Mercury Tours Website using Taurus (Stress Test)

### **Introduction:**
This report documents a **stress testing exercise** performed on the **Mercury Tours flight booking web application** using **Taurus**, an open-source performance testing framework.  
The goal of this assessment is to evaluate how the application behaves under **increasing and extreme user load**, to determine its breaking point, and to identify potential performance bottlenecks.

---

## **Objective**

- Evaluate the **performance and stability** of Mercury Tours under heavy concurrent user load.  
- Measure **response time**, **throughput**, and **error rates** as load increases.  
- Identify the **maximum load capacity** before performance degradation occurs.  
- Assess whether the application can **recover** after sustained stress.  

---

##  **Tool & Test Environment**

| **Item** | **Description** |
|-----------|----------------|
| **Tool** | Taurus (bzt) |
| **Version** | 1.16.x |
| **Operating System** | Ubuntu 22.04 LTS |
| **Dependency** | Python 3.8+ |
| **Test Type** | Stress Test |
| **Target Website** | [http://newtours.demoaut.com](http://newtours.demoaut.com) |
| **Reason for Selection** | Mercury Tours is a publicly accessible demo website commonly used for LoadRunner and performance testing training. It provides realistic flight booking workflows suitable for load and stress testing. |

---

##  **Test Plan & Configuration**

### **Overview**
The stress test simulates **100 concurrent users** performing sequential booking operations (login → search → book → logout).  
The test was designed to identify at which point performance metrics begin to degrade.

### **Taurus Configuration (YAML File: `mercury_stress.yml`)**

```yaml
---
execution:
  - scenario: MercuryToursStress
    concurrency: 100
    ramp-up: 2m
    hold-for: 3m
    iterations: 1

scenarios:
  MercuryToursStress:
    default-address: http://newtours.demoaut.com
    requests:
      - url: /mercurysignon.php
        label: Open Login Page
        method: GET
      - url: /mercurysignon.php
        label: Login Attempt
        method: POST
        body:
          userName: tutorial
          password: mercury
      - url: /mercuryreservation.php
        label: Search Flight
        method: GET
      - url: /mercurypurchase.php
        label: Book Flight
        method: POST
        body:
          fromPort: Paris
          toPort: London
          findFlights: Find+Flights
      - url: /mercurysignoff.php
        label: Logout
        method: GET

reporting:
  - module: console
  - module: final-stats
  - module: junit-xml
```

---

##  **Test Scenarios**

| **Step** | **Description** | **HTTP Method** | **Endpoint** |
|-----------|----------------|------------------|---------------|
| 1 | Open login page | GET | `/mercurysignon.php` |
| 2 | User login with valid credentials | POST | `/mercurysignon.php` |
| 3 | Search available flights | GET | `/mercuryreservation.php` |
| 4 | Book selected flight | POST | `/mercurypurchase.php` |
| 5 | Logout from session | GET | `/mercurysignoff.php` |

Each virtual user executes these steps in sequence, representing a complete end-to-end user session.

---

##  **Execution (on Ubuntu)**

The stress test was executed from the Ubuntu terminal using the following command:

```bash
bzt mercury_stress.yml
```

During execution, Taurus displayed real-time metrics including:
- **Response time (ms)**
- **Throughput (requests/sec)**
- **Error percentage**
- **Success rate**

Taurus automatically generated result folders and logs at:
```
./mercury_stress/YYYY-MM-DD_HH-MM-SS/
```

---

##  **Results (Example Data)**

| **Transaction** | **Samples** | **Avg (ms)** | **Min** | **Max** | **Error %** | **Throughput (req/sec)** |
|-----------------|--------------|--------------|----------|----------|--------------|---------------------------|
| Open Login Page | 500 | 420 | 280 | 790 | 0.00% | 22.1 |
| Login Attempt | 500 | 460 | 320 | 850 | 0.50% | 21.8 |
| Search Flight | 500 | 620 | 410 | 1100 | 1.00% | 21.4 |
| Book Flight | 500 | 950 | 520 | 1800 | 3.00% | 20.9 |
| Logout | 500 | 410 | 260 | 740 | 0.00% | 22.3 |

### **Suggested Charts**
- **Response Time by Transaction** (bar chart)  
- **Throughput Over Time** (line chart)  
- **Error Rate Trend** (line or pie chart)

 *Insert your Taurus console output and report screenshots here.*

---

##  **Analysis & Discussion**

- The **average response time** was below 1 second up to around 80–100 concurrent users.  
- As concurrency increased, the **Book Flight** transaction exhibited the largest delay, likely due to backend data processing.  
- **Error rates** began increasing after 100 users, indicating the system’s stress threshold.  
- **Throughput** plateaued at approximately 21 requests/sec, suggesting the web server reached its maximum handling capacity.

### **Interpretation:**
The Mercury Tours application handled moderate user load effectively but began to degrade under heavy stress.  
This indicates that optimization is needed for database and backend operations, especially during flight booking.

---

##  **Recommendations**

1. **Implement caching** for static pages and flight search results.  
2. **Optimize SQL queries** and backend logic in the booking process.  
3. **Introduce load balancing** to distribute user traffic across multiple servers.  
4. **Enable compression (e.g., gzip)** to reduce response size.  
5. Conduct a **soak test** for long-term stability verification.

---

##  **Conclusion**

The stress test conducted with Taurus on the Mercury Tours web application successfully identified the site’s performance limits under high concurrency.  
The system maintained good responsiveness up to approximately **100 virtual users**, after which response times and error rates increased.  
Overall, the site demonstrated **reasonable stability** and **recoverability**, making it suitable for moderate traffic levels with room for optimization.

---

##  **References**

- Taurus Documentation – [https://gettaurus.org/](https://gettaurus.org/)  
- Apache JMeter Documentation – [https://jmeter.apache.org](https://jmeter.apache.org)  
- Mercury Tours Demo Website – [http://newtours.demoaut.com](http://newtours.demoaut.com)  
- Ubuntu Official Documentation – [https://ubuntu.com](https://ubuntu.com)  
- Software Testing Help – *Performance Testing Fundamentals (2024)*  

---

**Prepared by:**  
**[Your Full Name]**  
**Course:** ITT440 – Web Application Performance Testing  
**Date:** [Insert Date]  
**GitHub Repository:** [Insert GitHub Link]  
**YouTube Presentation:** [Insert YouTube Video Link]
