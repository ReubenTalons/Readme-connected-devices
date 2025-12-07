# IoT Project Proposal: Intelligent HVAC Control System with Adaptive Thresholds



Student: Reuben

Course: INFO7374 - Programming the Internet of Things

Institution: Northeastern University

Date: December 6, 2025



## 1\. WHAT – Problem Statement

Traditional HVAC control systems use fixed temperature thresholds, causing frequent on/off cycling when temperatures hover near threshold values. This "actuator chatter" wastes energy (30-40% inefficiency), increases equipment wear, and provides poor comfort. Current IoT monitoring systems also lack secure communication, exposing building systems to cyber attacks.

The Problem: We need an intelligent IoT system that combines immediate reactive control with adaptive threshold management, while ensuring all communication is encrypted and secure. The system must use both MQTT and CoAP protocols efficiently to demonstrate protocol selection strategies for different use cases.



## 2\. WHY – Purpose

##### Why I Care:

As a cybersecurity professional and Graduate Teaching Assistant for Cybersecure Audit \& Compliance at Northeastern University, I've seen how IoT systems are both powerful and vulnerable. This project lets me combine my security expertise with IoT programming to build a system that is both intelligent and secure—demonstrating best practices that are often missing in real-world deployments.



##### Why You Should Care:



* Energy Savings: Adaptive threshold management reduces HVAC energy consumption by 30-40%



* Security Critical: IoT attacks increased 300% in 2024; this demonstrates proper TLS encryption and certificate management



* Real-World Application: This architecture applies to smart buildings, hospitals, data centers, greenhouses—anywhere environmental monitoring is critical



* Scalability: Distributed edge intelligence reduces cloud costs and enables offline operation





### 3\. HOW – System Diagram and Approach

#### System Architecture







..........................................

.........................................



#### Technology Stack


<img width="1720" height="955" alt="Tech Stack" src="https://github.com/user-attachments/assets/58eaf5f0-5f76-42b2-b814-5b136d0608b8" />










## How It Works



##### Step 1: Sensor Monitoring (CDA)



* Read temperature every 5 seconds



* Compare against thresholds (Floor: 20°C, Ceiling: 24°C)



* If violated, trigger appropriate actuator



#### Step 2: Communication



* CDA publishes sensor data via MQTT QoS 1 (reliable delivery)



* CDA subscribes to actuator commands via MQTT QoS 2 (guaranteed delivery)



* Alternative: Use CoAP for lightweight communication



#### Step 3: Trend Analysis (GDA)



* GDA subscribes to all sensor messages



* Tracks threshold crossings over time



* If >5 crossings in 10 minutes → trigger adaptive response





#### Step 4: Adaptive Control



* GDA calculates optimal threshold adjustment



* Sends UPDATE\_THRESHOLD command to CDA



* CDA applies new thresholds



* System stabilizes with fewer false triggers



#### Step 5: Security



* All MQTT communication encrypted with TLS 1.2



* Certificates validated on each connection



* Wireshark shows encrypted packets (unreadable without cert)





## 4\. RESULTS – Expected Outcomes

## What We Will Demonstrate



#### 1\. Real-Time Intelligent Control



* Live temperature monitoring on dashboard



* Automatic HVAC activation when thresholds crossed



* System responds in <100ms from sensor to actuator



* Visual indicators show system state (LED colors)

#### 

#### 2\. Adaptive Threshold Management



* Simulate 6 temperature fluctuations near threshold



* GDA detects pattern and adjusts thresholds automatically



* System reduces actuator cycling by 50-70%



* Dashboard displays threshold adjustment events



### 3\. Secure Communication



* All messages encrypted with TLS



* Wireshark packet capture showing encrypted traffic



* Certificate validation demonstrated



* 100% secure message delivery





### 4\. Protocol Performance Comparison

#### Based on completed testing with 10,000 messages:

#### MQTT Performance:



* QoS 0: 750ms (fastest)



* QoS 1: 2,627ms (reliable)



* QoS 2: 4,123ms (guaranteed)



* TLS adds 18-155% overhead



#### CoAP Performance:



* NON: 60ms for 10 requests (~6ms each) - 313x faster than CON



* CON: 18,866ms for 10 requests (~1,887ms each)



Key Result: Protocol choice matters! Use QoS 0/CoAP NON for frequent updates, QoS 2/CoAP CON for critical commands.

#### 

#### Quantifiable Results



<img width="1725" height="692" alt="Quantifiable Results" src="https://github.com/user-attachments/assets/f14a7ec1-0192-4eb4-ae81-db43a238a6c4" />






### Deliverables



* Working CDA with sensor integration and actuator control



* Working GDA with trend analysis and adaptive commands



* Configured Mosquitto broker with TLS encryption



* Performance test results (MQTT QoS 0/1/2, CoAP CON/NON)



* Security validation (TLS certificates, Wireshark analysis)



* Live dashboard showing real-time data and adaptive events



* Complete demonstration (90 minutes)





### Demonstration Timeline



<img width="1745" height="677" alt="Demo Timeline" src="https://github.com/user-attachments/assets/0fa7bd57-cfa4-4d15-a22a-876ee8172b47" />










### Conclusion

#### This project implements an intelligent, secure IoT system that demonstrates:



* Edge intelligence for immediate control (<100ms response)



* Gateway analytics for adaptive optimization (50-70% efficiency gain)



* Secure messaging with TLS encryption (100% encrypted communication)



* Protocol expertise showing when to use MQTT vs CoAP, QoS 0 vs QoS 2





Through rigorous testing with 10,000+ messages, we've proven that distributed intelligence (edge + gateway) creates smarter, more efficient IoT systems. The architecture is scalable, secure, and directly applicable to real-world smart building and industrial monitoring deployments.

Bottom Line: This isn't just a lab exercise—it's a production-ready architecture demonstrating best practices for secure, intelligent IoT system design.













