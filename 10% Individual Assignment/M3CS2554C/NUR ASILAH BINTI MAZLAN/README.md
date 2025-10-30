# Stress Testing on QuickPizza Using Grafana K6

## Abstract

## Introduction
Performance of web applications is fundamentally important to user’s pleasure and operational reliability. As applications scale, they need to be able to withstand increased traffic without sacrificing responsiveness or stability. Stress testing is one type of non-functional testing that observes how an application performs under extreme conditions. For example, the load will be gradually increased until the system is near or has exceeded its expected limits.

For purposes of the experiment, the QuickPizza demo website was chosen as the target system. The demo site provided static and dynamic content such as menu listings, news pages, and login forms. Thus, it was fitting for replicating realistic browsing and transaction activity. Grafana Cloud K6 is an open-source, cloud-based performance testing platform which was used to assess the website’s reaction as the number of simulated users increased. 
