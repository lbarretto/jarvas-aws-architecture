<div align="center">

# ☁️ Startup Jarva's

### AI-Powered Document Management SaaS Platform

<img width="1672" height="940" alt="Startup Jarva's project cover" src="https://github.com/user-attachments/assets/dc2e1360-263c-47af-b3fc-912f140d9fa7" />

<br/>

[![🇧🇷 Português](https://img.shields.io/badge/🇧🇷-Português-009c3b?style=for-the-badge)](./README.md)
[![🇺🇸 English](https://img.shields.io/badge/🇺🇸-English-lightgrey?style=for-the-badge)](./README.en.md)

<br/>

[![AWS](https://img.shields.io/badge/AWS-Cloud%20Architecture-FF9900?style=for-the-badge\&logo=amazonaws\&logoColor=white)](#5-solution)
[![Serverless](https://img.shields.io/badge/Architecture-Serverless-232F3E?style=for-the-badge\&logo=amazonaws\&logoColor=white)](#5-solution)
[![IaC](https://img.shields.io/badge/IaC-CloudFormation-527FFF?style=for-the-badge\&logo=amazonaws\&logoColor=white)](#7-infrastructure-as-code)
[![Status](https://img.shields.io/badge/Phase%2001-Completed-brightgreen?style=for-the-badge)](#5-solution)
[![Phase 02](https://img.shields.io/badge/Phase%2002-Planned-lightgrey?style=for-the-badge)](#-evolution-and-future-vision--phase-02)

[![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=flat-square\&logo=amazons3\&logoColor=white)](#-aws-services-used)
[![AWS Lambda](https://img.shields.io/badge/AWS%20Lambda-FF9900?style=flat-square\&logo=awslambda\&logoColor=white)](#-aws-services-used)
[![Amazon DynamoDB](https://img.shields.io/badge/Amazon%20DynamoDB-4053D6?style=flat-square\&logo=amazondynamodb\&logoColor=white)](#-aws-services-used)
[![Amazon Cognito](https://img.shields.io/badge/Amazon%20Cognito-DD344C?style=flat-square\&logo=amazoncognito\&logoColor=white)](#-aws-services-used)
[![API Gateway](https://img.shields.io/badge/Amazon%20API%20Gateway-FF4F8B?style=flat-square\&logo=amazonapigateway\&logoColor=white)](#-aws-services-used)
[![CloudFormation](https://img.shields.io/badge/AWS%20CloudFormation-527FFF?style=flat-square\&logo=amazonaws\&logoColor=white)](#7-infrastructure-as-code)

<br/>

*Project developed as part of the challenge proposed by **Escola da Nuvem** for the practical application of knowledge in AWS Cloud and cloud solution architecture.*

</div>

---

<details open>
<summary><h2>📌 Table of Contents</h2></summary>

* [1️⃣ TCC Context](#1-tcc-context)

  * [1.1 💡 What is the project?](#-what-is-the-project)
  * [1.2 📊 Why do we believe this is a relevant topic?](#-why-do-we-believe-this-is-a-relevant-topic)

* [2️⃣ Project Context](#2-project-context)

* [3️⃣ Problem to be solved and business impact](#3-problem-to-be-solved-and-business-impact)

  * [3.1 🔒 Data security and isolation](#-data-security-and-isolation)
  * [3.2 🗃️ Document retention](#️-document-retention)
  * [3.3 💵 Storage cost](#-storage-cost)
  * [3.4 ⚖️ The central dilemma](#️-the-central-dilemma)

* [4️⃣ Project and solution requirements](#4-project-and-solution-requirements)

* [5️⃣ Solution](#5-solution)

  * [5.1 🧩 From need to solution](#-from-need-to-solution)
  * [5.2 🔭 Solution overview](#-solution-overview)
  * [5.3 🛠️ AWS services used](#️-aws-services-used)
  * [5.4 🚶 Customer Journey](#-customer-journey)
  * [5.5 🏗️ AWS Architecture](#️-aws-architecture)
  * [5.6 🛡️ Resilience and fault tolerance](#resilience-and-fault-tolerance)
  * [5.7 🧭 Architecture, AWS CAF and AWS Well-Architected Framework](#-architecture-aws-caf-and-aws-well-architected-framework)
  * [5.8 💰 Project costs](#-project-costs)
  * [5.9 🚀 Evolution and Future Vision — Phase 02](#-evolution-and-future-vision--phase-02)

* [6️⃣ How the project was developed](#6-how-the-project-was-developed)

* [7️⃣ Infrastructure as Code](#7-infrastructure-as-code)

* [8️⃣ Presentation Video](#8--presentation-video)

* [9️⃣ Acknowledgments](#9-acknowledgments)

* [🔟 References](#10-references)

</details>

---

# 1. TCC Context

## 💡 What is the project?

This project was developed as part of a challenge proposed by **Escola da Nuvem**, with the goal of reinforcing, in practice, the knowledge acquired about cloud computing and, especially, how AWS services can be used to solve real-world business problems.

The challenge represents an opportunity to move beyond a purely conceptual approach and apply the knowledge acquired during our preparation for the **AWS Certified Cloud Practitioner** certification to the analysis and construction of an architectural solution.

More than simply selecting AWS services, the objective of the project is to understand the presented problem, identify its needs and constraints, and then evaluate how different cloud resources can add value to the business.

This approach also led us to realize that the project involves much more than file storage. Documents have a lifecycle, different levels of usage over time, security requirements, and strategic value for the business.

Therefore, decisions related to data organization, access, retention, and cost become part of the solution's architecture itself.

## 📊 Why do we believe this is a relevant topic?

The topic becomes especially relevant when we consider the growing use of Artificial Intelligence and the importance of the data that feeds these solutions.

In the proposed scenario, the documents uploaded by customers represent the historical foundation that will be used for the future evolution of the company's AI models.

Therefore, ensuring that this data is organized, protected, available when needed, and economically sustainable over time is a fundamental part of the business strategy.

In addition, the proposed scenario is set within a context of significant growth in the Artificial Intelligence market.

As identified during the scenario analysis:

> 📈 According to a projection by Gartner, global investment in artificial intelligence is expected to reach US$2.59 trillion in 2026, a 47% increase compared to the previous year, with expectations of reaching nearly US$3.5 trillion in 2027.
>
> 🇧🇷 In Brazil, an IBM study showed that 78% of Brazilian companies plan to increase their investments in AI, while AI spending in the country is expected to exceed US$2.4 billion, representing 30% growth compared to 2024.
>
> 🎯 Strategic adoption has also increased sharply: 95.2% of organizations consider AI a strategic priority for 2026, compared with only 32.8% investing in the technology in 2024.
>
> 🏗️ Approximately 45% of all projected investment for 2026 is related to AI infrastructure, including components such as cloud storage, processing, and data pipelines.

These figures help contextualize why an architecture focused on data storage and management for AI applications is relevant. The growth in Artificial Intelligence investments also increases the importance of the infrastructure required to support these solutions.

In the case of Startup Jarva's, this relationship is particularly important because the documents received by the platform represent precisely the historical raw material that may be used to train and evolve future AI models.

> **All this AI evolution depends on something fundamental: data that is properly stored, organized, protected, and available for use. There is no high-quality AI without an adequate historical data foundation behind it.**

The project therefore represents an increasingly relevant problem:

> **How can we build an infrastructure capable of transforming the growth in data volume into a strategic asset without compromising security, availability, and financial sustainability?**

<p align="center">
  <img width="1376" height="768" alt="AI growth context" src="https://github.com/user-attachments/assets/cf38ec2f-b4db-4055-991c-67868188a3ac" />
</p>

---

# 2. Project Context

**Startup Jarva's** is a hyper-growth company that provides a SaaS platform focused on **intelligent data extraction using Artificial Intelligence**.

As part of this service, the platform receives documents uploaded by customers, mainly **PDFs and images**, which serve as input for AI processing.

The expected volume is approximately **50,000 new files per month**, equivalent to around **600,000 files per year**, with a continuous growth trend.

The scenario has a characteristic that completely changes how the problem must be addressed:

> **The files cannot be deleted.**

Old documents continue to have value because they represent the historical data used as a foundation for training future Artificial Intelligence models.

Therefore, as the company grows, its amount of data also continuously increases.

Within a few years, the platform may accumulate millions of documents. This history represents not only a large amount of data, but also an intellectual asset that can directly contribute to the evolution of the company and its AI models.

This is precisely why we understand that Startup Jarva's is not simply building a document repository:

> **A repository preserves information. A data asset preserves information with the intention of generating value from it.**

This change in perspective is fundamental to understanding the rest of the project. Storage is no longer merely supporting infrastructure and becomes part of the product's strategy itself.

---

# 3. Problem to be solved and business impact

The problem faced by Startup Jarva's results from the combination of **rapid growth, the need for customer isolation, permanent document retention, and storage cost control**.

## 🔒 Data security and isolation

The platform has a **multi-tenant** nature, meaning that different customers use the same application and infrastructure.

This creates a fundamental requirement:

> **One customer cannot have access to documents belonging to another customer.**

Users need to access their own documents quickly and securely, but without a configuration, permission, or implementation failure allowing files belonging to other users to be exposed.

This isolation requirement must be considered from the beginning of the architecture rather than treated later as a correction.

The risk associated with this problem is not merely theoretical. The project's supporting documentation itself uses a real-world case to contextualize the impact that an inadequate configuration can cause:

> ⚠️ In 2022, a hacker claimed to have obtained data from approximately one billion Chinese citizens from an Elasticsearch deployment associated with a government agency. The report itself raised doubts about the veracity and scale of the claim, so the case should not be treated as a confirmed exposure on that scale.
>
> The example is used as contextualization of the risk associated with inadequate infrastructure configurations and unintended data exposure.

The value of the example lies in demonstrating the type of risk that Startup Jarva's needs to prevent:

> **An inadequate configuration or deployment can turn infrastructure that should protect data into a gateway for accessing it.**

This is especially relevant to Startup Jarva's because the platform will depend on the trust of customers who will be providing their own documents to the service.

A data exposure would compromise customer trust in the platform and, consequently, the company's value proposition itself. For this reason:

> **Security should not be a layer added later. It needs to be part of the architecture from the very first file received by the platform.**

---

## 🗃️ Document retention

Unlike systems where old data can be discarded, Startup Jarva's has a different strategic requirement:

> **No file should be deleted as part of the platform's normal operation.**

Documents represent the historical foundation that may be used to train future AI models. The fact that a document is old does not mean that it has lost its value. On the contrary, it becomes part of the company's historical data assets.

In numerical terms, the scenario expects approximately **50,000 files per month**, equivalent to around **600,000 files per year**.

Since no files are discarded as part of normal operations, this volume will continue to grow over time and may reach millions of documents after several years of operation.

---

## 💵 Storage cost

Permanent retention creates a second problem.

If approximately 50,000 files are added every month and none are removed, the stored volume will continue to grow indefinitely.

Keeping all these documents permanently in a storage class designed for frequent access could generate a cost incompatible with the company's growth.

Therefore, the project needs to consider the **data lifecycle**.

Recent documents have a higher access frequency and need immediate availability, while historical documents tend to be accessed less frequently, although they continue to have strategic value.

In the proposed architecture, documents initially remain in **Amazon S3 Intelligent-Tiering**, which is suitable for the period of higher access frequency.

After the first **12 months**, an **S3 Lifecycle** rule can automatically transition objects to **S3 Glacier Deep Archive**, reducing the storage cost of historical documents that still need to be preserved.

This strategy allows storage costs to follow the expected behavior of the data over time.

---

## ⚖️ The central dilemma

Based on these problems, we identified four needs that must be addressed simultaneously:

1. **⚡ Fast access:** customers need to normally access documents during the first 12 months.
2. **🗃️ Permanent retention:** no file should be deleted as part of normal platform operations because all files are part of the company's historical data asset.
3. **💵 Controlled cost:** old documents should stop occupying a frequent-access storage class when access becomes less frequent.
4. **🔒 Isolation and security:** each document belongs to a specific customer and cannot be accessed by other customers.

It is precisely the combination of these requirements that makes the problem more interesting.

Startup Jarva's cannot simply choose the cheapest alternative because that could negatively affect document access. Likewise, it cannot permanently keep the entire history in a storage class designed for frequent access because costs would grow together with the historical database. It also cannot prioritize only ease of access without considering customer isolation.

The challenge, therefore, is not simply finding a place to store millions of documents.

> **The real challenge is balancing security, access, retention, and cost throughout the entire data lifecycle.**

This is the question the architecture needs to answer.

---

# 4. Project and solution requirements

Based on the presented scenario and the identified problems, we established the requirements that the solution needs to meet.

### 🔐 Security

The solution must guarantee **customer isolation**, preventing one user from accessing documents belonging to another.

Access to documents must be controlled and restricted to the authorized owner.

### 📈 Scalability

The solution must support the platform's continuous growth and the ingestion of approximately **50,000 new files per month**, without relying on a single machine or infrastructure that must be manually resized whenever demand increases.

### 🛡️ Durability and retention

Historical documents must not be deleted by the application as part of normal operations.

The solution must allow files to remain preserved even when they are no longer accessed frequently.

### ⚡ Availability and access

Documents uploaded by customers must remain available for consultation during the period in which they have the highest access frequency, especially during the first 12 months.

### 💰 Cost efficiency

Storage costs should decrease as documents age.

The solution must allow files to remain preserved without requiring the entire historical dataset to permanently remain in a storage class intended for frequent access.

### 📊 Operations and monitoring

The infrastructure must allow the operation of the solution to be monitored, failures to be identified, and an audit trail of performed actions to be maintained.

### 🔄 Reproducibility

The infrastructure must be capable of being recreated consistently, allowing the architecture to be documented and reproduced through code.

### 🧱 Resilience and fault tolerance

The solution must avoid dependencies on individual servers or components whose unavailability could completely interrupt the platform.

Whenever possible, the architecture should use managed services capable of providing high availability as part of their operation, reducing the need for manual infrastructure management.

In addition, the solution must be capable of continuing to preserve documents and maintain the main services available even in the event of isolated failures affecting components or the underlying infrastructure.

---

# 5. Solution

<details>
<summary><h3>🗂️ Quick Index of Section 5</h3></summary>

* 5.1 🧩 [From need to solution](#-from-need-to-solution)
* 5.2 🔭 [Solution overview](#-solution-overview)
* 5.3 🛠️ [AWS services used](#-aws-services-used)
* 5.4 🚶 [Customer Journey](#-customer-journey)
* 5.5 🏗️ [AWS Architecture](#-aws-architecture)
* 5.6 🛡️ [Resilience and fault tolerance](#resilience-and-fault-tolerance)
* 5.7 🧭 [Architecture, AWS CAF and AWS Well-Architected Framework](#-architecture-aws-caf-and-aws-well-architected-framework)
* 5.8 💰 [Project costs](#-project-costs)
* 5.9 🚀 [Evolution and Future Vision — Phase 02](#-evolution-and-future-vision--phase-02)

</details>

## 🧩 From need to solution

Based on these requirements, it is clear that Startup Jarva's challenge is not simply storing a large amount of documents.

The architecture needs to follow the company's growth, protect each customer's data, preserve historical information as a strategic asset, and, at the same time, keep costs under control.

It is from these needs that we arrived at the architectural proposal for this project.

The choice of AWS services therefore does not start with the technology itself, but with the problems that need to be solved and the requirements that the solution needs to meet.

The proposed solution uses a **serverless** architecture based on AWS managed services, reducing the need for infrastructure management and allowing the solution to adapt to the platform's demand.

The architecture also separates important system responsibilities:

* 🔑 Authentication
* 🛂 Access control
* ⚙️ Business logic
* 🗄️ Document storage
* 🏷️ Metadata management
* 👀 Observability
* 📜 Auditing
* ♻️ Data lifecycle management
* 🧱 Infrastructure provisioning

---

## 🔭 Solution overview

The solution was designed to allow customers to upload and access their documents securely without receiving direct or unrestricted access to the storage environment.

The flow starts with user authentication through **Amazon Cognito**. After authentication, requests are sent to **Amazon API Gateway** and processed by **AWS Lambda**, which is responsible for applying business rules and validating the required permissions.

Metadata and document ownership information are stored in **Amazon DynamoDB**, allowing the system to verify whether the user is authorized to access a specific file.

Documents are stored in a private **Amazon S3** bucket. After permission validation, access is granted through **temporary pre-signed URLs**, limited to the requested operation and for a defined period.

In this way, the solution contributes to **customer isolation**, prevents public exposure of documents, and ensures that each user only has access to the files for which they are authorized.

### 📤 File access strategy

In Phase 01, uploads and downloads are performed directly through the **standard Amazon S3 endpoint**, using pre-signed URLs generated by the application.

This approach allows the customer to transfer files directly to S3 without the content having to pass through API Gateway or AWS Lambda, reducing intermediate processing while keeping access controlled by the application.

The use of pre-signed URLs ensures that the user receives authorization only to perform the specific requested operation and within a limited period.

Thus, the architecture meets the requirement for secure document transfer without adding additional acceleration mechanisms that are not necessary for the current scenario.

### 📦 Storage strategy

During the first **12 months**, documents remain in **Amazon S3 Intelligent-Tiering**, meeting the requirement for frequent access and immediate availability.

After this period, an **S3 Lifecycle** rule can automatically transition objects to **S3 Glacier Deep Archive**.

This storage class is suitable for long-term storage of data that needs to be preserved but has a low access frequency.

The transition reduces storage costs without deleting historical documents.

### 🔏 Document preservation

**S3 Object Lock** helps protect objects from deletion or modification during the configured retention period.

The retention configuration should be defined according to Startup Jarva's business requirements.

Therefore, Object Lock acts as an additional layer of document protection, while S3 Lifecycle is responsible for the transition strategy between storage classes.

### 🔑 Encryption

Objects stored in Amazon S3 are protected by **server-side encryption**, using the standard encryption provided by the service.

In a future evolution, **AWS KMS** may be incorporated to provide greater control over encryption keys and their respective access policies.

The result is an architecture designed to balance **security, scalability, resilience, historical preservation, user experience, and cost sustainability**.

By using managed and serverless services, the solution also reduces dependence on individually managed components, benefiting from the availability and fault-tolerance mechanisms offered by the AWS services used.

---

## 🛠️ AWS services used

| Service                               | Role in the solution                                                                                                                                    |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🔑 **Amazon Cognito**                 | User authentication and identity management, including the issuance of JWT tokens used for application access control                                   |
| 🚪 **Amazon API Gateway**             | API entry layer responsible for receiving requests, authorization validation, and integration with application logic                                    |
| ⚙️ **AWS Lambda**                     | Business logic execution, identity and permission validation, metadata queries, and pre-signed URL generation                                           |
| 🏷️ **Amazon DynamoDB**               | Storage of metadata and document ownership information, supporting access validation and authorization                                                  |
| 🗄️ **Amazon S3 Intelligent-Tiering** | Storage class used for documents during the initial period of higher access frequency, automatically adjusting access tiers according to usage patterns |
| ♻️ **S3 Lifecycle**                   | Document lifecycle management and automatic transition of objects to more appropriate storage classes over time                                         |
| ❄️ **S3 Glacier Deep Archive**        | Long-term historical storage for documents that need to be preserved but have a low access frequency                                                    |
| 🔒 **S3 Object Lock**                 | Protection of objects against deletion or modification during the configured retention period                                                           |
| 🛂 **AWS IAM**                        | Permission control following the principle of least privilege among services and architecture resources                                                 |
| 📊 **Amazon CloudWatch**              | Operational monitoring through logs, metrics, dashboards, and alarms                                                                                    |
| 📜 **AWS CloudTrail**                 | Logging and auditing of actions performed within the account and AWS services                                                                           |
| 💰 **AWS Budgets**                    | Budget definition and monitoring, enabling cost-related alerts to be created                                                                            |
| 📈 **AWS Cost Explorer**              | Analysis of service costs and usage patterns, supporting the identification of trends and optimization opportunities                                    |
| 🧱 **AWS CloudFormation**             | Infrastructure provisioning, reproduction, and standardization through code                                                                             |

---

## 🚶 Customer Journey

The technical architecture shows how the services are connected. However, to understand the solution from the perspective of the person using the platform, we also developed a view focused on the **Customer Journey**.

This journey represents the path followed by the user from accessing the platform to the historical preservation of their documents.

<p align="center">
  <img width="1536" height="1024" alt="Customer Journey - AI-Powered Document Management SaaS Platform" src="https://github.com/user-attachments/assets/205a90b4-dfd8-44de-83bf-c4a7f09828fc" />
</p>

The journey was organized into three main stages:

### 1. 📥 Access and upload

The customer accesses the platform, authenticates, and uploads a document for application processing.

At this point, the objective is to provide a simple user experience without compromising security and the correct identification of document ownership.

### 2. 🔐 Protection and usage

After upload, the document is associated with the customer's account and securely stored.

When the user wants to view or download a file, the platform verifies their identity and permissions before granting access. The customer does not receive unrestricted access to the storage environment. Access is granted only to the requested document and in a controlled manner.

### 3. 🗄️ Historical preservation

Over time, documents remain preserved as part of the company's history.

During the first 12 months, files remain in a storage class suitable for frequent access. After this period, the lifecycle strategy allows them to transition to a lower-cost historical storage class while keeping the documents preserved for future business needs.

This view reinforces one of the project's central principles:

> **Data security and preservation must be present throughout the entire customer journey, not only at the time of storage.**

---

## 🏗️ AWS Architecture

The technical view of the solution presents the AWS services used and the main communication flow between the architecture components.

<p align="center">
  <img width="1533" height="1026" alt="Image" src="https://github.com/user-attachments/assets/36705fb2-a173-4a72-9f50-2d1fefdc9bd7" />
</p>

### 🔍 How does the architecture solve the problem?

The architecture was designed to directly address the main challenges identified by Startup Jarva's.

* **🔒 Security and isolation:** authentication through Amazon Cognito, application-level validations, and the use of pre-signed URLs allow document access to be controlled without directly exposing the storage environment.
* **🗃️ Retention and historical preservation:** Amazon S3 provides a durable foundation for document storage, while S3 Object Lock helps protect documents against deletion or modification during the defined retention period.
* **📈 Growth and scalability:** the use of serverless and managed services allows the solution to accommodate increasing numbers of users and documents without relying on individually managed servers.
* **💰 Cost control:** S3 Lifecycle allows storage to adapt to the document lifecycle, keeping recent files available for frequent access and moving historical documents to lower-cost storage classes.
* **📤 Controlled file transfer:** pre-signed URLs allow customers to upload and download files directly to Amazon S3 without receiving permanent permissions or unrestricted access to the bucket.

In this way, the architecture transforms the main business challenges into technical decisions, seeking to balance **security, access, historical preservation, scalability, and cost sustainability**.

### 🔁 Main flow (real-time request)

The flow below represents the synchronous path of a user request, from login to document storage:

1. The user logs into the platform using **Amazon Cognito**.
2. After authentication, the user receives the tokens required to access the application.
3. Requests are sent to **Amazon API Gateway**, which acts as the API entry point.
4. **AWS Lambda** processes the request and applies the business rules.
5. When necessary, the function queries metadata in **Amazon DynamoDB** to validate document ownership and authorization.
6. After validation, the application generates a pre-signed URL for the requested operation in **Amazon S3**.
7. The user uploads or downloads the document directly from S3 using this temporary authorization and the service's standard endpoint.
8. Documents remain stored in a private bucket.

The document lifecycle management, including the transition to **S3 Glacier Deep Archive after 12 months** and protection through **S3 Object Lock**, is not part of this synchronous flow. These mechanisms have already been detailed in the [📦 Storage strategy](#-storage-strategy) and [🔏 Document preservation](#-document-preservation) sections.

In addition to the main flow, the architecture incorporates mechanisms for observability, auditing, access control, cost optimization, and Infrastructure as Code.

---

## Resilience and fault tolerance

In addition to security and scalability, the architecture was designed to reduce dependence on individual components that could represent single points of failure.

One of the main decisions in Phase 01 was to use an architecture based on **serverless services managed by AWS**. This means that the team does not need to depend on a single server, virtual machine, or instance to keep the application running.

The main components of the solution, such as **Amazon Cognito**, **Amazon API Gateway**, **AWS Lambda**, **Amazon DynamoDB**, and **Amazon S3**, are managed services operating on infrastructure provided by AWS.

Therefore, the application does not depend on a single Availability Zone manually configured by the team to execute its main flow. Responsibility for the underlying infrastructure and service availability is shared with AWS according to the characteristics and service-level agreements of each service.

### ⚠️ What happens if a component fails?

The architecture was designed to reduce the impact of failures related to individual infrastructure components. For example, there is no single EC2 instance responsible for processing all platform requests.

Application logic is executed by **AWS Lambda**, while documents and metadata are stored in managed services such as **Amazon S3** and **Amazon DynamoDB**. This approach reduces the risk that the failure of a single application-managed server will completely interrupt the system.

However, it is important to highlight that:

> **Resilience does not mean that the application is immune to every type of failure.**

Failures related to application logic, incorrect configurations, inadequate permissions, or service outages still need to be considered as the system evolves.

For this reason, the architecture incorporates **observability** mechanisms using **Amazon CloudWatch** and **auditing** through **AWS CloudTrail**, allowing problems to be identified and operational behavior to be monitored.

### 🌱 Resilience as part of the architecture's evolution

Phase 01 establishes a resilient foundation through the use of managed services and the reduction of single points of failure under the team's direct responsibility.

As the platform grows and its availability requirements become more demanding, additional mechanisms may be evaluated, such as advanced recovery strategies, data replication, and business continuity plans.

In this way, resilience is treated as a principle present from the conception of the solution, but also as an area that can evolve according to the business's criticality and scale.

---

## 🧭 Architecture, AWS CAF and AWS Well-Architected Framework

<p align="center">
  <img width="1376" height="768" alt="Image" src="https://github.com/user-attachments/assets/5ae1c337-4dae-42c0-8340-45ca05c827a4" />
</p>

The construction of the solution was guided by cloud architecture best practices, considering principles from the [AWS Cloud Adoption Framework (AWS CAF)](https://aws.amazon.com/pt/cloud-adoption-framework/) and the [AWS Well-Architected Framework](https://aws.amazon.com/pt/architecture/well-architected/).

AWS CAF helps analyze cloud adoption broadly, relating architecture to business needs, security, operations, and resource management. The AWS Well-Architected Framework provides technical principles for assessing whether an architecture is being built securely, reliably, efficiently, and sustainably.

The relationship between the architecture and these principles can be summarized as follows:

| Pillar                        | Focus                                                                                                   | AWS services involved                                                                                                                                                        | Contribution                                                                                                                                                                                                                                                                                                                                                                                                      |
| ----------------------------- | ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🔐 **Security**               | Authentication, permission control, and document ownership validation                                   | Amazon Cognito, AWS IAM, Amazon API Gateway, AWS Lambda, pre-signed URLs, Amazon S3 (server-side encryption)                                                                 | Ensures that access to data is controlled and limited to authorized operations. In Phase 02, AWS KMS may expand control over encryption keys.                                                                                                                                                                                                                                                                     |
| 🛡️ **Reliability**           | Reducing dependence on individual components, ensuring durable storage, and preserving document history | Amazon Cognito, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3, S3 Lifecycle, S3 Glacier Deep Archive, S3 Object Lock, Amazon CloudWatch, Infrastructure as Code | Relies on AWS-managed infrastructure, reducing single points of failure. Documents remain in Amazon S3 Intelligent-Tiering during the first 12 months and then move to Glacier Deep Archive, reducing costs without deleting them. S3 Object Lock protects against deletion or modification during retention, while CloudWatch monitors operational behavior and IaC ensures consistent environment reproduction. |
| ⚡ **Performance Efficiency**  | Meeting demand without relying on a single machine                                                      | Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3                                                                                                                   | Serverless and managed services provide a foundation capable of supporting application growth. Transfers are performed directly through Amazon S3 using pre-signed URLs.                                                                                                                                                                                                                                          |
| 💰 **Cost Optimization**      | Matching resources to real application behavior and data access patterns                                | S3 Lifecycle, S3 Glacier Deep Archive, serverless services                                                                                                                   | Recent documents remain in a frequent-access class and move to historical storage after 12 months. The architecture avoids adding services that do not address a concrete need in the current scenario.                                                                                                                                                                                                           |
| 📊 **Operational Excellence** | Monitoring, auditing, and infrastructure reproducibility                                                | Amazon CloudWatch, AWS CloudTrail, AWS CloudFormation                                                                                                                        | CloudWatch monitors logs, metrics, and alarms; CloudTrail records actions for auditing and governance; CloudFormation enables infrastructure provisioning and reproduction as code.                                                                                                                                                                                                                               |

---

## 💰 Project costs

<p align="center">
  <img width="1376" height="768" alt="Project cost estimate" src="https://github.com/user-attachments/assets/c5877632-d50d-452d-8545-5b1f6229f31a" />
</p>

The architecture was designed not only to meet Startup Jarva's technical requirements but also to keep costs compatible with the platform's growth.

Considering a scenario of approximately **50,000 new documents per month**, the Phase 01 estimate results in:

| Indicator                      |        Estimate |
| ------------------------------ | --------------: |
| 💵 **Recurring monthly cost**  |   **US$143.54** |
| 🧾 **Initial cost**            |    **US$33.00** |
| 📅 **12-month projection**     | **US$1,755.48** |
| 📄 **Cost per document/month** |   **US$0.0029** |

> 💡 **In other words:** the architecture can process approximately **50,000 documents per month** with a recurring cost below **US$0.003 per document**, demonstrating a low marginal cost per processed unit.

### 📊 Where is the cost concentrated?

Most of the cost is related to **document storage and data transfer**, rather than computing capacity.

* 🗄️ **Amazon S3 Intelligent-Tiering:** US$65.63/month
* 🌐 **Data transfer:** US$61.44/month
* ❄️ **S3 Glacier Deep Archive:** US$8.42/month
* 📊 **Amazon CloudWatch:** US$6.18/month
* ⚙️ **Other services:** less than 1% impact or an estimated cost of US$0.00 at the analyzed scale

This distribution reinforces one of the project's main architectural decisions: **costs should follow the lifecycle and behavior of the data**.

Recent documents remain in a layer suitable for frequent access, while historical documents can be directed to lower-cost long-term storage.

### 📈 Optimization strategy

The architecture avoids adding services or optimization mechanisms without a concrete need.

One example is **S3 Transfer Acceleration**. Although it can improve the transfer experience in geographically distributed scenarios, its adoption would significantly increase the estimated costs. Therefore, it was kept as a potential evolution for **Phase 02**, rather than a mandatory component of Phase 01.

> **The strategy is simple: add complexity and cost only when the platform's actual growth justifies the investment.**

### 📄 Pricing details

The complete estimate, including the assumptions used, read calculations, service costs, 12-month projection, free-tier levels, and analysis of the impact of S3 Transfer Acceleration, is available in the document:

👉 **[📄 AWS Services Pricing - Startup Jarva's](./AWS%20Services%20Pricing%20-%20Startup%20Jarva's.md)**

> *Estimate prepared based on the AWS Pricing Calculator, using the US East (N. Virginia) region. The values represent a projection based on the scenario assumptions and may vary according to actual application behavior and changes in AWS service prices.*

---

## 🚀 Evolution and Future Vision — Phase 02

The architecture presented in Phase 01 was developed to meet the main requirements of the proposed scenario, prioritizing security, customer isolation, scalability, resilience, document retention, cost optimization, observability, and infrastructure reproducibility.

As part of the solution's evolution, we identified several areas that could be improved in a second phase of the project.

These improvements are not necessary for the initial architecture to meet the defined requirements, but they represent opportunities to increase the platform's security, governance, resilience, performance, and operational maturity as the business grows.

Phase 02 does not represent a replacement for the current architecture. It builds upon the foundation created in Phase 01 and evaluates which new resources and strategies become meaningful as the number of users, document volume, operational criticality, and sensitivity of stored data increase.

### 🔐 Phase 02 — Security and Governance Evolution

The main objective of Phase 02 is to strengthen data protection and the management of sensitive information, complementing the security mechanisms already present in Phase 01.

The services evaluated for this stage are:

| Service                    | Objective in Phase 02                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| 🔑 **AWS KMS**             | Centralized management of encryption keys and greater control over data protection                                       |
| 🤫 **AWS Secrets Manager** | Secure storage and management of credentials, secrets, and sensitive information used by the application                 |
| 🔎 **Amazon Macie**        | Discovery and identification of sensitive data stored in Amazon S3, supporting information classification and protection |

The adoption of these services should be evaluated considering platform growth, the sensitivity level of stored documents, and the financial impact of their use.

Each resource should be incorporated when there is a concrete need that justifies its use, considering security, governance, operational complexity, and cost, rather than simply increasing the number of components in the architecture.

### ⚡ Phase 02 — Performance and Global Experience Evolution

Phase 01 uses the standard Amazon S3 endpoint for file transfers because the initial scenario does not establish geographic distance as a problem or mandatory requirement for the solution.

However, as Startup Jarva's grows, transfer behavior can be monitored to identify possible impacts related to user location, file size, and upload/download experience.

In this context, **S3 Transfer Acceleration** may be evaluated as a possible architectural evolution.

Its adoption would make more sense in scenarios such as:

* 🌎 international expansion of the platform;
* 📍 customers geographically distributed far from the bucket region;
* 📦 significant increases in transferred file sizes;
* 📈 substantial growth in transfer volume;
* 📊 identification, through metrics or user feedback, of experience degradation caused by geographic distance.

In this way, the service is no longer treated as a mandatory architecture component and instead becomes a **decision driven by actual performance requirements**.

> **The objective is not to add optimization mechanisms prematurely, but to evaluate their adoption when operational data demonstrates that the benefit justifies the additional cost.**

This approach keeps Phase 01 aligned with the current scenario and allows the architecture to evolve progressively as new requirements emerge.

### 🚀 How can the solution evolve?

The platform's evolution can be analyzed through several important questions:

* How could the solution support a significantly larger volume of users and documents?
* How can data protection be strengthened as the amount and sensitivity of information increase?
* How can the presence of sensitive information in stored documents be automatically identified and monitored?
* How can the management of credentials and confidential information used by the application be improved?
* How can control over the keys used to protect data be increased?
* How can the impact of failures and outages affecting critical solution components be further reduced?
* How can recovery and continuity strategies be established if platform availability requirements become more stringent?
* How can a good transfer experience be maintained if the platform begins serving customers distributed globally?
* How can platform growth remain sustainable without increasing costs disproportionately?

Phase 02 therefore represents a natural evolution of the architecture, in which additional security, governance, performance, and resilience mechanisms can be incorporated as business requirements become more complex.

### 📈 Future vision

In a scenario of Startup Jarva's growth, the architecture may evolve to support a larger volume of users, documents, and processing while maintaining the principles that guided the solution from its conception.

Possible evolution paths include:

* **🔑 Greater cryptographic protection:** use of AWS KMS to expand control over encryption keys and data protection mechanisms.
* **🤫 Sensitive information management:** use of AWS Secrets Manager to centralize and protect credentials and other secrets used by the application.
* **🔎 Sensitive data discovery:** use of Amazon Macie to identify and classify potentially sensitive information stored in Amazon S3.
* **⚡ Global performance evolution:** evaluation of S3 Transfer Acceleration if the platform's geographic expansion or actual transfer behavior justifies the additional investment.
* **🛡️ Greater resilience:** evaluation of additional recovery and business continuity mechanisms as platform availability requirements and criticality increase.
* **📜 Greater governance:** expansion of auditing, monitoring, and control mechanisms as the platform grows.
* **📈 Scalability:** evolution of the architecture to support a significant increase in users and documents without depending on individual components that limit growth.
* **💰 Cost optimization:** continuous review of storage strategies and service usage according to actual application behavior.

These improvements do not necessarily need to be implemented in the first version of the solution. The objective of this stage is to demonstrate that the architecture was designed not only to meet the current scenario but also to allow consistent evolution as the business grows.

> **Phase 01 solves the current problem. Phase 02 prepares the architecture for the challenges that emerge as the platform grows and matures.**

---

# 6. How the project was developed

<p align="center">
  <img width="1905" height="1065" alt="Agile project management flow" src="https://github.com/user-attachments/assets/9b9cb4cf-11d1-4d90-8950-c318547d43de" />
</p>

The project was developed using an **agile management** approach, combining **Scrum**, **Kanban**, and **PDCA** to organize activities, monitor solution evolution, and promote continuous cycles of analysis, development, and review.

Because the project involved not only building a technical architecture but also analyzing the business problem, gathering requirements, evaluating AWS services, and preparing documentation, each of these practices contributed to a different dimension of the process.

## 🏃 Weekly Sprints (Scrum)

The work was organized into **weekly Sprints**, during which the main objectives for each cycle were defined. Periodic meetings monitored task progress, discussed challenges, aligned decisions, and reviewed deliverables.

This organization allowed an initially broad problem to be divided into smaller and progressive deliverables. Instead of defining the entire architecture at once, decisions matured as the team deepened its understanding of the problem, requirements, and possibilities offered by AWS services.

## 🗂️ Kanban Board

The workflow was visualized through a **Kanban board in Trello**, with activities organized into stages — **To Do, In Progress, In Review, and Done**. The board also centralized contextual notes, planning, and suggestions, giving the team a shared view of what needed to be done, what was in progress, and what had already been completed.

## 🔄 PDCA and continuous improvement

Complementing the Sprints, we applied the **PDCA (Plan, Do, Check, Act)** cycle to continuously evaluate and improve decisions:

1. **Plan:** identify priorities and define the objectives for the cycle.
2. **Do:** execute the planned activities.
3. **Check:** review results and decisions, identifying areas for improvement.
4. **Act:** incorporate lessons learned and adjust the next planning cycle.

This cycle was essential because several architectural decisions matured throughout the project. As requirements analysis progressed, new needs and improvement opportunities were identified and incorporated.

## 🔗 How the approaches connect

**Scrum** provided structure to the work cycles, **Kanban** brought visibility to the activity flow, and **PDCA** ensured continuous evaluation and improvement of the process:

**Planning → Sprint → Execution → Review → Adjustments → Next Sprint**

This combination balanced organization and flexibility. There were clear objectives for each cycle while still allowing decisions to be reviewed as new aspects of the problem emerged.

## 🧭 Decision management and architecture evolution

Decisions were not treated as isolated technical tasks. Each choice was related to project requirements, business needs, and aspects such as **security, scalability, resilience, availability, retention, and costs**. The evolution followed a progressive flow:

**Problem understanding → Requirements gathering → Alternative analysis → Solution definition → Review → Architecture evolution**

This process also allowed us to distinguish what was necessary to meet the requirements of **Phase 01** from what could be incorporated later as part of the platform's evolution.

One example of this process was the analysis of **S3 Transfer Acceleration**. Initially considered as an alternative for optimizing file transfers, the service was reassessed based on the actual requirements of the scenario and its impact on solution costs. Since there was no requirement related to global transfer or evidence of performance problems caused by geographic distance, we chose to keep Phase 01 using the standard Amazon S3 endpoint and pre-signed URLs.

Resources such as **AWS KMS, AWS Secrets Manager, Amazon Macie**, and additional performance optimization mechanisms were reserved for potential future evolution, avoiding unnecessary complexity and cost in the initial architecture without a concrete need to justify them.

## ✅ Result of the management approach

The combination of **Scrum, Kanban, and PDCA** allowed the team to monitor solution evolution, review decisions, and incorporate improvements incrementally and collaboratively — resulting in a process where **management and architecture evolved together**.

> **The project was not developed as a linear sequence of decisions. It evolved through cycles of planning, execution, review, and continuous improvement, allowing the solution to mature alongside the team's understanding of the problem.**

---

# 7. Infrastructure as Code

The solution's infrastructure was developed following the **Infrastructure as Code (IaC)** concept, allowing the resources required for the architecture to be defined and provisioned through code.

This approach helps make the infrastructure **reproducible, consistent, and version-controlled**, reducing dependence on manual configurations and making it easier to create environments with the same architectural structure.

For this project, the infrastructure was implemented using **AWS CloudFormation**, through a template that describes the resources and their configurations. The model's development also considered the [official AWS best practices](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/best-practices.html), including aspects related to template creation, stack management, and access control through AWS IAM.

In this way, the architecture no longer exists only as a conceptual diagram and can instead be represented and provisioned in a structured manner through code.

### 🔗 Access the infrastructure code

[![View infrastructure.yaml](https://img.shields.io/badge/CloudFormation-infrastructure.yaml-527FFF?style=for-the-badge\&logo=amazonaws\&logoColor=white)](https://github.com/lbarretto/jarvas-aws-architecture/blob/main/infrastructure.yaml)

---

# 8. 🎬 Presentation Video

To complement the written documentation, we recorded a project presentation video in which we explain the challenge context, the main problems identified, and the proposed solution architecture.

<div align="center">

[![Watch the presentation video](https://img.shields.io/badge/▶️-Watch%20on%20YouTube-FF0000?style=for-the-badge\&logo=youtube\&logoColor=white)](https://youtu.be/4kUy7GKyM3A)

</div>

---

# 9. Acknowledgments

This project was collaboratively developed as part of a learning journey and the practical application of knowledge acquired during our preparation in cloud computing.

We would like to thank **Escola da Nuvem**, the instructors, mentors, and all team members who contributed analyses, ideas, and different perspectives throughout the development of the project.

<p align="center">
  <em><img width="1196" height="892" alt="Image" src="https://github.com/user-attachments/assets/7d9b668e-a836-4cfd-a797-54402378410d" /></em>
</p>

---

# 10. References

**1. Amazon S3 — Block Public Access**
Public access blocking configurations and how these settings can prevent policies or permissions that would allow public access to objects.

**2. Amazon S3 — Pre-signed URLs**
Official documentation on pre-signed URLs and how to provide temporary and controlled access to objects stored in Amazon S3.

**3. AWS re:Post — Prefix-based access**
Official example of an IAM policy using the `s3:prefix` condition and identity variables to restrict users to their own prefixes within a shared bucket.

**4. Amazon S3 — Object lifecycle management**
Official documentation on S3 Lifecycle rules and the transition of objects between different storage classes, including historical and long-term storage scenarios.

**5. Amazon API Gateway — Features**
Documentation on the role of API Gateway as an API publishing layer, integration with AWS Lambda, traffic control, and security and monitoring features.

**6. AWS Lambda**
Official documentation on the serverless execution model, event-driven execution, integration with other AWS services, and usage-based billing.

**7. G1 Technology — News report**
Shanghai Police case (2022): claim of exposure of records associated with approximately 1 billion citizens due to a possible configuration failure in a data infrastructure.

The case is used exclusively to contextualize the risk associated with unintended data exposure and not as technical proof of an exposure at that scale.

**8. IBM — Cost of a Data Breach Report 2026**
IBM's annual report on costs, causes, and impacts related to data breaches, used as a reference to contextualize risks associated with information security and the evolution of Artificial Intelligence.

**9. Gartner — Worldwide AI Spending**
Gartner projections regarding the growth of global investments in Artificial Intelligence and the increasing importance of the infrastructure required to support these solutions.

---

<div align="center">

**☁️ Startup Jarva's**
AI-Powered Document Management SaaS Platform

[![Back to top](https://img.shields.io/badge/⬆-Back%20to%20top-lightgrey?style=flat-square)](#-startup-jarvas)

</div>
