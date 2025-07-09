# aws-saa-c03
AWS Solutions Architect Associate Certification Study

## Topic 1

### 📋 Quick Revision: AWS Global Infrastructure

#### 🌍 **Region**

* A **Region** is a **separate geographical area** where AWS has multiple data centers.
* Each Region contains all the resources (servers, networking, storage) needed to run AWS services.
* Regions are designed to provide **fault tolerance, high availability, and global reach**.
* Example: `us-west-2` (Oregon).

#### 🏢 **Availability Zone (AZ)**

* An **AZ** is an **isolated location** within a Region.
* Each AZ has its own **redundant power, networking, and connectivity**, physically separated from other AZs to minimize the impact of disasters.
* A Region typically has at least **3 or more AZs**, allowing for **high availability and failover**.
* When deploying in **Multi-AZ**, you design your workload across **two or more AZs** for resilience.

#### 🌐 **Edge Location**

* An **Edge Location** is a **data center closer to end users**, used to deliver content with **low latency**.
* They are part of AWS’s **Content Delivery Network (CDN)**, leveraging **Points of Presence (PoPs)**.
* Primarily used for **caching and content delivery**, e.g., via Amazon CloudFront.

#### 📝 Notes:

* AWS is continuously adding more Regions and AZs.
* GovCloud Regions are specialized Regions for **government workloads** with stricter compliance.
* Be aware that the **AZ names (e.g., `us-west-2a`) can map differently in different AWS accounts**, but **AZ IDs** (`usw2-az1`) stay consistent.

### 🔍 Exam Tips:

- ✅ Know the difference between Region, AZ, and Edge Location.
- ✅ Understand why AWS separates workloads across AZs (fault tolerance).
- ✅ Remember that Edge Locations serve cached content closer to users (low latency).
- ✅ Recognize that AZs have independent infrastructure within a Region.

## Topic 2

### 📋 Quick Revision: AWS Shared Responsibility Model

The **Shared Responsibility Model** defines **who is responsible for what** when running workloads in AWS.
It splits responsibilities between **AWS** and **the customer (you)**.

### 🧑‍💻 **Customer Responsibility — Security *in* the Cloud**

You are responsible for everything you build, configure, and run **inside the cloud**:

* 🔐 **Data encryption** — You must encrypt your data at rest & in transit if required.
* 💾 **Backup** — You must back up your data to meet your compliance & recovery needs.
* 👥 **Access & authorization** — You control who can access what, using IAM, MFA, etc.
* 🖥️ **OS & network configuration** — You maintain and patch your operating systems, firewalls, and VPC settings for EC2 or other services where applicable.

### ☁️ **AWS Responsibility — Security *of* the Cloud**

AWS takes care of the infrastructure and services **underneath your workloads**:

* 🖥️ **Hardware maintenance** — Managing servers, storage, networking hardware.
* 🏢 **Physical security** — Controlling who enters data centers, surveillance, etc.
* 🔄 **Redundancy & global infrastructure** — Keeping Regions, AZs, and Edge Locations running.
* 📦 **Managed services software** — Patching and securing AWS-managed services.

### 📝 Key Phrase to Remember:

> ✨ **You are responsible for security *in* the cloud, AWS is responsible for security *of* the cloud.**


### 🔍 Exam Tips:

- ✅ Know which responsibilities belong to AWS vs the customer.
- ✅ Be able to give examples of customer-controlled areas (e.g., IAM policies, S3 encryption).
- ✅ Understand that AWS’s responsibilities stop at the hypervisor & hardware layer — everything else is up to you.

## Topic 3

### 📋 Quick Revision: AWS Well-Architected Framework

The **Well-Architected Framework** provides **6 pillars** of best practices to design reliable, secure, efficient, and cost-effective cloud architectures.

You **must know these 6 pillars for the exam**, and understand examples of each.

### 🏗️ The 6 Pillars

#### 1️⃣ **Operational Excellence**

Run and monitor systems effectively, continuously improve.
Key practices:
- Operations as code
- Small, frequent changes
- Use managed services
- Collect metrics & gain insights

#### 2️⃣ **Security**

Protect **data, systems, and assets** while delivering business value.
Key practices:
- Encryption (at rest & in transit)
- Authentication & authorization controls
- Apply **layered security** (defense in depth)
- Maintain traceability (logging & monitoring)

#### 3️⃣ **Cost Optimization**

Avoid unnecessary costs while meeting business needs.
Key practices:
- Adopt a **consumption model** (pay for what you use)
- Use managed services where appropriate
- Measure and optimize efficiency
- Use discounts (e.g., Reserved Instances, Savings Plans)

#### 4️⃣ **Reliability**

Ensure workloads perform as intended and recover quickly from failures.
Key practices:
- Automate recovery (e.g., Auto Scaling, DNS failover)
- Test recovery procedures
- Design for horizontal scaling
- Monitor and handle changes in demand

#### 5️⃣ **Performance Efficiency**

Use IT resources efficiently to meet system requirements.
Key practices:
- Choose appropriate resources & instance types
- Experiment & innovate often
- Use serverless & global deployments
- Eliminate bottlenecks through testing and optimization

#### 6️⃣ **Sustainability**

Minimize environmental impact of cloud workloads.
Key practices:
- Right-size resources
- Increase utilization & avoid over-provisioning
- Scale on-demand instead of pre-allocating resources
- Use managed services to reduce footprint

### 🔍 Exam Tips:

- ✅ Memorize the **6 pillars & examples of each**.
- ✅ Many scenario-based questions test your ability to pick the best design aligned with one or more pillars.
- ✅ Remember: **Use managed services & automation whenever appropriate to achieve these goals.**

## Topic 4

### 📋 Quick Revision: High Availability vs. Fault Tolerance

#### 🏗️ **High Availability (HA)**

* Goal: Keep systems **operational most of the time**, minimizing **downtime & interruptions**.
* Typically achieves \~99.99% uptime.
* Uses **redundancy & failover** mechanisms, often across **multiple AZs**.
* Example:
  * Web app with **load balancer + auto-scaling** across AZs.
  * Short outages may still occur, but recovery is fast.

#### 🔒 **Fault Tolerance (FT)**

* Goal: Systems continue to operate **without interruption**, even if components fail.
* Aim is **100% uptime** — seamless failover with no visible impact.
* Typically involves **multi-region** deployments for geographic isolation.
* Example:
  * **Amazon Aurora Global Database** with synchronous multi-region replication.

### 📝 Key Differences:

| Feature            | High Availability            | Fault Tolerance               |
| ------------------ | ---------------------------- | ----------------------------- |
| **Downtime?**      | Minimal, brief interruptions | None, seamless operation      |
| **Design focus?**  | Redundancy & quick recovery  | Automatic, invisible failover |
| **Typical Scope?** | Multi-AZ                     | Multi-Region                  |

### 🔍 RTO & RPO: Disaster Recovery Metrics

#### ⏱️ **RTO (Recovery Time Objective)**

* Maximum acceptable **time to restore** service after an outage.
* Example: *We must recover within 5 minutes.*

#### 🕒 **RPO (Recovery Point Objective)**

* Maximum acceptable **data loss**, measured as the age of data that can be lost.
* Example: *We can afford to lose up to 10 hours of data.*

### 🔍 Exam Tips:

- ✅ Know the difference between HA & FT (especially AZ vs Region).
- ✅ Be ready to match examples with each.
- ✅ Understand RTO (how fast to recover) & RPO (how much data loss is acceptable).
- ✅ Be able to design for different business requirements based on these metrics.

## Topic 5

