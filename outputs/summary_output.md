# Exam Study Guide: Cloud Platforms, Security, and Automation (BUS5001)

This study guide covers key concepts, security principles, cloud platform components (Azure Blob Storage), and workflow automation from the course materials.

***

## Page 1: Security and Governance

### I. Security Fundamentals and Perspectives

Security encompasses various domains:
*   **Data**
*   **Application**
*   **Compute**
*   **Network** (including Perimeter)
*   **Identity**
*   **Physical**

### II. Core Security Objectives (CIA + A)

Measuring security relies on ensuring these four principles are met:
*   **Confidentiality:** Protecting information from unauthorized access.
*   **Integrity:** Ensuring data is accurate and has not been tampered with.
*   **Authenticity:** Provided by an authorized source. Includes **Non-repudiation**—the inability of a party to deny or challenge the authenticity of an interaction.
*   **Availability:** Being accessible and usable during a certain time period.

### III. Identity and Access Management (IAM)

IAM encompasses Authentication and Authorization. It manages user identities, access groups, password policies, role/privilege management, and credential management.

#### A. Authentication
Authentication determines **who you are** ("Do we know you?").
*   **Ways to Authenticate:** Passwords, Multi-Factor Authentication (MFA), Biometrics (fingerprints/face recognition), Security Tokens.
*   **Personal Best Practices:** Use long complex passwords, utilize a password manager, and audit credentials (e.g., via *haveibeenpwned.com*).

#### B. Multi-Factor Authentication (MFA)
MFA requires **more than one factor**.
| MFA Type | Description/Example | Source |
| :--- | :--- | :--- |
| **Knowledge** | Something you know (e.g., password) | |
| **Possession** | Something you have (e.g., security token) | |
| **Physical** | Something you are (e.g., biometrics) | |
| **Location** | Where you are | |

#### C. Authorization
Authorization determines **what you can do** ("Now that you have access what are the actions you can perform"?). This is often implemented via **RBAC (Role Based Access Control)**.

#### D. Active Directory (AD)
AD provides centralized control to manage users, computers, and devices.
*   **Functions:** Authentication & Authorization, Organizational Structure (Domains, OUs, Forests & Trees), and Group Policy (sets security and configuration laws).
*   **Components:** Global Catalogue (listing of all resources) and Trust Relationships (alliances between domains for resource sharing).

### IV. Security Concepts: Vulnerability, Threat, and Risk

Understanding the relationship between these concepts is crucial for security management.

| Concept | Definition | Source |
| :--- | :--- | :--- |
| **Threat** | A potential security violation that can breach privacy or cause harm. Generally exploits a known weakness (vulnerability). | |
| **Vulnerability** | A weakness that can be exploited due to insufficient security controls, configuration deficiencies, user errors, hardware/firmware flaws, or software bugs. | |
| **Risk** | The possibility of loss or harm from an activity. | |

**Risk Management/Measurement (Conceptual Formula):**
Risk is measured based on the threat level and known vulnerabilities.
$$\text{Risk} = (\text{Probability of Threat Occurring to Exploit Vulnerabilities}) \times (\text{Expectation of Loss})$$

### V. Key Security Mechanisms and Encryption

Security mechanisms are countermeasures that comprise a defensive framework.

*   **Public Key Infrastructure (PKI):** Used for secure communication. It involves a pair of keys: a public key (available to anyone) and a private key (kept secret).
    *   **Confidentiality Example:** If Alice wants to send a message securely to Bob, she encrypts it with Bob's **public key**. Only Bob can decrypt it using his **private key**.
    *   **Authenticity/Digital Signing Example:** Alice seals the box (message) with her own **private seal (signature)**. Bob verifies this seal using Alice's **public key** to ensure it’s from her and untampered.
*   **Encryption:** Mechanisms like HTTPS ensure message confidentiality.
*   **Hashing:** Used for integrity verification (e.g., MD5 / SHA 1 – 3; generally SHA2 is used).

### VI. Data Governance

Data governance is a principled approach to managing data throughout its life cycle, ensuring it is **secure, private, accurate, available, and usable**. It includes the actions people must take, the processes they must follow, and the technology that supports them.

