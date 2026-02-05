# Secure Network & SDLC Design for a CRM Software Company

## Overview

This repository presents a **security-focused network and SDLC design** based on a realistic enterprise scenario.

The objective is to design a **secure, scalable, and maintainable environment** for a company that develops CRM software and processes **sensitive customer and employee data**.

The design prioritizes:
- Risk reduction
- Clear security boundaries
- Least-privilege access
- Practical operational security

The focus is deliberately on **security principles and architectural decisions**, rather than specific vendors or products, reflecting how security engineers and architects approach real-world environments.

---

## Business Context

The organization:

- Operates from a **two-floor office**
- Develops and maintains **CRM software**
- Handles sensitive **customer and internal data**
- Hosts critical systems in an **on-site server room**
- Requires **high availability internet access**
- Anticipates **~20% annual growth in users**

### Departments

- Development
- Sales
- Human Resources (HR)
- Finance

Each department has **distinct access requirements** and **different levels of data sensitivity**, which directly informs the security architecture.

---

## Security Objectives

- Minimize attack surface through **network segmentation**
- Limit lateral movement and blast radius
- Enforce **least-privilege access** between systems and users
- Protect critical infrastructure and data stores
- Support future growth without redesigning the entire network
- Enable secure software development and deployment practices

---

## Network Architecture

The network is designed around **explicit trust boundaries**, avoiding a flat internal network.

### Key Architectural Decisions

- **Dual Internet Service Providers (ISPs)** for redundancy
- **Single central firewall** enforcing all traffic policies
- **Dedicated networks per department**
- **Isolated server network** for critical systems
- **Fully segregated guest Wi-Fi**

This structure ensures that a compromise in one area is **contained** and does not automatically propagate across the organization.

📌 *Refer to the Network Architecture Diagram in the `diagrams` directory.*

---

## Network Segmentation Model

Users and systems are segmented based on **role, function, and data sensitivity**.

| Network            | Purpose |
|--------------------|---------|
| Developer Network  | Access to development tools and environments |
| Sales Network      | Access to CRM and demo systems |
| HR Network         | Employee records and payroll systems |
| Finance Network    | Accounting and payment systems |
| Server Network     | Core infrastructure and application servers |
| Guest Wi-Fi        | Internet-only access for visitors |

This segmentation enforces **least privilege** and reduces both insider and external threat impact.

---

## Firewall Policy (Conceptual)

Firewall policies are expressed in **plain language** to ensure they are auditable, reviewable, and easily communicated.

### Example Policy Rules

- Developers may access development systems only
- Developers have no access to HR or Finance networks
- Sales users may access demo and CRM services only
- User endpoints cannot directly access databases
- Servers do not initiate connections to user devices
- Guest Wi-Fi is restricted to outbound internet access only

These controls significantly reduce:
- Lateral movement
- Privilege abuse
- Impact of compromised endpoints

---

## Secure SDLC Architecture

The software development lifecycle is separated into **controlled environments** to reduce risk and prevent accidental exposure of sensitive data.

### Environments

- **Development**  
  Code creation using synthetic or non-production data

- **Test / QA**  
  Functional and integration testing with masked data

- **Staging / UAT**  
  Final validation prior to release

- **Production**  
  Live systems with real data and strict access controls

- **Security Sandbox (Optional)**  
  Isolated environment for testing attacks and high-risk changes

Each environment includes appropriate:
- Access controls
- Logging and monitoring
- Data handling restrictions

📌 *Refer to the SDLC Flow Diagram in the `diagrams` directory.*

---

## Scalability & Growth Considerations

The architecture supports ongoing growth by:

- Avoiding a monolithic internal network
- Allowing departmental networks to scale independently
- Enabling incremental upgrades to network capacity and infrastructure

This ensures the environment remains **secure and manageable** as the organization expands.

---

## Security Governance & Operational Controls

Beyond technical controls, the design includes **operational security considerations** commonly required in real organizations:

- Defined incident response and escalation procedures
- Daily, isolated backups of critical systems
- Regular backup restoration testing
- Role-based access control with periodic access reviews
- Security awareness training for employees
- Physical security controls for sensitive areas

Security is treated as a **people, process, and technology discipline**, not solely a technical problem.

---

## Skills Demonstrated

- Network security architecture design
- Risk-based segmentation and access control
- Firewall policy design and reasoning
- Secure SDLC planning
- Security-focused decision documentation
- Clear technical and non-technical communication
- Business-aligned security thinking

---

## Disclaimer

This project is **educational and demonstrative**.

No real company data, credentials, or production systems are used.
