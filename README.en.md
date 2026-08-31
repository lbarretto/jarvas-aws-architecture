<div align="center">

# ☁️ Startup Jarva's
### AI-Powered Document Management SaaS Platform

<img width="1672" height="940" alt="Project cover - Startup Jarva's" src="https://github.com/user-attachments/assets/dc2e1360-263c-47af-b3fc-912f140d9fa7" />

<br/>

[![🇧🇷 Português](https://img.shields.io/badge/🇧🇷-Português-lightgrey?style=for-the-badge)](./README.md)
[![🇺🇸 English](https://img.shields.io/badge/🇺🇸-English-009c3b?style=for-the-badge)](./README.en.md)

<br/>

[![AWS](https://img.shields.io/badge/AWS-Cloud%20Architecture-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)](#5-solution)
[![Serverless](https://img.shields.io/badge/Architecture-Serverless-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)](#5-solution)
[![IaC](https://img.shields.io/badge/IaC-CloudFormation-527FFF?style=for-the-badge&logo=amazonaws&logoColor=white)](#7-infrastructure-as-code)
[![Status](https://img.shields.io/badge/Phase%2001-Completed-brightgreen?style=for-the-badge)](#5-solution)
[![Phase 02](https://img.shields.io/badge/Phase%2002-Planned-lightgrey?style=for-the-badge)](#-evolution-and-future-vision--phase-02)

[![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=flat-square&logo=amazons3&logoColor=white)](#-aws-services-used)
[![AWS Lambda](https://img.shields.io/badge/AWS%20Lambda-FF9900?style=flat-square&logo=awslambda&logoColor=white)](#-aws-services-used)
[![Amazon DynamoDB](https://img.shields.io/badge/Amazon%20DynamoDB-4053D6?style=flat-square&logo=amazondynamodb&logoColor=white)](#-aws-services-used)
[![Amazon Cognito](https://img.shields.io/badge/Amazon%20Cognito-DD344C?style=flat-square&logo=amazoncognito&logoColor=white)](#-aws-services-used)
[![API Gateway](https://img.shields.io/badge/Amazon%20API%20Gateway-FF4F8B?style=flat-square&logo=amazonapigateway&logoColor=white)](#-aws-services-used)
[![CloudFormation](https://img.shields.io/badge/AWS%20CloudFormation-527FFF?style=flat-square&logo=amazonaws&logoColor=white)](#7-infrastructure-as-code)

*Project developed as part of a challenge proposed by **Escola da Nuvem** for the practical application of AWS Cloud knowledge and cloud solutions architecture.*

</div>

---

<details open>
<summary><h2>📌 Table of Contents</h2></summary>

- [1️⃣ Capstone Project Context](#1-capstone-project-context)
  - [1.1 💡 What is the project?](#-what-is-the-project)
  - [1.2 📊 Why do we believe this is a relevant topic?](#-why-do-we-believe-this-is-a-relevant-topic)

- [2️⃣ Project Context](#2-project-context)

- [3️⃣ Problem to be solved and business impact](#3-problem-to-be-solved-and-business-impact)
  - [3.1 🔒 Data security and isolation](#-data-security-and-isolation)
  - [3.2 🗃️ Document retention](#️-document-retention)
  - [3.3 💵 Storage cost](#-storage-cost)
  - [3.4 ⚖️ The central dilemma](#️-the-central-dilemma)

- [4️⃣ Project and solution requirements](#4-project-and-solution-requirements)

- [5️⃣ Solution](#5-solution)
  - [5.1 🧩 From need to solution](#-from-need-to-solution)
  - [5.2 🔭 Solution overview](#-solution-overview)
  - [5.3 🛠️ AWS services used](#️-aws-services-used)
  - [5.4 🚶 Customer Journey](#-customer-journey)
  - [5.5 🏗️ AWS Architecture](#️-aws-architecture)
  - [5.6 🛡️ Resilience and fault tolerance](#resilience-and-fault-tolerance)
  - [5.7 🧭 Architecture, AWS CAF and AWS Well-Architected Framework](#-architecture-aws-caf-and-aws-well-architected-framework)
  - [5.8 💰 Project costs](#-project-costs)
  - [5.9 🚀 Evolution and Future Vision — Phase 02](#-evolution-and-future-vision--phase-02)

- [6️⃣ How the project was developed](#6-how-the-project-was-developed)

- [7️⃣ Infrastructure as Code](#7-infrastructure-as-code)

- [8️⃣ Presentation Video](#8--presentation-video)

- [9️⃣ Acknowledgments](#9-acknowledgments)

- [🔟 References](#10-references)

</details>

---

# 1. Capstone Project Context

## 💡 What is the project?

This project was developed as part of a challenge proposed by **Escola da Nuvem**, aiming to reinforce, in practice, the knowledge acquired about cloud computing and, above all, how AWS services can be used to solve real business problems.

The challenge represents an opportunity to move beyond a purely conceptual approach and apply the knowledge studied during our preparation for the **AWS Certified Cloud Practitioner** certification to the analysis and construction of an architectural solution.

More than simply selecting AWS services, the goal of the project is to understand the problem presented, identify its needs and constraints, and, from there, evaluate how different cloud resources can add value to the business.

This approach also led us to realize that the project involves much more than file storage. Documents have a life cycle, different levels of usage over time, security requirements, and strategic value for the business.

As a result, decisions related to the organization, access, retention, and cost of data become part of the solution's architecture itself.

## 📊 Why do we believe this is a relevant topic?

The topic becomes especially relevant when we consider the growth in the use of Artificial Intelligence and the importance of the data that fuels these solutions.

In the proposed scenario, the documents submitted by clients represent the historical base used for the future evolution of the company's AI models.

Therefore, ensuring that this data is organized, protected, available when needed, and economically sustainable over time is a fundamental part of the business strategy.

Additionally, the proposed scenario is set within a context of significant growth in the Artificial Intelligence market.

As identified during the scenario analysis:

> 📈 According to a projection by the consulting firm Gartner, global investment in artificial intelligence is expected to reach US$2.59 trillion in 2026, a 47% increase over the previous year, with expectations of nearly US$3.5 trillion by 2027.
>
> 🇧🇷 In Brazil, an IBM study showed that 78% of national companies plan to expand their AI investments, and AI spending in the country is expected to exceed US$2.4 billion, a 30% increase compared to 2024.
>
> 🎯 Strategic adoption has also surged: 95.2% of organizations consider AI a strategic priority for 2026, compared to only 32.8% that invested in the technology in 2024.
>
> 🏗️ About 45% of all investment projected for 2026 is related to AI infrastructure, including components such as cloud storage, processing, and data pipelines.

This data helps contextualize why an architecture focused on storing and managing data for AI applications is relevant. The growth in Artificial Intelligence investments also increases the importance of the infrastructure needed to support these solutions.

In the case of Startup Jarva's, this relationship is particularly important because the documents received by the platform represent exactly the historical raw material that can be used to train and evolve future AI models.

> **All of this AI evolution depends on something fundamental: data that is well stored, organized, protected, and available for use. There is no quality AI without an adequate historical data foundation behind it.**

The project, therefore, represents an increasingly relevant problem:

> **How do you build an infrastructure capable of turning growing data volumes into a strategic asset, without compromising security, availability, and financial sustainability?**

<p align="center">
  <img width="1376" height="768" alt="Context of AI growth" src="https://github.com/user-attachments/assets/cf38ec2f-b4db-4055-991c-67868188a3ac" />
</p>

---

# 2. Project Context

**Startup Jarva's** is a hyper-growth company that offers a SaaS platform focused on **intelligent data extraction using Artificial Intelligence**.

As part of this service, the platform receives documents submitted by clients, mainly **PDFs and images**, which serve as input for the AI processing.

The projected volume is approximately **50,000 new files per month**, equivalent to about **600,000 files per year**, with a trend of continuous growth.

The scenario has a characteristic that completely changes how the problem must be addressed:

> **Files cannot be deleted.**

Old documents continue to have value because they represent the historical record used as the basis for training future Artificial Intelligence models.

Therefore, as the company grows, the amount of data also grows continuously.

Within a few years, the platform could accumulate millions of documents. This history represents not just a large amount of data, but an intellectual asset that can directly contribute to the evolution of the company and its AI models.

That is precisely why we understand that Startup Jarva's is not simply building a document repository:

> **A repository preserves information. A data asset preserves information with the intention of generating value from it.**

This shift in perspective is fundamental to understanding the rest of the project. Storage stops being just supporting infrastructure and becomes part of the product strategy itself.

---

# 3. Problem to be solved and business impact

Startup Jarva's problem is the result of a combination of **accelerated growth, the need for isolation between clients, permanent document retention, and control of storage costs**.

## 🔒 Security and data isolation

The platform has a **multi-tenant** nature, meaning different clients use the same application and its infrastructure.

This creates a fundamental need:

> **One client must not have access to documents belonging to another client.**

Users need to be able to access their own documents quickly and securely, without a configuration, permission, or implementation flaw allowing other users' files to be exposed.

This need for isolation must be considered from the very start of the architecture, not addressed later as a fix.

The risk associated with this problem is not merely theoretical. The project's foundational document itself uses a real case to contextualize the impact that an inadequate configuration can cause:

> ⚠️ In 2022, a hacker claimed to have obtained data on about one billion Chinese citizens from an Elasticsearch deployment associated with a government agency. The report itself raised doubts about the accuracy and scale of the claim, so the case should not be treated as a proven exposure at that scale.
>
> The example is used to contextualize the risk associated with inadequate infrastructure configurations and improper data exposure.

The value of the example lies in demonstrating the type of risk that Startup Jarva's needs to avoid:

> **An inadequate configuration or deployment can turn infrastructure that should protect data into a gateway to access it.**

This is especially relevant for Startup Jarva's because the platform will depend on the trust of clients who will be handing over their own documents to the service.

A data exposure incident would compromise client trust in the platform and, consequently, the company's own value proposition. For this reason:

> **Security should not be a layer added later. It needs to be part of the architecture from the very first file received by the platform.**

---

## 🗃️ Document retention

Unlike systems where old data can be discarded, Startup Jarva's has a different strategic requirement:

> **No file should be deleted as part of the platform's normal operation.**

The documents represent the historical base that can be used to train future AI models. The fact that a document is old does not mean it has lost its value — on the contrary, it becomes part of the company's historical data assets.

In numbers, the scenario predicts approximately **50,000 files per month**, equivalent to about **600,000 files per year**.

Since no file is discarded as part of normal operation, this volume will continue to grow over time, potentially reaching millions of documents after a few years of operation.

---

## 💵 Storage cost

Permanent retention creates a second problem.

If approximately 50,000 files are added every month and none of them are removed, the stored volume will keep growing indefinitely.

Keeping all these documents permanently in a storage class geared toward frequent access could generate a cost incompatible with the company's growth.

For this reason, the project needs to consider the **data life cycle**.

Recent documents have a higher access frequency and need immediate availability, while historical documents tend to be accessed less frequently, even though they continue to hold strategic value.

In the proposed architecture, documents initially remain in **Amazon S3 Intelligent-Tiering**, suited to the period of highest access frequency.

After the first **12 months**, an **S3 Lifecycle** rule can automatically transition the objects to **S3 Glacier Deep Archive**, reducing the storage cost of historical documents that still need to be preserved.

This strategy allows the storage cost to track the data's expected behavior over time.

---

## ⚖️ The central dilemma

Based on these problems, we identified four needs that must be met simultaneously:

1. **⚡ Fast access:** clients need normal access to documents during the first 12 months.
2. **🗃️ Permanent retention:** no file should be deleted as part of the platform's normal operation, since all of them are part of the company's historical asset.
3. **💵 Cost under control:** older documents should stop occupying a frequent-access storage class once access becomes less frequent.
4. **🔒 Isolation and security:** each document belongs to a specific client and cannot be accessed by other clients.

It is precisely the combination of these needs that makes the problem more interesting.

Startup Jarva's cannot simply choose the cheapest alternative, because that could harm document access. Likewise, it cannot keep the entire history permanently in a frequent-access storage class, because the cost would grow along with the historical base. Nor can it prioritize ease of access alone without considering isolation between clients.

The challenge, therefore, is not simply finding a place to store millions of documents.

> **The real challenge is balancing security, access, retention, and cost throughout the entire data life cycle.**

This is the question the architecture needs to answer.

---

# 4. Project and solution requirements

Based on the scenario presented and the problems identified, we established the requirements the solution needs to meet.

### 🔐 Security

The solution must guarantee **isolation between clients**, preventing one user from accessing documents belonging to another.

Access to documents must be controlled and restricted to the authorized owner.

### 📈 Scalability

The solution must support the platform's continuous growth and the ingestion of approximately **50,000 new files per month**, without depending on a single machine or an infrastructure that needs to be manually scaled with each increase in demand.

### 🛡️ Durability and retention

Historical documents must not be deleted by the application as part of normal operation.

The solution must allow files to remain preserved even when they are no longer accessed frequently.

### ⚡ Availability and access

Documents submitted by clients must remain available for retrieval during the period when they have the highest access frequency, especially during the first 12 months.

### 💰 Cost-efficiency

Storage cost must decrease as documents age.

The solution must allow files to remain preserved without requiring the entire history to remain permanently in a frequent-access storage class.

### 📊 Operations and monitoring

The infrastructure must allow the solution's operation to be tracked, failures to be identified, and an audit trail of actions taken to be maintained.

### 🔄 Reproducibility

The infrastructure must be able to be recreated consistently, allowing the architecture to be documented and reproduced through code.

### 🧱 Resilience and fault tolerance

The solution must avoid dependencies on individual servers or components whose unavailability could completely interrupt the platform's operation.

Whenever possible, the architecture should use managed services capable of offering high availability as part of their operation, reducing the need for manual infrastructure management.

Additionally, the solution must be able to continue preserving documents and keeping core services available even in the face of isolated failures in components or the underlying infrastructure.

---

# 5. Solution

<details>
<summary><h3>🗂️ Quick index for Section 5</h3></summary>

- 5.1 🧩 [From need to solution](#-from-need-to-solution)
- 5.2 🔭 [Solution overview](#-solution-overview)
- 5.3 🛠️ [AWS services used](#-aws-services-used)
- 5.4 🚶 [Customer Journey](#-customer-journey)
- 5.5 🏗️ [AWS Architecture](#-aws-architecture)
- 5.6 🛡️ [Resilience and fault tolerance](#resilience-and-fault-tolerance)
- 5.7 🧭 [Architecture, AWS CAF and AWS Well-Architected Framework](#-architecture-aws-caf-and-aws-well-architected-framework)
- 5.8 💰 [Project costs](#-project-costs)
- 5.9 🚀 [Evolution and Future Vision — Phase 02](#-evolution-and-future-vision--phase-02)

</details>

## 🧩 From need to solution

Based on these requirements, it becomes clear that Startup Jarva's challenge is not just about storing a large volume of documents.

The architecture needs to keep pace with the company's growth, protect each client's data, preserve the historical record as a strategic asset, and, at the same time, keep costs under control.

It is from these needs that we arrived at this project's architectural proposal.

The choice of AWS services, therefore, does not stem from the technology itself, but from the problems that need to be solved and the requirements the solution must meet.

The proposal developed uses a **serverless** architecture, based on managed AWS services, reducing the need for infrastructure management and allowing the solution to keep pace with the platform's demand.

The architecture also separates important system responsibilities:

- 🔑 Authentication
- 🛂 Access control
- ⚙️ Business logic
- 🗄️ Document storage
- 🏷️ Metadata management
- 👀 Observability
- 📜 Auditing
- ♻️ Data life cycle management
- 🧱 Infrastructure provisioning

---

## 🔭 Solution overview

The solution was designed to allow clients to submit and access their documents securely, without receiving direct or unrestricted access to the storage environment.

The flow begins with user authentication through **Amazon Cognito**. After authentication, requests are routed to **Amazon API Gateway** and processed by **AWS Lambda**, which is responsible for applying business rules and validating the necessary permissions.

Document metadata and ownership information are stored in **Amazon DynamoDB**, allowing verification of whether the user is authorized to access a given file.

Documents are stored in a private **Amazon S3** bucket. After permission validation, access is granted through **temporary, pre-signed URLs**, limited to the requested operation and a specific time window.

This way, the solution contributes to **isolation between clients**, avoids public exposure of documents, and ensures that each user only has access to the files they are authorized to use.

### 📤 File access strategy

In Phase 01, uploads and downloads are performed directly through the **standard Amazon S3 endpoint**, using pre-signed URLs generated by the application.

This approach allows the client to transfer files directly to S3 without the content needing to pass through API Gateway or AWS Lambda, reducing intermediate processing while keeping access controlled by the application.

The use of pre-signed URLs ensures that the user receives authorization only to perform the specific requested operation, within a limited time period.

This way, the architecture meets the requirement for secure document transfer without adding acceleration mechanisms that are not necessary for the current scenario.

### 📦 Storage strategy

During the first **12 months**, documents remain in **Amazon S3 Intelligent-Tiering**, meeting the requirement for frequent access and immediate availability.

After that period, an **S3 Lifecycle** rule can automatically transition the objects to **S3 Glacier Deep Archive**.

This class is suitable for long-term storage of data that needs to be preserved but has low access frequency.

The transition reduces storage costs without eliminating historical documents.

### 🔏 Document preservation

**S3 Object Lock** helps protect objects against deletion or modification during the configured retention period.

Retention settings should be defined according to Startup Jarva's business requirements.

This way, Object Lock acts as an additional layer of document protection, while S3 Lifecycle is responsible for the strategy of transitioning between storage classes.

### 🔑 Encryption

Objects stored in Amazon S3 are protected with **server-side encryption**, using the default encryption offered by the service.

In a future evolution, **AWS KMS** could be incorporated to provide greater control over encryption keys and their respective access policies.

The result is an architecture that seeks to balance **security, scalability, resilience, historical preservation, user experience, and cost sustainability**.

By using managed and serverless services, the solution also reduces dependency on individual components managed by the team, benefiting from the availability and fault-tolerance mechanisms offered by the AWS services used.

---

## 🛠️ AWS services used

| Service | Role in the solution |
|---|---|
| 🔑 **Amazon Cognito** | Authentication and identity management for users, including issuing JWT tokens used to control access to the application |
| 🚪 **Amazon API Gateway** | API entry layer, responsible for receiving requests, validating authorization, and integrating with application logic |
| ⚙️ **AWS Lambda** | Execution of business logic, identity and permission validation, metadata lookups, and generation of pre-signed URLs |
| 🏷️ **Amazon DynamoDB** | Storage of metadata and document ownership information, supporting access and authorization validation |
| 🗄️ **Amazon S3 Intelligent-Tiering** | Storage class used for documents during the initial period of frequent access, automatically adjusting access tiers based on usage patterns |
| ♻️ **S3 Lifecycle** | Life cycle management of documents and automatic transition of objects to more suitable storage classes over time |
| ❄️ **S3 Glacier Deep Archive** | Long-term historical storage for documents that need to be preserved but have low access frequency |
| 🔒 **S3 Object Lock** | Protection of objects against deletion or modification during the configured retention period |
| 🛂 **AWS IAM** | Permission control following the principle of least privilege across the architecture's services and resources |
| 📊 **Amazon CloudWatch** | Operational monitoring through logs, metrics, dashboards, and alarms |
| 📜 **AWS CloudTrail** | Logging and auditing of actions performed on the account and AWS services |
| 💰 **AWS Budgets** | Definition and tracking of budgets, enabling the creation of alerts related to infrastructure costs |
| 📈 **AWS Cost Explorer** | Analysis of costs and service usage patterns, supporting the identification of trends and optimization opportunities |
| 🧱 **AWS CloudFormation** | Provisioning, reproduction, and standardization of infrastructure through code |
---

## 🚶 Customer Journey

The technical architecture shows how the services connect. However, to understand the solution from the perspective of those who use the platform, we also developed a view focused on the **Customer Journey**.

This journey represents the path taken by the user, from accessing the platform to the historical preservation of their documents.

<p align="center">
  <img width="1536" height="1024" alt="Customer Journey - AI-Powered Document Management SaaS Platform" src="https://github.com/user-attachments/assets/205a90b4-dfd8-44de-83bf-c4a7f09828fc" />
</p>

The journey was organized into three main moments:

### 1. 📥 Access and submission

The client accesses the platform, authenticates, and submits a document for processing by the application.

At this stage, the goal is to provide a simple user experience without compromising security or the correct identification of document ownership.

### 2. 🔐 Protection and use

After submission, the document is associated with the client's account and stored securely.

When the user wants to view or download a file, the platform verifies their identity and permissions before granting access. The client does not receive unrestricted access to the storage environment. Access is granted only to the requested document, in a controlled manner.

### 3. 🗄️ Historical preservation

Over time, documents remain preserved as part of the company's history.

During the first 12 months, files remain in a class suited to frequent access. After that period, the life cycle strategy allows transitioning to a lower-cost historical storage class, keeping documents preserved for future business needs.

This view reinforces one of the project's core principles:

> **Security and data preservation must be present throughout the entire customer journey, not just at the moment of storage.**

---

## 🏗️ AWS Architecture

The technical view of the solution presents the AWS services used and the main communication flow between the architecture's components.

<p align="center">
  <img width="1530" height="1028" alt="Image" src="https://github.com/user-attachments/assets/45bfedc5-69a8-448e-8bc6-2924ac69a226" />
</p>

### 🔍 How does the architecture solve the problem?

The architecture was designed to directly address the main challenges identified by Startup Jarva's.

- **🔒 Security and isolation:** authentication via Amazon Cognito, validations performed by the application, and the use of pre-signed URLs allow document access to be controlled without directly exposing the storage environment.
- **🗃️ Retention and historical preservation:** Amazon S3 provides a durable foundation for document storage, while S3 Object Lock helps protect documents against deletion or modification during the defined retention period.
- **📈 Growth and scalability:** the use of serverless and managed services allows the solution to keep pace with an increasing number of users and documents without depending on servers individually managed by the team.
- **💰 Cost control:** S3 Lifecycle allows storage to adapt to the document life cycle, keeping recent files available for frequent access and moving historical documents to lower-cost classes.
- **📤 Controlled file transfer:** pre-signed URLs allow clients to upload and download files directly to Amazon S3, without receiving permanent permissions or unrestricted access to the bucket.

This way, the architecture turns the main business challenges into technical decisions, seeking to balance **security, access, historical preservation, scalability, and cost sustainability**.

### 🔁 Main flow (real-time request)

The flow below represents the synchronous path of a user request, from login to document storage:

1. The user logs into the platform using **Amazon Cognito**.
2. After authentication, the user receives the tokens needed to access the application.
3. Requests are sent to **Amazon API Gateway**, which acts as the API's entry point.
4. **AWS Lambda** processes the request and applies business rules.
5. When necessary, the function queries metadata in **Amazon DynamoDB** to validate ownership and authorization related to the document.
6. After validation, the application generates a pre-signed URL for the requested operation on **Amazon S3**.
7. The user performs the upload or download directly on S3 using this temporary authorization and the standard service endpoint.
8. Documents remain stored in a private bucket.

Document life cycle management, including the transition to **S3 Glacier Deep Archive after 12 months** and protection via **S3 Object Lock**, is not part of this synchronous flow. These mechanisms were already detailed in the [📦 Storage strategy](#-storage-strategy) and [🔏 Document preservation](#-document-preservation) sections.

In addition to the main flow, the architecture incorporates mechanisms for observability, auditing, access control, cost optimization, and infrastructure as code.

---

## Resilience and fault tolerance

Beyond security and scalability, the architecture was also designed to reduce dependency on individual components that could represent single points of failure.

One of Phase 01's main decisions was to use an architecture based on **serverless services managed by AWS**. This means the team does not need to depend on a single server, virtual machine, or instance to keep the application running.

The solution's main components, such as **Amazon Cognito**, **Amazon API Gateway**, **AWS Lambda**, **Amazon DynamoDB**, and **Amazon S3**, are managed services that run on infrastructure provided by AWS.

As a result, the application does not depend on a single Availability Zone manually configured by the team to run its main flow. Responsibility for the underlying infrastructure and service availability is shared with AWS according to the characteristics and service level agreements of each service.

### ⚠️ What happens if a component fails?

The architecture was designed to reduce the impact of failures related to individual component infrastructure. For example, there is no single EC2 instance responsible for processing all platform requests.

Application logic runs on **AWS Lambda**, while documents and metadata are stored in managed services such as **Amazon S3** and **Amazon DynamoDB**. This approach reduces the risk that the failure of a single server managed by the application could completely interrupt the system.

However, it is important to note that:

> **Resilience does not mean the application is immune to any type of failure.**

Failures related to application logic, incorrect configurations, inadequate permissions, or unavailability of external services still need to be considered as the system evolves.

For this reason, the architecture incorporates **observability** mechanisms using **Amazon CloudWatch**, and **auditing** mechanisms using **AWS CloudTrail**, allowing issues to be identified and the solution's operational behavior to be tracked.

### 🌱 Resilience as part of the architecture's evolution

Phase 01 establishes a resilient foundation through the use of managed services and the reduction of single points of failure under the team's direct responsibility.

As the platform grows and its availability requirements become more demanding, new mechanisms can be evaluated, such as advanced recovery strategies, data replication, and business continuity plans.

This way, resilience is treated as a principle present since the solution's conception, but also as an area that can evolve according to the business's criticality and scale.

---

## 🧭 Architecture, AWS CAF and AWS Well-Architected Framework

<p align="center">
  <img width="1376" height="768" alt="Image" src="https://github.com/user-attachments/assets/5ae1c337-4dae-42c0-8340-45ca05c827a4" />
</p>

The solution was built following cloud architecture best practices, taking into account the principles of the [AWS Cloud Adoption Framework (AWS CAF)](https://aws.amazon.com/architecture/well-architected/) and the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/).

AWS CAF helps analyze cloud adoption broadly, relating the architecture to business needs, security, operations, and resource management. The AWS Well-Architected Framework, in turn, offers technical principles to assess whether the architecture is being built securely, reliably, efficiently, and sustainably.

The relationship between the architecture and these principles can be summarized as follows:

| Pillar | Focus | AWS services involved | How it contributes |
|---|---|---|---|
| 🔐 **Security** | Authentication, permission control, and document ownership validation | Amazon Cognito, AWS IAM, Amazon API Gateway, AWS Lambda, pre-signed URLs, Amazon S3 (server-side encryption) | Ensures that data access is controlled and limited to authorized operations. In Phase 02, AWS KMS could expand control over encryption keys. |
| 🛡️ **Reliability** | Reducing dependency on individual components, ensuring durable storage, and preserving document history | Amazon Cognito, Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3, S3 Lifecycle, S3 Glacier Deep Archive, S3 Object Lock, Amazon CloudWatch, infrastructure as code | Relies on AWS-managed infrastructure, reducing single points of failure. Documents stay in Amazon S3 Intelligent-Tiering for the first 12 months and then migrate to Glacier Deep Archive, cutting costs without eliminating them. S3 Object Lock protects against deletion or modification during retention, while CloudWatch monitors operational behavior and IaC ensures consistent environment reproduction. |
| ⚡ **Performance efficiency** | Keeping up with demand without depending on a single machine | Amazon API Gateway, AWS Lambda, Amazon DynamoDB, Amazon S3 | Serverless and managed services provide a foundation capable of keeping up with application growth. Transfers are performed directly with Amazon S3 through pre-signed URLs. |
| 💰 **Cost optimization** | Adapting resources to the application's real behavior and data access patterns | S3 Lifecycle, S3 Glacier Deep Archive, serverless services | Recent documents stay in a frequent-access class and migrate to historical storage after 12 months. The architecture avoids adding services that don't address a concrete need in the current scenario. |
| 📊 **Operational excellence** | Monitoring, auditing, and infrastructure reproducibility | Amazon CloudWatch, AWS CloudTrail, AWS CloudFormation | CloudWatch tracks logs, metrics, and alarms; CloudTrail logs actions for auditing and governance; CloudFormation enables provisioning and reproducing infrastructure as code. |

---

## 💰 Project costs

<p align="center">
  <img width="1376" height="768" alt="Project cost estimate" src="https://github.com/user-attachments/assets/c5877632-d50d-452d-8545-5b1f6229f31a" />
</p>

The architecture was designed not only to meet Startup Jarva's technical requirements, but also to keep costs compatible with the platform's growth.

Considering a scenario of approximately **50,000 new documents per month**, the Phase 01 estimate results in:

| Indicator | Estimate |
|---|---:|
| 💵 **Recurring monthly cost** | **US$ 143.54** |
| 🧾 **Initial cost** | **US$ 33.00** |
| 📅 **12-month projection** | **US$ 1,755.48** |
| 📄 **Cost per document/month** | **US$ 0.0029** |

> 💡 **In other words:** the architecture can process approximately **50,000 documents per month** with a recurring cost of less than **US$ 0.003 per document**, demonstrating a low marginal cost per unit processed.

### 📊 Where is the cost concentrated?

Most of the cost is related to **document storage and transfer**, not computing capacity.

- 🗄️ **Amazon S3 Intelligent-Tiering:** US$ 65.63/month
- 🌐 **Data transfer:** US$ 61.44/month
- ❄️ **S3 Glacier Deep Archive:** US$ 8.42/month
- 📊 **Amazon CloudWatch:** US$ 6.18/month
- ⚙️ **Other services:** impact under 1% or an estimated cost of US$ 0.00 at the analyzed scale

This distribution reinforces one of the project's main architectural decisions: **cost must track the data's life cycle and behavior**.

Recent documents remain in a tier suited to frequent access, while historical documents can be directed to long-term, lower-cost storage.

### 📈 Optimization strategy

The architecture avoids adding services or optimization mechanisms without a concrete need.

One example is **S3 Transfer Acceleration**. Although it could improve the transfer experience in geographic expansion scenarios, its adoption would significantly increase the estimated costs. For this reason, it was kept as a possible **Phase 02** evolution, rather than a mandatory Phase 01 component.

> **The strategy adopted is simple: add complexity and cost only when the platform's real growth justifies the investment.**

### 📄 Pricing breakdown

The full estimate, including the assumptions used, read calculations, per-service costs, 12-month projection, free-tier levels, and an analysis of the impact of S3 Transfer Acceleration, is available in the document:

👉 **[📄 AWS Services Pricing - Startup Jarva's](./Precificação%20Serviços%20AWS%20-%20Startup%20Jarva's.md)**

> *Estimate prepared based on the AWS Pricing Calculator, using the US East (N. Virginia) region. The figures represent a projection based on the scenario's assumptions and may vary according to the application's actual behavior and changes in AWS service pricing.*

---

## 🚀 Evolution and Future Vision — Phase 02

The architecture presented in Phase 01 was developed to meet the main requirements of the proposed scenario, prioritizing security, isolation between clients, scalability, resilience, document retention, cost optimization, observability, and infrastructure reproducibility.

As part of the solution's evolution, we identified some points that could be improved in a second phase of the project.

These improvements are not necessary for the initial architecture to meet the defined requirements, but they represent opportunities to raise the platform's level of security, governance, resilience, performance, and operational maturity as the business grows.

Phase 02 does not represent a replacement of the current architecture. It builds on the foundation established in Phase 01 and evaluates which new resources and strategies become relevant as the number of users, document volume, operational criticality, and sensitivity of stored data increase.

### 🔐 Phase 02 — Security and Governance Evolution

Phase 02's main goal is to strengthen data protection and the management of sensitive information, complementing the security mechanisms already present in Phase 01.

The services evaluated for this stage are:

| Service | Goal in Phase 02 |
|---|---|
| 🔑 **AWS KMS** | Centralized management of encryption keys and greater control over data protection |
| 🤫 **AWS Secrets Manager** | Secure storage and management of credentials, secrets, and sensitive information used by the application |
| 🔎 **Amazon Macie** | Discovery and identification of sensitive data stored in Amazon S3, supporting the classification and protection of information |

The adoption of these services must be evaluated considering the platform's growth, the sensitivity level of the stored documents, and the financial impact of their use.

Each resource should be incorporated when there is a concrete need that justifies its use, considering security, governance, operational complexity, and cost — not simply as a way to increase the number of components in the architecture.

### ⚡ Phase 02 — Performance and Global Experience Evolution

Phase 01 uses the standard Amazon S3 endpoint to perform file transfers, since the initial scenario does not establish geographic distance as a problem or mandatory requirement of the solution.

However, as Startup Jarva's grows, transfer behavior can be monitored to identify possible impacts related to user location, file size, and upload/download experience.

In this context, **S3 Transfer Acceleration** could be evaluated as a possible architecture evolution.

Its adoption would make more sense in a scenario such as:

- 🌎 international expansion of the platform;
- 📍 clients geographically distributed in regions far from the bucket;
- 📦 significant increase in the size of transferred files;
- 📈 significant growth in transfer volume;
- 📊 identification, through metrics or user feedback, of experience degradation caused by geographic distance.

This way, the service stops being treated as a mandatory architecture component and becomes a **decision driven by a real performance need**.

> **The goal is not to add optimization mechanisms preemptively, but to evaluate their adoption when operational data shows that the benefit justifies the additional cost.**

This approach keeps Phase 01 more aligned with the current scenario and allows the architecture to evolve progressively as new requirements arise.

### 🚀 How can the solution evolve?

The platform's evolution can be analyzed through some important questions:

- How could the solution support a significantly larger volume of users and documents?
- How can the level of data protection be increased as the amount and sensitivity of information grows?
- How can the presence of sensitive information in stored documents be automatically identified and monitored?
- How can the management of credentials and confidential information used by the application be improved?
- How can control over the keys used to protect data be increased?
- How can the impact of failures and unavailability in critical components of the solution be further reduced?
- How can recovery and continuity strategies be established if the platform's availability requirements become more demanding?
- How can a good transfer experience be maintained if the platform starts serving globally distributed clients?
- How can the platform's growth remain sustainable without disproportionately increasing costs?

Phase 02 therefore represents a natural evolution of the architecture, in which additional security, governance, performance, and resilience mechanisms can be incorporated as business needs become more complex.

### 📈 Future vision

In a growth scenario for Startup Jarva's, the architecture could evolve to support a larger volume of users, documents, and processing, while maintaining the principles that guided the solution since its inception.

Among the possibilities for evolution are:

- **🔑 Greater cryptographic protection:** using AWS KMS to expand control over encryption keys and data protection mechanisms.
- **🤫 Sensitive information management:** using AWS Secrets Manager to centralize and protect credentials and other secrets used by the application.
- **🔎 Sensitive data discovery:** using Amazon Macie to identify and classify potentially sensitive information stored in Amazon S3.
- **⚡ Global performance evolution:** evaluation of S3 Transfer Acceleration if the platform's geographic expansion or actual transfer behavior justifies the additional investment.
- **🛡️ Greater resilience:** evaluation of additional recovery and business continuity mechanisms as the platform's availability requirements and criticality increase.
- **📜 Greater governance:** expansion of auditing, monitoring, and control mechanisms as the platform grows.
- **📈 Scalability:** evolution of the architecture to support a significant increase in the number of users and documents without depending on individual components that limit growth.
- **💰 Cost optimization:** ongoing review of storage strategies and service usage according to the application's actual behavior.

These improvements do not necessarily need to be implemented in the first version of the solution. The goal of this stage is to demonstrate that the architecture was designed not only to meet the current scenario, but also to allow consistent evolution as the business grows.

> **Phase 01 solves the current problem. Phase 02 prepares the architecture for the challenges that arise with the platform's growth and maturity.**

---

# 6. How the project was developed

<p align="center">
  <img width="1905" height="1065" alt="Project agile management flow" src="https://github.com/user-attachments/assets/9b9cb4cf-11d1-4d90-8950-c318547d43de" />
</p>

The project's development was carried out using an **agile management** approach, combining **Scrum**, **Kanban**, and **PDCA** to organize activities, track the solution's evolution, and promote continuous cycles of analysis, development, and review.

Since the project involved not only building a technical architecture, but also analyzing the business problem, gathering requirements, evaluating AWS services, and preparing documentation, each of these practices contributed to a different dimension of the process.

## 🏃 Weekly Sprints (Scrum)

The work was organized into **weekly Sprints**, in which the cycle's main goals were defined. Periodic meetings tracked task progress, discussed difficulties, aligned decisions, and reviewed deliverables.

This organization allowed an initially broad problem to be divided into smaller, progressive deliverables: instead of defining the entire architecture at once, decisions matured as the team deepened its understanding of the problem, the requirements, and the possibilities offered by AWS services.

## 🗂️ Kanban Board

The workflow was visualized on a **Kanban board in Trello**, with activities organized into stages — **To Do, In Progress, In Review, and Done**. The board also centralized context notes, planning, and suggestions, giving the team a shared view of what needed to be done, what was in progress, and what had already been completed.

## 🔄 PDCA and continuous improvement

Complementary to the Sprints, we applied the **PDCA (Plan, Do, Check, Act)** cycle to continuously evaluate and improve decisions:

1. **Plan:** identify priorities and define the cycle's goals.
2. **Do:** execute the planned activities.
3. **Check:** review results and decisions, identifying points for improvement.
4. **Act:** incorporate learnings, adjusting the next planning cycle.

This cycle was essential because several architectural decisions matured throughout the project: as requirement analysis progressed, new needs and improvement opportunities were identified and incorporated.

## 🔗 How the approaches connect

**Scrum** provided structure to the work cycles, **Kanban** brought visibility to the flow of activities, and **PDCA** ensured continuous evaluation and improvement of the process:

**Planning → Sprint → Execution → Review → Adjustments → Next Sprint**

This combination balanced organization and flexibility — there were clear goals for each cycle, but also room to revisit decisions as new aspects of the problem emerged.

## 🧭 Decision management and architecture evolution

Decisions were not treated as isolated technical tasks: each choice was related to the project's requirements, business needs, and aspects such as **security, scalability, resilience, availability, retention, and costs**. The evolution followed a progressive flow:

**Understanding the problem → Requirements gathering → Alternatives analysis → Solution definition → Review → Architecture evolution**

This process also made it possible to distinguish what was necessary to meet **Phase 01** requirements from what could be incorporated later, as part of the platform's evolution.

One example of this process was the analysis of **S3 Transfer Acceleration**. Initially considered as an alternative to optimize file transfer, the service was re-evaluated based on the scenario's actual requirements and its cost impact on the solution. Since there was no requirement related to global transfer, nor evidence of performance problems caused by geographic distance, we chose to keep Phase 01 using the standard Amazon S3 endpoint and pre-signed URLs.

Resources such as **AWS KMS, AWS Secrets Manager, Amazon Macie**, and additional performance optimization mechanisms were reserved for possible future evolutions, avoiding adding complexity and cost to the initial architecture without a concrete need to justify them.

## ✅ Result of the management approach

The combination of **Scrum, Kanban, and PDCA** allowed the team to track the solution's evolution, review decisions, and incorporate improvements incrementally and collaboratively — resulting in a process in which **management and architecture evolved together**.

> **The project was not developed as a linear sequence of decisions. It evolved through cycles of planning, execution, review, and continuous improvement, allowing the solution to mature alongside the team's understanding of the problem.**

---

# 7. Infrastructure as Code

The solution's infrastructure was developed following the **Infrastructure as Code (IaC)** concept, allowing the resources needed for the architecture to be defined and provisioned through code.

This approach helps make the infrastructure **reproducible, consistent, and versionable**, reducing dependency on manual configurations and making it easier to create environments with the same architectural structure.

For this project, the infrastructure was implemented using **AWS CloudFormation**, through a template that describes the resources and their configurations. The development of the template also took into account [AWS's official best practices](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html), including aspects related to template creation, stack management, and access control through AWS IAM.

This way, the architecture no longer exists only as a conceptual diagram and can instead be represented and provisioned in a structured way through code.

### 🔗 Access the infrastructure code

[![View infrastructure.yaml](https://img.shields.io/badge/CloudFormation-infrastructure.yaml-527FFF?style=for-the-badge&logo=amazonaws&logoColor=white)](https://github.com/lbarretto/jarvas-aws-architecture/blob/main/infrastructure.yaml)

---
# 8.🎬 Presentation Video

To complement the written documentation, we recorded a presentation video of the project, in which we explain the context of the challenge, the main problems identified, and the architecture of the proposed solution.

<div align="center">

[![Watch the presentation video](https://img.shields.io/badge/▶️-Watch%20on%20YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/4kUy7GKyM3A)

</div>

---

# 9. Acknowledgments

This project was built collaboratively as part of a learning journey and the practical application of knowledge acquired during our cloud computing preparation.

We would like to thank **Escola da Nuvem**, the teachers, mentors, and all team members who contributed with analysis, ideas, and different perspectives throughout the project's development.

<p align="center">
  <em><img width="1196" height="896" alt="Group photo" src="https://github.com/user-attachments/assets/d8629eb0-3388-4bfa-9cb1-b7780856db12" /></em>
</p>

---

# 10. References

**1. Amazon S3 — Block Public Access**
Public access blocking settings and how these settings can prevent policies or permissions that would allow public access to objects.

**2. Amazon S3 — Pre-signed URLs**
Official documentation on pre-signed URLs and how to grant temporary, controlled access to objects stored in Amazon S3.

**3. AWS re:Post — Prefix-based access**
Official example of an IAM policy that uses the `s3:prefix` condition and identity variables to restrict users to their own prefixes within a shared bucket.

**4. Amazon S3 — Object life cycle management**
Official documentation on S3 Lifecycle rules and transitioning objects between different storage classes, including historical and long-term storage scenarios.

**5. Amazon API Gateway — Features**
Documentation on API Gateway's role as an API publishing layer, integration with AWS Lambda, traffic control, and security and monitoring features.

**6. AWS Lambda**
Official documentation on the serverless execution model, event-driven execution, integration with other AWS services, and usage-based billing.

**7. G1 Tecnologia — News report**
Shanghai Police case (2022): a claim of exposure of records associated with about 1 billion citizens due to a possible configuration flaw in a data infrastructure.

The case is used exclusively to contextualize the risk related to improper data exposure and not as technical proof of an exposure at that scale.

**8. IBM — Cost of a Data Breach Report 2026**
IBM's annual report on the costs, causes, and impacts related to data breaches, used as a reference to contextualize the risks associated with information security and the evolution of Artificial Intelligence.

**9. Gartner — Worldwide AI Spending**
Gartner's projections on the growth of global Artificial Intelligence investments and the growing importance of the infrastructure needed to support these solutions.

---

<div align="center">

**☁️ Startup Jarva's**
AI-Powered Document Management SaaS Platform

[![Back to top](https://img.shields.io/badge/⬆-Back%20to%20top-lightgrey?style=flat-square)](#-startup-jarvas)

</div>
