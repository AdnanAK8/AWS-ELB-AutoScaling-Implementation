# Implementation Report

# AWS Elastic Load Balancer (ELB) and Auto Scaling Group (ASG)
---
# 1. Introduction

Cloud computing has transformed the way applications are deployed and managed. Modern applications require high availability, scalability, and fault tolerance to handle varying workloads efficiently.

Amazon Web Services (AWS) provides Elastic Load Balancing (ELB) and Auto Scaling services that help organizations build resilient cloud infrastructures. Elastic Load Balancing distributes incoming traffic among multiple EC2 instances, while Auto Scaling automatically adjusts the number of instances according to demand.

This project demonstrates the architecture, configuration, and working of ELB and Auto Scaling Groups in AWS.

---

# 2. Problem Statement

A single server can become overloaded when traffic increases, resulting in slower response times and potential downtime.

To solve this issue:

* Incoming traffic should be distributed across multiple servers.
* Resources should automatically scale according to workload.
* The application should remain highly available even if one server fails.

AWS ELB and Auto Scaling provide an efficient solution to these challenges.

---

# 3. Objectives

The primary objectives of this project are:

* To understand Elastic Load Balancing.
* To configure Auto Scaling Groups.
* To improve application availability.
* To achieve automatic scaling.
* To enhance fault tolerance.
* To optimize resource utilization.

---

# 4. AWS Services Used

| AWS Service           | Purpose                    |
| --------------------- | -------------------------- |
| Amazon EC2            | Virtual Servers            |
| Elastic Load Balancer | Traffic Distribution       |
| Auto Scaling Group    | Automatic Resource Scaling |
| Amazon CloudWatch     | Monitoring and Alerts      |
| Security Groups       | Network Security           |
| VPC                   | Networking Infrastructure  |

---

# 5. System Architecture

```text
                    Internet
                        │
                        ▼
          ┌──────────────────────────┐
          │ Elastic Load Balancer    │
          └─────────────┬────────────┘
                        │
             ┌──────────┴──────────┐
             ▼                     ▼
      EC2 Instance 1        EC2 Instance 2
             │                     │
             └──────────┬──────────┘
                        ▼
               Auto Scaling Group
            Min=2 | Desired=2 | Max=4
```

---

# 6. Implementation Methodology

## Step 1: EC2 Instance Configuration

Two EC2 instances are configured to host a sample web application.

### Configuration

* Amazon Linux AMI
* Instance Type: t2.micro
* HTTP Port: 80
* SSH Port: 22

The web server is installed and configured on both instances.

---

## Step 2: Target Group Creation

A Target Group is created to manage EC2 instances receiving traffic from the Load Balancer.

### Configuration

* Protocol: HTTP
* Port: 80
* Health Check Path: /

The EC2 instances are registered with the Target Group.

---

## Step 3: Elastic Load Balancer Setup

An Application Load Balancer (ALB) is configured.

### Configuration

| Parameter    | Value                     |
| ------------ | ------------------------- |
| Type         | Application Load Balancer |
| Scheme       | Internet Facing           |
| Protocol     | HTTP                      |
| Port         | 80                        |
| Target Group | WebApp-TG                 |

### Functions

* Distributes traffic across instances.
* Performs health checks.
* Redirects traffic away from unhealthy instances.

---

## Step 4: Launch Template Creation

A Launch Template is created to define the configuration for future EC2 instances.

### Included Parameters

* AMI Selection
* Instance Type
* Security Group
* Startup Configuration

This template is later used by the Auto Scaling Group.

---

## Step 5: Auto Scaling Group Configuration

An Auto Scaling Group is created using the Launch Template.

### Configuration

| Parameter        | Value |
| ---------------- | ----- |
| Minimum Capacity | 2     |
| Desired Capacity | 2     |
| Maximum Capacity | 4     |

The Auto Scaling Group is attached to the Load Balancer.

---

## Step 6: Scaling Policy Configuration

### Policy Type

Target Tracking Scaling Policy

### Monitoring Metric

Average CPU Utilization

### Threshold

50%

### Scale-Out Action

When CPU utilization exceeds 50%:

* Launch one additional EC2 instance.
* Register the instance with the Load Balancer.

### Scale-In Action

When CPU utilization falls below 30%:

* Terminate unused instances.
* Reduce infrastructure cost.

---

# 7. Workflow

```text
User Request
      │
      ▼
Elastic Load Balancer
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
Scale Out / Scale In
```

---

# 8. Benefits

### High Availability

Traffic is distributed across multiple servers, reducing downtime.

### Scalability

Resources automatically increase during peak demand.

### Fault Tolerance

If one instance fails, traffic is redirected to healthy instances.

### Cost Optimization

Unused resources are terminated automatically.

### Better Performance

Workloads are evenly distributed among available servers.

---

# 9. Expected Results

* Continuous application availability.
* Balanced traffic distribution.
* Automatic resource management.
* Reduced operational effort.
* Improved user experience.

---

# 10. Challenges Faced

* Understanding AWS networking concepts.
* Learning Load Balancer architecture.
* Configuring Auto Scaling policies.
* AWS billing restrictions prevented live implementation.

Therefore, the project focuses on architectural design, configuration planning, and implementation documentation.

---

# 11. Learning Outcomes

Through this project, the following concepts were learned:

* Elastic Load Balancing
* Auto Scaling Groups
* EC2 Instance Management
* CloudWatch Monitoring
* Cloud Scalability
* High Availability Design
* Resource Optimization

---

# 12. Conclusion

AWS Elastic Load Balancer and Auto Scaling Group provide a robust solution for managing scalable and highly available applications. By distributing incoming traffic and dynamically adjusting resources according to demand, organizations can improve performance, reduce downtime, and optimize infrastructure costs.

This project successfully demonstrates the architecture, configuration process, workflow, and benefits of implementing ELB and Auto Scaling in AWS cloud environments.

---

## Author

**Adnan Akhtar**

