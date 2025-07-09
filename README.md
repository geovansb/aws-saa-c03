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


