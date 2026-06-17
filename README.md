# AWS ELB and Auto Scaling Implementation

![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![ELB](https://img.shields.io/badge/Elastic_Load_Balancer-Implemented-blue)
![AutoScaling](https://img.shields.io/badge/Auto_Scaling-Configured-green)
![Status](https://img.shields.io/badge/Status-Documentation%20Based-success)

---

##  Project Overview

This project demonstrates the concepts and configuration of **AWS Elastic Load Balancer (ELB)** and **Auto Scaling Groups (ASG)** used to build scalable, highly available, and fault-tolerant cloud applications.

The objective is to distribute incoming traffic across multiple EC2 instances and automatically adjust computing resources based on application demand.

---

##  Objectives

* Understand AWS Elastic Load Balancing.
* Configure Auto Scaling Groups.
* Improve application availability.
* Enable automatic scaling based on workload.
* Reduce downtime and improve performance.

---

##  Architecture Diagram

```text
                    Internet
                        │
                        ▼
           ┌──────────────────────┐
           │ Elastic Load Balancer│
           └───────────┬──────────┘
                       │
          ┌────────────┴────────────┐
          ▼                         ▼
   EC2 Instance 1            EC2 Instance 2
          │                         │
          └────────────┬────────────┘
                       ▼
              Auto Scaling Group
              Min:2 | Max:4
```

---

## Repository Contents

```text
AWS-ELB-AutoScaling-Implementation/
│
├── README.md
├── implementation-report.md
├── ELB-Setup.md
├── AutoScaling-Group.md
```

---

##  AWS Services Used

| Service               | Purpose                    |
| --------------------- | -------------------------- |
| Amazon EC2            | Virtual Servers            |
| Elastic Load Balancer | Traffic Distribution       |
| Auto Scaling Group    | Automatic Resource Scaling |
| CloudWatch            | Monitoring & Alerts        |
| Security Groups       | Network Security           |
| VPC                   | Networking Infrastructure  |

---

##  Deliverable 1: ELB Setup

### Load Balancer Configuration

| Parameter    | Value                     |
| ------------ | ------------------------- |
| Type         | Application Load Balancer |
| Scheme       | Internet Facing           |
| Protocol     | HTTP                      |
| Port         | 80                        |
| Target Group | WebApp-TG                 |

### Features

* Traffic Distribution
* Health Checks
* High Availability
* Fault Tolerance
* Improved Performance

---

##  Deliverable 2: Auto Scaling Group

### Auto Scaling Configuration

| Parameter         | Value           |
| ----------------- | --------------- |
| Minimum Instances | 2               |
| Desired Instances | 2               |
| Maximum Instances | 4               |
| Scaling Metric    | CPU Utilization |
| Threshold         | 50%             |

### Scaling Behavior

#### Scale Out

```text
CPU Utilization > 50%
```

Action:

```text
Launch Additional EC2 Instance
```

#### Scale In

```text
CPU Utilization < 30%
```

Action:

```text
Terminate Unused Instance
```

---

##  Benefits

✅ High Availability

✅ Automatic Resource Scaling

✅ Better Performance

✅ Reduced Downtime

✅ Cost Optimization

✅ Improved Reliability

---

##  Expected Workflow

```text
User Request
      │
      ▼
Load Balancer
      │
 ┌────┴────┐
 ▼         ▼
EC2-1    EC2-2
      │
      ▼
CloudWatch Monitoring
      │
      ▼
Auto Scaling Group
      │
      ▼
Launch / Terminate Instances
```

---

##  Learning Outcomes

Through this project, I gained knowledge of:

* AWS Cloud Infrastructure
* EC2 Instances
* Elastic Load Balancing
* Auto Scaling Groups
* CloudWatch Monitoring
* High Availability Architecture
* Cloud Resource Optimization

---

## Note

Due to AWS billing restrictions, a live deployment could not be performed. This repository demonstrates the complete architecture, configuration process, implementation documentation, and expected outcomes of AWS Elastic Load Balancer and Auto Scaling Group implementation.

---

##  Conclusion

Elastic Load Balancer and Auto Scaling are essential AWS services for creating scalable and highly available cloud applications. Together, they ensure efficient traffic distribution, automatic resource management, and improved application reliability.

---

###  Author

**Adnan Akhtar**
Computer Science Engineering Student
Cloud Computing & AWS Enthusiast