*   **Implications of Lack of Governance (Examples):** Major data breaches resulted in significant loss of user data and company value, such as Yahoo (3 billion records, $350M loss), Equifax (148 million SSNs/dates of birth, $700M payouts), and Marriott (500 million records, $24M class-action lawsuits).

***

## Page 2: Cloud Platforms and Workflow Automation

### I. Azure Blob Storage

Azure Blob storage is **Microsoft's object storage solution** for the cloud, optimized for storing massive amounts of **unstructured data** (data without a particular model or definition, like text or binary data).

#### A. Blob Storage Use Cases (Examples)
*   Serving images or documents directly to a browser.
*   Storing files for distributed access.
*   Streaming video and audio.
*   Storing data for backup, restore, disaster recovery, and archiving.

#### B. Resources within Blob Storage
Azure Storage offers three types of resources:
1.  **The Storage Account:** A unique namespace in Azure for your data, forming the base address for objects.
2.  **A Container:** Organizes a set of blobs, similar to a directory. Can store an unlimited number of blobs.
3.  **A Blob:** Azure Storage supports three main types:
    *   **Block blobs:** Store text and binary data; made of individually managed blocks. Max size ~190.7 TiB.
    *   **Append blobs:** Optimized for append operations; ideal for logging data from virtual machines.
    *   **Page blobs:** Store random access files up to 8 TiB; serve as disks for Azure virtual machines (VHD files).

#### C. Hosting a Static Website (Example)
Static website hosting is a feature enabled on the storage account.
*   **Configuration Requirements:**
    *   **Index document name:** The default page displayed when a user navigates to the root (e.g., `index.html`).
    *   **Error document path:** The default page displayed when a requested page does not exist (e.g., `404.html`).
*   **Deployment:** Files are uploaded to the special **\$web container**. The content type of the files should be set (e.g., `text/html`).

### II. Workflow Automation

Workflow Automation involves automating manual tasks with software that executes all or part of a process. These tools often use low-code, drag-and-drop editor environments.

#### A. Key Components (Structure)
| Component | Function/Role |
| :--- | :--- |
| **Workflow** | Sequence of actions/activities, each having input and an output with a process that runs on it. |
| **Triggers** | Events or conditions that initiate a workflow. |
| **Actions** | Tasks executed as part of the workflow. |
| **Connectors** | Pre-built integrations for communication between web applications and services. |

#### B. Types and Design Concepts
*   **RPA (Robotic Process Automation):** Automates repetitive, manual tasks by mimicking human interaction with software applications and UIs (e.g., Power Automate, UIPath).
*   **Design Tools:** Workflow editors, data mapping/transformation, **Branching (Conditional logic)**, and **Loops**.

#### C. Automation Example (Lead Management)
1.  A website visitor submits a form (Trigger).
2.  The action automatically enrolls the visitor in a drip campaign and sets the deal status to "New" (Action).
3.  The first email is sent requesting a meeting (Action).
4.  The lead schedules an appointment (Action).
5.  A thank you email is sent (Action).
6.  The CRM creates a new task assigned to a sales rep (Action).
7.  The sales rep reaches out personally, ending the automated workflow.

#### D. Azure Logic Apps Example (Email Attachments)
Azure Logic Apps automate and orchestrate workflows. A common workflow is saving email attachments to Blob Storage.

*   **Trigger:** Use an Office 365 Outlook trigger, such as **When a new email arrives (V3)**, configured to only fire if the email has attachments.
*   **Action:** Use the Azure Blob Storage action **Create blob (V2)**, which will create a blob for each attachment.
*   **Workflow Control (Dynamic Expression Example):** To ensure unique naming or organization, expressions are used.
    $$\text{Expression Example: } \mathbf{formatDateTime(triggerBody()?\['receivedDateTime'], 'yyyy-MM-dd')}$$
    This expression formats the email's received time data into a structured date string. The system automatically adds **For Each** controls to iterate through multiple attachments, ensuring the **Create blob** action runs for every file received.
