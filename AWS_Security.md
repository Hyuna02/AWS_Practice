# AWS Academy Cloud Architecting: Core Summary

## Introducing Cloud Architecting

### Key Concepts

* **Cloud Architecture Definition**: Applying cloud characteristics (such as on-demand availability and elasticity) alongside AWS services to design solutions that meet technical and business requirements.
* **AWS Well-Architected Framework Pillars**: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, and Sustainability.
* **Best Practices**:
* **Decouple** architectural tiers and use **[Elastic Load Balancing (ELB)](https://awsacademy.instructure.com/courses/178929)** to distribute traffic.
* Minimize manual intervention during system failures by using **[Amazon CloudWatch](https://awsacademy.instructure.com/courses/178929)** to detect issues and trigger automated provisioning.
* Maximize **cost efficiency** by provisioning only needed servers and stopping services when not in use.
* Store read-only content close to headquarters in **[Amazon S3](https://awsacademy.instructure.com/courses/178929)** and deliver it globally using **[Amazon CloudFront](https://awsacademy.instructure.com/courses/178929)**.


* **Global Infrastructure Selection**:
* **Regions**: Choose based on compliance laws, regulations, and reducing end-user latency.
* **Availability Zones (AZs)**: Choose to ensure application resiliency during system failures and protection against localized natural disasters.



### Highlights

* **Best definition of cloud architecture**: Applying cloud characteristics to a solution that uses cloud services and features to meet technical and business requirements.
* **Operational excellence practices**: Review and improve processes continuously; apply software engineering principles to infrastructure as code (IaC).
* **Multi-tier communication best practice**: Design the web tier to communicate with the application tier through **ELB**.
* **Server failure handling**: **CloudWatch** detects system failures and initiates automated provisioning for new servers.
* **Cost efficiency approach**: Provision necessary servers and stop services when idle.
* **Global data delivery**: Use an **S3** bucket in the closest region and serve users via **CloudFront**.

---

## Securing Access

### Key Concepts

#### 1. AWS Shared Responsibility Model

* **Customer Responsibility (Security *IN* the Cloud)**: Customer data, platform, applications, IAM (identity & access management), OS configurations, firewall/network configurations, and encryption (client-side & server-side).
* **AWS Responsibility (Security *OF* the Cloud)**: Compute, storage, databases, networking hardware, and global infrastructure (regions, AZs, edge locations).

#### 2. Security Pillar Design Principles

1. Implement a strong identity foundation.
2. Protect data in transit (TLS) and at rest (encryption).
3. Apply security at all layers.
4. Keep people away from data.
5. Maintain traceability.
6. Prepare for security events.
7. Automate security best practices.

#### 3. IAM (Identity and Access Management) Essentials

* **Authentication vs. Authorization**: Verifying "who you are" vs. determining "what you are allowed to do."
* **Key Terms**:
* **Principal**: A person or application that can sign in and make requests to AWS.
* **IAM Identity**: IAM resource objects that can be authorized in policies (users, groups, roles).
* **IAM Role**: Provides temporary security credentials and can be assumed by individuals, applications, or services.


* **Principle of Least Privilege**: Granting only the bare minimum permissions needed to perform a task.
* **Policy Evaluation Logic**:
* **Implicit Deny**: Default state when no explicit allow rule exists.
* **Explicit Deny**: Takes absolute precedence; if any policy explicitly denies an action, access is blocked regardless of any allow rules.
* **Policy Elements**: `Effect` (Allow/Deny), `Statement`, `Action`, `Resource`, `Condition`.



### Highlights

* **Least Privilege characteristics**: Grant access only as needed; craft security policies that limit access to specific tasks.
* **IAM benefit**: Grants principals granular access to resources.
* **IAM Roles**: Provide temporary security credentials; can be assumed by individuals, applications, and services.
* **Root user best practice**: Create a separate admin user for daily tasks and restrict the root user.
* **IAM evaluation order**: Checks for **explicit deny** statements before evaluating explicit allows.
* **IAM policy elements**: The **Effect** element specifies whether to allow or deny a request, and **Statement** encapsulates rules defining allowed or denied actions.
