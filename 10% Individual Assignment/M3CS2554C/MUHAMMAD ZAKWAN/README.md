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
<br>

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
| **Target Website** | [JSONPlaceholder](https://jsonplaceholder.typicode.com/) |

**Configuration:**
| Parameter                     | Value                                      |
|------------------------------|--------------------------------------------|
| Number of Users              | 180 Users                                  |
| User Percentages  | 5% (Before Spike)                                  |
|    | 90% (During Spike)                                 |
|     | 5% (After Spike)                                    |
| Loop Count                   | 10 Times (Each user sends 10 requests)     |
| Ramp-Up Period               | 1 Second (All users start at the same time)       |
 

# 🔐 KEY FEATURES OF JMETER (Related to Spike Testing)

- 🚀 **Custom Thread Groups** (set amount of users)  
  can simulate sudden traffic spikes using custom thread groups like Ultimate Thread Group.

- ⏱️ **Sync Timer** (use ramp-up)  
  allow all virtual users hit the server at the same time — perfect for spike testing.


- 📊 **Real-Time Performance Metrics** (results analyzation)  
  have built-in listeners to monitor response time, error rate, and system behavior during the spike.

<br>
<br>

# 📂 RAW DATA PRESENTATION
|              Amount of users                  |          Before spike throughput (5% of 180 users)             |
|--------------------------------|-----------------------------|
|<img width="402" height="244" alt="image" src="https://github.com/user-attachments/assets/9d505f0e-a995-447b-8498-fde485ac84ed" /> | <img width="402" height="240" alt="image" src="https://github.com/user-attachments/assets/6ba0f47b-9a6a-4a77-8145-4516a7cc71a5" /> |

| **During spike throughput (90% of 180 users)**   |  **After spike throughput (5% of 180 users)**   |
|-------------------------------|---------------------------------|
| <img width="402" height="245" alt="image" src="https://github.com/user-attachments/assets/6b401e7d-09f1-421e-8a44-7ccc19f222f7" /> | <img width="402" height="245" alt="image" src="https://github.com/user-attachments/assets/10104827-a3d7-495a-87b9-97bfc1d5c234" /> |

| **Summary report**   |  **Aggregate report**   |
|-------------------------------|---------------------------------|
| <img width="402" height="241" alt="image" src="https://github.com/user-attachments/assets/9c8c7cfc-7b6c-4e07-a589-cb18ba04ef49" /> | <img width="404" height="229" alt="image" src="https://github.com/user-attachments/assets/07e64cdb-0095-476a-90f5-92c79e9ec583" /> |

| **Response time graph <br> (◼️Before spike, 🟥During spike, 🟩After spike)**   |  **Status results in table**   |
|-------------------------------|---------------------------------|
| <img width="402" height="245" alt="image" src="https://github.com/user-attachments/assets/58625624-3954-44c1-ae70-ad3051dad0f2" /> | <img width="402" height="250" alt="image" src="https://github.com/user-attachments/assets/40a0aa11-6538-406a-9330-b460f3e59890" />|


# 📊INTERPRETATION OF RESULT & IDENTIFIED BOTTLENECKS
ASDFG

# 🆕RECOMMENDATION FOR IMPROVEMENT
TYUI

# 🗒️ CONCLUSION
LALALA
I


