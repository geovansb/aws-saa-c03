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

✅ Know the difference between Region, AZ, and Edge Location.
✅ Understand why AWS separates workloads across AZs (fault tolerance).
✅ Remember that Edge Locations serve cached content closer to users (low latency).
✅ Recognize that AZs have independent infrastructure within a Region.

## Topic 2


