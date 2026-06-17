# Working ELB Setup

## Elastic Load Balancer Configuration

### Load Balancer Details

| Parameter       | Value                     |
| --------------- | ------------------------- |
| Name            | WebApp-ELB                |
| Type            | Application Load Balancer |
| Scheme          | Internet-facing           |
| IP Address Type | IPv4                      |
| Protocol        | HTTP                      |
| Port            | 80                        |

---

## Target Group Configuration

| Parameter         | Value     |
| ----------------- | --------- |
| Target Group Name | WebApp-TG |
| Target Type       | Instance  |
| Protocol          | HTTP      |
| Port              | 80        |
| Health Check Path | /         |

---

## Registered Targets

| Instance ID    | Status  |
| -------------- | ------- |
| EC2 Instance 1 | Healthy |
| EC2 Instance 2 | Healthy |

---

## Security Group Rules

### Inbound Rules

| Type | Port |
| ---- | ---- |
| HTTP | 80   |
| SSH  | 22   |

### Outbound Rules

| Type        | Port |
| ----------- | ---- |
| All Traffic | All  |

---

## Traffic Flow

Internet → Load Balancer → EC2 Instance 1 / EC2 Instance 2

The Elastic Load Balancer distributes incoming traffic evenly across healthy EC2 instances, ensuring high availability and fault tolerance.

---

## Expected Outcome

* Load distributed across multiple servers.
* Improved application availability.
* Reduced server overload.
* Automatic failover if an instance becomes unhealthy.
