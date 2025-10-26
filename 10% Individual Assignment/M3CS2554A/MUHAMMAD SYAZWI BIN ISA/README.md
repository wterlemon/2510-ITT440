# 🚀 Web Application Performance Testing

**Course:** 2510-ITT440  
**Assessment:** 1 (10%)  
**Author:** [Your Name]  
**Video Demo:** [Link to your YouTube Video Here]

---

## 🛠️ Tool of Choice: `k6` by Grafana Labs

I have selected **`k6`** as my performance testing tool.

*   **Why k6?** k6 is a modern, developer-centric, and open-source load testing tool built for making performance testing a productive and enjoyable experience. It uses JavaScript for test scripting, making it accessible and powerful.
*   **Key Features:**
    *   CLI-based with a simple and clean API.
    *   Scripting in JS (ES6+ supported).
    *   Built-in metrics for performance analysis.
    *   Designed for automation and CI/CD integration.

---

## 🧪 Application Under Test (AUT)

I tested the public demo of **Sauce Demo**, a sample e-commerce website.

*   **Application URL:** [https://www.saucedemo.com/](https://www.saucedemo.com/)
*   **Reason for Choice:** It provides a realistic user flow (login, product browsing, cart management) without requiring any setup, making it an ideal candidate for consistent and repeatable performance tests.

---

## ⚡ Performance Test Executed: Spike Test

The type of performance test I conducted is a **Spike Test**.

*   **Objective:** To determine how the application behaves under a sudden and massive increase in load, simulating a scenario like a "flash sale" or a mention by a popular influencer.
*   **What it measures:** The system's ability to handle abrupt traffic surges and its recovery process once the surge subsides.

---

## 🎬 Video Demonstration

A full screen capture of the test planning, execution, and result analysis is available on YouTube.

[![Watch the video](https://img.youtube.com/vi/YOUR_VIDEO_ID_HERE/0.jpg)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID_HERE)

*(Click the image above to watch the video)*

---

## 📝 Test Plan & Script

### Scenario: User Login Spike
Simulate a scenario where 300 virtual users simultaneously attempt to log into the Sauce Demo application over a very short period (15 seconds).

### k6 Test Script (`spike_test.js`)

```javascript
import http from 'k6/http';
import { check, sleep } from 'k6';

// Define test configuration
export const options = {
  stages: [
    { duration: '5s', target: 10 },  // Ramp-up to 10 users quickly
    { duration: '15s', target: 300 }, // SPIKE: Rapidly ramp-up to 300 users
    { duration: '5s', target: 0 },    // Ramp-down to 0 users
  ],
};

export default function () {
  // Step 1: Navigate to the login page (GET request)
  let res = http.get('https://www.saucedemo.com/');

  // Check if the page loaded successfully
  check(res, {
    'is status 200': (r) => r.status === 200,
    'body contains login form': (r) => r.body.includes('login-button'),
  });

  // Step 2: Submit login credentials (POST request)
  const loginPayload = {
    'user-name': 'standard_user',
    'password': 'secret_sauce',
  };

  res = res.submitForm({
    formSelector: 'form',
    fields: loginPayload,
  });

  // Check if login was successful by looking for the products page
  check(res, {
    'login successful': (r) => r.status === 200 && r.url.includes('inventory.html'),
  });

  // A short think time to simulate a user reading the page
  sleep(1);
}  
