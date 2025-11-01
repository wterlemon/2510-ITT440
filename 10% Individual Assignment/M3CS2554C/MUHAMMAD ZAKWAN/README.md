<h1 align="center"># WEB PERFORMANCE TESTING</h1>
<img width="1024" height="149" alt="JSONPLACEHOLDER" src="https://github.com/user-attachments/assets/f42984a7-add7-40bd-8c8b-166d9220fc0d" />
Belum siap lagi <br>
<br>

## 🧑‍🎓 Student Information 

| Field       | Details             | 
|-------------|---------------------|
| 👤 **NAME**    | MUHAMMAD ZAKWAN 'IRFAN BIN MOHD ZAMRY   | 
| 🆔 **STUDENT ID** | 2025127509    |
| 📘 **TITLE**     | SPIKE TESTING ON JSONPLACEHOLDER WEB |

##

# 💡 INTRODUCTION TO WEB PERFORMANCE TESTING

| 🧪 **Spike Testing** | 🔗 **Do You Know JSONPlaceholder?** |
|----------------------|--------------------------------------|
| Spike testing is a type of performance testing that evaluates how a website or application handles sudden, extreme surges in traffic or load like flash sales, viral posts, or ticket releases. It helps ensure your system remains stable and responsive under pressure. | JSONPlaceholder is a free online REST API service that provides fake data for testing and prototyping web applications. It's widely used by developers to simulate backend responses without needing a real server perfect for learning, demos, and mockups. |
<br>

**What we want to know from this test ?**  💡
<br>
- How JSONPlaceholder website handle suddent high users at one time, and how it recover from that.

# 🧰 TOOL SELECTION
- Apache JMeter <br>
<img width="349" height="104" alt="image" src="https://github.com/user-attachments/assets/564c25c4-bad6-4d3f-b6a4-ce40440f31eb" />
 <br>
I'm using this powerful open-source tool to perform spike testing by simulating sudden surges in user traffic. JMeter allows me to configure thread groups that rapidly increase load, helping me observe how the system responds under pressure. <br>
<br>

- UBuntu Linux <br>
<img width="297" height="134" alt="image" src="https://github.com/user-attachments/assets/19746cc7-2c56-4f8b-b5f0-3e80789f76ca" />
 <br>
I'm using Ubuntu Linux as the operating system to host and execute my performance tests. Its stability, security, and lightweight footprint make it ideal for server-side testing environments. <br>
<br>

# 💻 TEST ENVIRONMENT SETUP & METHODOLOGY 

**Setup:**
| Component | Description |
|------------|-------------|
| **Platform** | Ubuntu 22.04 LTS (Linux-based) |
| **Tool** | JMeter |
| **Target Website** | JSONPlaceholder |

**Configuration:**
| Parameter                     | Value                                      |
|------------------------------|--------------------------------------------|
| Number of Users              | 180 Users                                  |
| User Percentages Before Spike     | 5%                                         |
| User Percentages During Spike     | 90%                                        |
| User Percentages After Spike      | 5%                                         |
| Loop Count                   | 10 Times (Each user sends 10 requests)     |
| Ramp-Up Period               | 1 Second (All users start instantly)       |
 

# 🔐 KEY FEATURES OF JMETER (Related to Spike Testing)

- 🚀 **Custom Thread Groups**  
  can simulate sudden traffic spikes using custom thread groups like Ultimate Thread Group.

- ⏱️ **Sync Timer**  
  allow all virtual users hit the server at the same time — perfect for spike testing.


- 📊 **Real-Time Performance Metrics**  
  have built-in listeners to monitor response time, error rate, and system behavior during the spike.

<br>
<br>

# 📂 RAW DATA PRESENTATION
<img width="421" height="236" alt="image" src="https://github.com/user-attachments/assets/1c1a146e-04a6-40e5-ba11-070d9a6f7309" /> <img width="421" height="239" alt="image" src="https://github.com/user-attachments/assets/358db2a3-8780-45b9-bd14-85947d5dff11" />





# 📊INTERPRETATION OF RESULT & IDENTIFIED BOTTLENECKS
ASDFG

# 🆕RECOMMENDATION FOR IMPROVEMENT
TYUI

# 🗒️ CONCLUSION
LALALA
I


