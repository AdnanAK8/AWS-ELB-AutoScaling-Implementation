# AWS Elastic Load Balancer (ELB) and Auto Scaling Implementation

##  Project Overview

This project demonstrates the implementation of **AWS Elastic Load Balancer (ELB)** and **Auto Scaling Groups (ASG)** to improve application availability, fault tolerance, and scalability. The load balancer distributes incoming traffic across multiple EC2 instances, while Auto Scaling automatically adjusts the number of instances based on CPU utilization.

---

##  Objectives

* Configure an Elastic Load Balancer (ELB).
* Distribute traffic across multiple EC2 instances.
* Create an Auto Scaling Group (ASG).
* Implement automatic scaling based on CPU utilization.
* Improve application availability and reliability.

---

##  Architecture

```text
                    Internet
                        │
                        ▼
           ┌─────────────────────────┐
           │ Elastic Load Balancer   │
           └───────────┬─────────────┘
                       │
        ┌──────────────┴──────────────┐
        │                             │
        ▼                             ▼
┌─────────────────┐         ┌─────────────────┐
│   EC2 Instance  │         │   EC2 Instance  │
│   Web Server 1  │         │   Web Server 2  │
└─────────────────┘         └─────────────────┘
        │                             │
        └──────────────┬──────────────┘
                       ▼
              Auto Scaling Group
          (Min: 2, Desired: 2, Max: 4)
```

---

##  AWS Services Used

| Service         | Purpose                |
| --------------- | ---------------------- |
| EC2             | Virtual Servers        |
| ELB             | Traffic Distribution   |
| Auto Scaling    | Automatic Scaling      |
| CloudWatch      | Monitoring Metrics     |
| Security Groups | Network Security       |
| VPC             | Network Infrastructure |

---

##  Implementation Steps

### Step 1: Launch EC2 Instances

* Launch two Amazon EC2 instances.
* Configure Security Groups:

  * SSH (Port 22)
  * HTTP (Port 80)
* Install Apache Web Server.

Example User Data Script:

```bash
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<h1>Welcome to AWS Web Server</h1>" > /var/www/html/index.html
```

---

### Step 2: Configure Target Group

1. Open EC2 Dashboard.
2. Navigate to Target Groups.
3. Create a new Target Group.
4. Select:

   * Target Type: Instance
   * Protocol: HTTP
   * Port: 80
5. Register both EC2 instances.

---

### Step 3: Create Elastic Load Balancer

1. Open Load Balancers.
2. Create Application Load Balancer.
3. Select:

   * Internet-facing
   * IPv4
4. Choose VPC and Public Subnets.
5. Configure Listener:

   * HTTP (80)
6. Attach Target Group.

---

### Step 4: Verify Load Balancing

* Copy the Load Balancer DNS Name.
* Open it in a browser.
* Refresh multiple times to verify traffic distribution.

---

### Step 5: Create Launch Template

1. Open Launch Templates.
2. Configure:

   * Amazon Linux AMI
   * t2.micro Instance
   * Security Group
   * User Data Script

This template will be used by Auto Scaling Group.

---

### Step 6: Create Auto Scaling Group

1. Open Auto Scaling Groups.
2. Create Auto Scaling Group using Launch Template.
3. Configure:

   * Minimum Capacity: 2
   * Desired Capacity: 2
   * Maximum Capacity: 4
4. Attach Existing Load Balancer.

---

### Step 7: Configure Scaling Policy

Policy Type:

```text
Target Tracking Scaling Policy
```

Metric:

```text
Average CPU Utilization
```

Target Value:

```text
50%
```

When CPU utilization exceeds the threshold, additional instances are launched automatically.

---

## Benefits

* High Availability
* Improved Reliability
* Automatic Scaling
* Better Performance
* Fault Tolerance
* Cost Optimization

##  Challenges Faced

* Understanding Load Balancer configuration.
* Configuring Security Groups.
* Linking Target Groups with ELB.
* Setting Auto Scaling policies correctly.

---

##  Learning Outcomes

* Learned AWS Load Balancing concepts.
* Understood Auto Scaling mechanisms.
* Gained experience with CloudWatch monitoring.
* Improved cloud infrastructure management skills.

---

##  Future Enhancements

* HTTPS using SSL Certificates.
* Multi-AZ Deployment.
* Integration with Route 53.
* CI/CD Pipeline using GitHub Actions.
* Container Deployment using Docker and ECS.

## Note

AWS requires billing activation to create EC2 instances, Load Balancers, and Auto Scaling Groups.

Due to billing restrictions on the current AWS account, a live implementation could not be performed. This repository demonstrates the complete architecture, configuration process, implementation steps, and expected outcomes of ELB and Auto Scaling deployment.

---

##  Conclusion

The implementation of Elastic Load Balancer (ELB) and Auto Scaling Group (ASG) successfully improves the scalability, reliability, and availability of cloud-based applications. By automatically distributing traffic and dynamically adjusting resources based on demand, AWS provides a robust infrastructure solution for modern web applications.

---

###  Author

**Adnan Akhtar**
Computer Science Engineering Student
Cloud Computing & AWS Enthusiast
