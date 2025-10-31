# Comprehensive Web Application Performance Testing & Analysis
---

### STUDENT NAME : NUR ARIF ASYRAF BIN ZAHARI
### ITT440 - INDIVIDUAL ASSIGNMENT
### GROUP : M3CS2554B
---

# 🔍 Stress Testing on DummyJSON using Artillery
---

## Introduction

The assignment demands Artillery execution of a stress test on DummyJSON API to evaluate its operational stability when facing high traffic volumes. The test evaluates API performance under heavy traffic conditions to detect rate limit violations that result in HTTP 429 errors and assesses its recovery time after traffic decreases. The test evaluates API scalability through performance metrics which include response time and data processing capacity and error frequency during warm-up, high load and recovery phases.

---

## Objectives

- To evaluate the performance and stability of the DummyJSON API under different load conditions.
- To observe how the API responds during warm-up, sustained high load, and recovery phases.
- To identify potential performance bottlenecks or timeout issues under heavy traffic.
- To measure response times, throughput, and error rates for performance analysis.

---

## Tool & Test Selection Justification
<p align="center">
<img width="500" height="243" alt="1_p4IQfjORMIMZtN8SJRjzcA" src="https://github.com/user-attachments/assets/9bcc62c7-bf15-4428-a6d8-d43b25c77ad2" />    
<img width="500" height="497" alt="image" src="https://github.com/user-attachments/assets/51d8c870-99b9-4708-ba60-9dffb25ca339" />

## Performance Testing Tool (Artillery)

The experiment used Artillery because this open-source tool enables simple testing framework designed for HTTP, WebSocket, and API-level testing. Stress testing through YAML script execution. The tool delivers precise measurements of response times and errors while Built-in Cloud dashboard for reporting which is Artillery Cloud generates visual performance graphs for better analysis.

## Target Web Application (DummyJson)

The experiment used DummyJSON because it offers a free stable fake REST API that performs well for performance testing. The API generates realistic data about products and users which enables Artillery to perform simulations of actual API operations. The API generates stable responses which make it perfect for studying system performance and stability during high-stress situations.

---

## Environment Setup
| **Component**          | **Details**                                                                        |
| ---------------------- | ---------------------------------------------------------------------------------- |
| **Environment**        | Windows 11 operating system                                                        |
| **Testing Framework**  | Artillery v2.0.26                                                                   |
| **Configuration File** | `stress_test.yml`                                                                  |
| **Execution Method**   | `artillery run stress_test.yml --record --key a9_x5xh12axy495k0pmfhng64nkpf3u2kti` |
| **Target Endpoint**    | [DummyJSON API](https://dummyjson.com) – REST API for fake data testing            |
| **Test Category**      | Stress Test                                                                        |
| **Test Duration**      | 3 minutes, 13 seconds                                                               |
| **Load Pattern**       | Warm-up → Sustained High Load → Recovery                                           |
| **Reporting Platform** | Artillery Cloud Dashboard                                                          |

