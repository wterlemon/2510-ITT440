# OWASP Juice Shop Stress Testing with Locust

![Locust Logo](https://locust.io/static/img/logo.png)
![OWASP Juice Shop](https://raw.githubusercontent.com/juice-shop/juice-shop/master/frontend/src/assets/public/images/JuiceShop_Logo.png)

## 📊 Assignment Overview
- **Course**: ITT440 - Network Programming
- **Assessment**: 10% Individual Assignment 1
- **Tool**: Locust (Python-based load testing tool)
- **Target**: OWASP Juice Shop Web Application
- **Test Type**: Stress Testing

## 🎯 Objectives
- Learn web application performance testing
- Implement stress testing using Locust
- Analyze application behavior under heavy load
- Identify performance bottlenecks

## 🛠️ Tools & Technologies
- **Load Testing Tool**: Locust.io
- **Target Application**: OWASP Juice Shop
- **Programming Language**: Python
- **Metrics Collected**: Response times, RPS, failure rates

## 📈 Test Scenario

### User Behavior Simulation
1. **Homepage Browsing** (30% probability)
2. **Product Search** (20% probability) 
3. **Product Details View** (10% probability)
4. **About Page** (10% probability)

### Load Configuration
- **Maximum Users**: 100
- **Spawn Rate**: 10 users/second
- **Test Duration**: 5 minutes
- **Testing Environment**: Production (Heroku)

## 🚀 Installation & Setup

```bash
# Clone this repository
git clone https://github.com/yourusername/juice-shop-stress-test.git

# Navigate to project directory
cd juice-shop-stress-test

# Install dependencies
pip install -r requirements.txt
