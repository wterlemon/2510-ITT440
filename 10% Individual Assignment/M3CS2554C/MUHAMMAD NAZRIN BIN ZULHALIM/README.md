# :tiger: Performance Analysis of ‘https://demo.nopcommerce.com’ using Grafana k6

### 👨‍💻 Name: Muhammad Nazrin bin Zulhalim
### 🎓 Student ID: 2025157375
### 🧾 Course: ITT440 – Individual Assignment  
### 🧠 Group: M3CS2554C

---
## :building_construction: Project Objective
## The objective of this is to analyse how ‘https://demo.nopcommerce.com’ will behave under soak testing using Grafana k6. k6 is used to simulate continuous real life traffic loads and identify performance degradation, memory and resource leaks and stability issues. The result of the test will be the indicators(KPIs) of the key performance and application endurance.

---
## :dart: Target Application
## The application selected for this analysis is 'https://demo.nopcommerce.com', a publicly accessible demo e-commerce platform. This application was chosen because e-commerce needs to be able to handle continuous traffic and complex user flows.

---
## 🛠️ Test Environment
| Component | Details |
|------------|----------|
| **Test Machine** | HP Probook 440 G8 |
| **CPU** | 11th Gen Intel(R) Core(TM) i7-1165G7 |
| **RAM** | 16GB DDR4 |
| **Tool** | Grafana k6 v1.3.0 |
| **Target Application URL** | ‘https://demo.nopcommerce.com’ |

---
## :microscope: Test Methodology: Simulating Realistic Behaviour
### To ensure the testing is valid, a realistic user scenario was created. The test simulates a user browsing the site, searching for a product and viewing certain product's page, with random pause between each steps.

---
## :train: Soak Test: Configuration and Execution
###  The k6 'options' were configured to simulate a sustained, moderate load over a certain period of time such for 35 minutes. The test ramps up to 50 Virtual Users over 5 minutes then continues to rises up to 200 Virtual Users and then 300 Virtual Users and will be hold at that for the duration of the test.
