# Performance Testing Report: Web Application Load Analysis on Vercel Infrastructure Using Apache JMeter (WIP)

**Author:** Muhammad Syahir Rifqi bin Mohamad Nizam

**Student ID Number:** 2202539538 

**Date:** October 2025
## Introduction

In modern web development, ensuring that an application performs reliably under sustained traffic is critical—especially for production environments hosted on cloud platforms like Vercel. This is where **SOAK testing** becomes an essential part of the performance validation toolkit.

### What is a SOAK Test?

A **SOAK test** is a type of performance test that evaluates how a system behaves under a steady load over an extended period of time. Unlike stress or spike tests that focus on peak limits, SOAK tests aim to uncover:

- **Memory leaks**
- **Resource exhaustion**
- **Latency creep**
- **Backend degradation**
- **Cold start behavior**

By simulating real-world usage patterns over hours, SOAK tests help ensure that applications remain stable, responsive, and error-free during prolonged activity.

### Why SOAK Testing Matters

SOAK testing is especially important for:

- **Cloud-hosted apps** with dynamic scaling and edge deployments  
- **Serverless architectures** prone to cold starts and timeout thresholds  
- **User-facing platforms** where performance degradation impacts UX and retention  
- **CI/CD pipelines** that require pre-deployment validation under realistic conditions  

It provides empirical evidence of long-term reliability, helping developers and DevOps teams make informed decisions about scaling, caching, and infrastructure tuning.

---
