<h1 align="center"># WEB PERFORMANCE TESTING</h1>
<img width="1024" height="293" alt="LOAD-TESTING-ON-JSONPLACEHOLD-03-11-2025" src="https://github.com/user-attachments/assets/d112f20d-b2bf-4df2-9774-605e2d33270c" />
<br>
## 🧑‍🎓 Student Information 

| Field       | Details             | 
|-------------|---------------------|
| 👤 **NAME**    | MUHAMMAD ZAKWAN 'IRFAN BIN MOHD ZAMRY   | 
| 🆔 **STUDENT ID** | 2025127509    |
| 📘 **TITLE**     | LOAD TESTING ON JSONPLACEHOLDER WEB |

##

# 💡 INTRODUCTION TO WEB PERFORMANCE TESTING

| 🧪 **Load Testing** | 🔗 **Do You Know JSONPlaceholder?** |
|----------------------|--------------------------------------|
| Load testing happens when you simulate many users using your website or app at the same time. It’s like giving your system a workout to see how strong and fast it is under pressure. | JSONPlaceholder is a free online REST API service that provides fake data for testing and prototyping web applications. It's widely used by developers to simulate backend responses without needing a real server perfect for learning, demos, and mockups. |
<br>

**What we want to know from this test ?**  💡
<br>
- We want to know if the system stays fast, stable, and error-free when many users use it at once.
<br>

# 🧰 TOOL SELECTION
- Apache JMeter <br>
<img width="349" height="104" alt="image" src="https://github.com/user-attachments/assets/564c25c4-bad6-4d3f-b6a4-ce40440f31eb" />
 <br>
I'm using this powerful open-source tool to perform load testing by simulating continuous heavy load in user traffic. JMeter helping me observe how the system responds under pressure. <br>
<br>

- UBuntu Linux <br>
<img width="449" height="334" alt="image" src="https://github.com/user-attachments/assets/7e6baef3-52e8-49fb-8331-cc9f0ef4ebe9" />

 <br>
I'm using Ubuntu Linux as the operating system to host and execute my performance tests. Its stability, security, and lightweight footprint make it ideal for server-side testing environments. <br>
<br>

# 💻 TEST ENVIRONMENT SETUP & METHODOLOGY 

**Setup:**
| Component | Description |
|------------|-------------|
| **Platform** | Ubuntu 24.04.2 LTS (Linux-based) |
| **Hardware model** | intel Core i5 |
| **Tool** | JMeter |
| **Target Website** | [JSONPlaceholder](https://jsonplaceholder.typicode.com/) |

**Configuration:**
| Parameter                     | Value                                      |
|------------------------------|--------------------------------------------|
| Number of Users              | 200 Users (normal), 1000 Users (Heavy load)              |
| Loop Count                   | 5 Times (Each user sends 5 requests)     |
| Ramp-Up Period               | 60 Second (All users use the system in one period)       |
 

# 🔐 KEY FEATURES OF JMETER (Related to Spike Testing)

- 🚀 **Custom Thread Groups** (set amount of users)  
  can simulate heavy traffic loads using custom thread groups.

- ⏱️ **Sync Timer** (use ramp-up)  
  allow all virtual users hit the server in period of times — perfect for load testing.


- 📊 **Real-Time Performance Metrics** (results analyzation)  
  have built-in listeners to monitor response time, error rate, and system behavior during the load.

<br>
<br>

# 📂 RAW DATA PRESENTATION
|              Normal load of users                  |          Heavy load of users          |
|--------------------------------|-----------------------------|
|<img width="414" height="254" alt="image" src="https://github.com/user-attachments/assets/0f99e64d-46cb-4961-8ad6-e16831880073" /> | <img width="414" height="254" alt="image" src="https://github.com/user-attachments/assets/04e10d06-5eff-405f-bab3-3c3e3e2f9646" />|

| HTTP request   |  **After spike throughput (5% of 180 users)**   |
|-------------------------------|---------------------------------|
| <img width="414" height="254" alt="image" src="https://github.com/user-attachments/assets/fcf22ab5-d921-4a88-88ca-8796ba9174ce" />| <img width="402" height="245" alt="image" src="https://github.com/user-attachments/assets/10104827-a3d7-495a-87b9-97bfc1d5c234" /> |

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


