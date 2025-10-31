# 🔥Can It Handle the Heat? A Load Test Article by Ainul's Network Programming 101 ✨

## 🎯 Executive Summary: Gatling Load Test Baseline

This document summarizes the core purpose, findings, and recommendations from the primary load test documented in the README, conducted as part of Ainul's Network Programming 101.

<p align="center">
  <a href="https://gatling.io/" target="_blank">
    <img src="https://cdn.prod.website-files.com/685a8fe4ddca049f26333871/68b5961b1a99f68c22d5cf56_Open%20graph%20Gatling%20image.svg" alt="Gatling Logo Link" width="300">
  </a>
</p>

## 🛠️ Why Gatling, huh? (Tool selection justification)

I picked Gatling as my load testing tool because its modern design makes the entire performance check-up process—from generating traffic to analyzing results—more efficient and reliable.

Gatling uses a smart, **asynchronous architecture** which means it can handle **huge traffic** and simulate thousands of users using very little computer power. This allows me to run bigger, more realistic tests to find the application's true breaking limits.

The test scenarios are written as clean, **simple, and readable code** (a DSL), making them easy to update when the application changes, which also helps the team collaborate better. 

After every test, Gatling automatically generates **amazing, detailed HTML reports**. These reports give me instant insight into the results with graphs that clearly pinpoint the exact slow spots (bottlenecks) in the application. 

Finally, Gatling **fits right into my automated development process (CI/CD)**, ensuring I catch performance problems early and continuously before it ever become a serious issue.
  
---
## 🖥️ You are now at the test run prep! (Test environment setup)
| Category | Component/Software | Purpose in Environment |
| :--- | :--- | :--- |
| **Target Website** | **AUT Base URL** | `https://the-internet.herokuapp.com` |
| **Runtime Environment** | **Java Runtime Environment** | Executes the simulation written in Java. |
| **Load Testing Tool** | **Gatling Open Source** | Core engine for execution and reporting. |
| **Execution Method** | **Terminal / Command Line** | Used to execute the Gatling script via the provided **`gatling.sh`** or **`gatling.bat`** runner files. |
| **Simulation Script** | **Class Name** | `CleanSimulation.java` |
| **Injection Profile** | **Load Strategy** | `rampUsers(10).during(60)` (Injecting **10 users** over **60 seconds**). |
| **Reporting/Analysis** | **Gatling HTML Reports** | The output format used to view and analyze performance metrics. |

---
## 📜 Next Station, My Testing Handbook! (Methodology)

firstly we will go to **PHASE 1** where I initializing my pre - framework in my computer terminal

1.  **Write Java Code**

The coding below is my java coding that Gatling had used to make a Stimulation Load test at `https://the-internet.herokuapp.com`
```java
package example;

import static io.gatling.javaapi.core.CoreDsl.*;
import static io.gatling.javaapi.http.HttpDsl.*;

import io.gatling.javaapi.core.*;
import io.gatling.javaapi.http.*;

public class CleanSimulation extends Simulation {

  private static final HttpProtocolBuilder httpProtocol = http
      .baseUrl("https://the-internet.herokuapp.com")
      .acceptHeader("text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8");

  private static final ScenarioBuilder scn = scenario("Heroku App Login Workflow FINAL FIX")
      
      // Step 1: GET the Login Page
      .exec(
          http("T01_GET_Login_Page")
              .get("/login")
              .check(status().is(200))
      )
      .pause(1) 
      
      // Step 2: POST the login form data, which includes the automatic redirect to /secure
      .exec(
          http("T02_POST_Login_and_Access_Secure")
              .post("/authenticate")
              .formParam("username", "tomsmith") 
              .formParam("password", "SuperSecretPassword!")
              
              // Check the final state after the redirect (the secured page)
              .check(status().is(200)) 
              // Verification: Check for a unique element on the secured page
              .check(css("h4").is("Welcome to the Secure Area. When you are done click logout below."))
      )
      
      .pause(2) 
      
      .exec(session -> {
          System.out.println("Login Sequence Complete!");
          return session;
      });


  // 3. Injection Profile: 10 users over 60 seconds
  {
    setUp(
      scn.injectOpen(
        // Inject 10 users gradually over 60 seconds for stable, sustained metrics
        rampUsers(10).during(60) 
      )
    )
    .protocols(httpProtocol)
    // 4. Assertion: Expecting success
    .assertions(
        global().failedRequests().percent().lte(1.0)
    );
  }
}
```
2.  **Launch Gatling**

From my Computer terminal or command prompt, I had navigated to my project root
`cd "C:\Users\Ainul Mardhiah\Gatling Open Source"` 

After that, I had run and execute my specific command, which is `.\mvnw.cmd gatling:test`.

And then at my gatling prompt, I type the number 1 because it's corresponds to `example.CleanSimulation` and press Enter.

secondly, we wiil go and see the official load run test at **PHASE 2**.

5.  **Run Official Load:** Execute the full **10 users over 60 seconds** load.
6.  **Monitor Safety:** Actively monitor your machine's resources and **STOP IMMEDIATELY** if the public application shows stress.

### Phase 3: Analysis & Conclusion (The Verdict)

7.  **Validate Success:** Check the HTML report failure rate against the **$\le 1.0\%$ assertion**.
8.  **Analyze $p95$:** Determine the overall response time quality by reviewing the **$95^{th}$ Percentile ($p95$)** for the critical request: `"T02_POST_Login_and_Access_Secure"`.
9.  **Pinpoint Bottleneck:** Compare the timings between **T01** (page load) and **T02** (login processing) to identify the slowest step.
10. **Final Report:** Document the results, stating whether the test **Passed or Failed** the established goal.

---

## ○ Raw data presentation (e.g., charts/graphs).

## ○ Interpretation of results.

## ○ Identified bottlenecks.

## ○ Recommendations for improvement.

## ○ Final conclusions.


---

