# 1. Identity, Access Management (IAM) & Security

What can do what, where and how securely

## 1.1 Basics

### IAM (Identity and Access Management)

The OCI service that controls **who can access which resources and what actions they can perform**.

### User

An individual identity in OCI with credentials used to sign in and access resources. 

### Group (IAM Group)

A collection of users that share the **same permissions**, defined through policies.

### Principal

An IAM entity (user, group, or OCI resource) that can be **authenticated and authorized**.

### Policy Statement

A rule that defines **who (principal) can do what (action) on which resource and where**.

+### Policies

IAM rules written in policy statements that **grant permissions** to users, groups, or resources.

### Action

The operation allowed on a resource in a policy 

- `read`, 
- `use`, 
- `manage`.

### Resource

The OCI object or service that a policy applies to 

- `instance`, 
- `bucket`, 
- `volume`.

### AuthN (Authentication)

The process of **verifying the identity** of a user or system.

### AuthZ (Authorization)

The process of **determining what actions** an authenticated user or system is allowed to perform.

### Federation

A mechanism that allows users to **authenticate using an external identity provider** 

- Active Directory.

### Dynamic Group

An IAM group that automatically includes **OCI resources** based on matching rules, not manual membership.

### Compartments

Logical containers used to **organize**, **isolate**, and **control access** to OCI resources.

### Root Compartment

The **top-level compartment** in a tenancy that contains all other compartments.

+### Compartments (Root Compartment)

The default parent compartment under which **all OCI resources and compartments exist**.

### Tenancy

The OCI account that represents your organization and **owns all resources and compartments**.

### Tagging

Adding metadata (key–value pairs) to OCI resources for **organization, cost tracking, and automation**.

## 1.2 Security Services & Controls

### Cloud Guard

### Oracle Cloud Guard (OCG)

### Detectors

### Responders

### Problems

### Targets

### Security Zone

### Shared Security Model

### Shared Security Responsibility Model

### Web Application Firewall (WAF)

## 1.3 Encryption & Secrets

### Encryption

### Vault (OCI Vault)

### Vault Service

### Key (Master Encryption Key)

### Master Encryption Key (MEK)

### Customer-Managed Key (CMK)

### Secret

# 2. Networking

## 2.1 Core Networking

## 2.2 Gateways & Connectivity

## 2.3 Traffic & Data Flow

## 2.4 Network Security

## 2.5 OSI & Loading Balancing

# 3. Compute & Scaling

## 3.1 Compute Basics

## 3.2 Scaling & Availability

## 3.3 Serverless

# 4. Storage

## 4.1 Object Storage

## 4.2 Block & File Storage

## 4.3 Data Protection

# 5. Availability, Regions & Infrastructure

## 5.1 Physical layout and fault tolerance

# 6. Billing, Cost Management & Governance

## 6.1 Money, limits and control

### Pay As You Go (PAYG)

### Universal Credits (Oracle Universal Credits)

### Oracle Universal Credits (UCM)

### Bring Your Own License (BYOL)

### Budgets

### Budget Threshold

### Cost Analysis

### Notification (E-mail Alert)

### Compartment Quota

### Service Limits

# 7. Database & Analytics

## 7.2 Managed database services

### MySQL HeatWave Database Service

# 8. Miscellaneous / Supporting Concepts

## 8.1 Important but cross-cutting ideas

### Metadata

### Workload

### Multi-cloud Solution

### Service Limits (also governance-related)