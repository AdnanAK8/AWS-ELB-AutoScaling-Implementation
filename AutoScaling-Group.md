# Auto Scaling Group Configuration

## Launch Template

### Instance Configuration

| Parameter      | Value             |
| -------------- | ----------------- |
| AMI            | Amazon Linux 2023 |
| Instance Type  | t2.micro          |
| Key Pair       | MyKeyPair         |
| Security Group | WebServer-SG      |

---

## Auto Scaling Group Settings

| Parameter               | Value      |
| ----------------------- | ---------- |
| Auto Scaling Group Name | WebApp-ASG |
| Minimum Capacity        | 2          |
| Desired Capacity        | 2          |
| Maximum Capacity        | 4          |

---

## Attached Load Balancer

Application Load Balancer (ALB)

Target Group: WebApp-TG

---

## Scaling Policy

### Target Tracking Policy

Metric:

```text
Average CPU Utilization
```

Target Value:

```text
50%
```

---

## Scale-Out Rule

Condition:

```text
CPU > 50%
```

Action:

```text
Add 1 EC2 Instance
```

---

## Scale-In Rule

Condition:

```text
CPU < 30%
```

Action:

```text
Remove 1 EC2 Instance
```

---

## Monitoring

AWS CloudWatch continuously monitors:

* CPU Utilization
* Network Traffic
* Instance Health
* Request Count

---

## Benefits

* Automatic scaling during peak traffic.
* Cost optimization during low traffic.
* High availability.
* Improved performance.
* Reduced manual intervention.

---

## Expected Outcome

The Auto Scaling Group automatically launches or terminates EC2 instances based on application demand, ensuring scalability and reliability.
