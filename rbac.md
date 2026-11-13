---
title: "Rbac"
---

**Role-Based Access Control (RBAC)** is a security model that restricts system access to authorized users based on their organizational roles rather than their individual identities. Instead of assigning permissions directly to every user, administrators group permissions into roles (such as *Admin*, *Editor*, or *Viewer*) and then assign those roles to users.

### Core Components of RBAC

* **Users:** The individuals, service accounts, or automated processes interacting with the system.
* **Roles:** Job functions or titles within an organization that define a specific level of authority (e.g., *Billing Manager*, *DevOps Engineer*).
* **Permissions:** Approvals to perform specific operations (such as `read`, `write`, `delete`, or `execute`) on specific resources (like files, databases, or API endpoints).
* **Sessions:** The active mapping between a user and the subset of roles they have activated for a particular interaction.

---

### How RBAC Works (The NIST Model)

Standardized by the National Institute of Standards and Technology ([NIST](https://csrc.nist.gov/projects/role-based-access-control)), RBAC typically operates across four progressive levels:

1. **Core RBAC:** The foundational setup where users are assigned to roles, roles are assigned permissions, and users acquire permissions through their roles. Many-to-many relationships apply (one user can have multiple roles, and one role can belong to multiple users).
2. **Hierarchical RBAC:** Introduces role inheritance. Senior roles automatically inherit the permissions of junior roles (e.g., a *Team Lead* role inherits all permissions of a *Developer* role, plus additional approval rights).
3. **Static Separation of Duty (SSD):** Prevents conflicts of interest by enforcing rules at the assignment level. For example, a single user cannot be assigned both the *Purchase Requester* and *Purchase Approver* roles.
4. **Dynamic Separation of Duty (DSD):** Allows a user to hold conflicting roles in general, but prevents them from activating both roles simultaneously within the same active session.

---

### RBAC vs. Other Access Control Models

| Feature | RBAC (Role-Based) | ACL (Access Control Lists) | ABAC (Attribute-Based) |
| --- | --- | --- | --- |
| **Access Basis** | User's assigned role | Specific user or group identity | Dynamic attributes (user, resource, time, location) |
| **Granularity** | Coarse-to-medium | Fine (per object) | Very fine and context-aware |
| **Scalability** | High; easy to onboard/offboard | Low; becomes unmanageable at scale | High, though complex to configure |
| **Example Rule** | "Managers can approve expenses." | "Alice and Bob can edit `budget.xlsx`." | "Managers can approve expenses under $5,000 during business hours from the corporate VPN." |

---

### Key Benefits

* **Principle of Least Privilege:** Users only receive the exact access required to perform their job duties, minimizing the blast radius if an account is compromised.
* **Operational Efficiency:** Onboarding a new employee or changing someone's department only requires updating their role assignment rather than manually configuring dozens of individual resource permissions.
* **Compliance and Auditing:** Auditors can easily verify who has access to sensitive data by reviewing role definitions and user-role mappings, simplifying compliance with frameworks like SOC 2, HIPAA, and GDPR.

### Common Challenges

* **Role Explosion:** Over time, organizations often create too many hyper-specific roles to handle edge cases, resulting in thousands of roles that are harder to manage than individual permissions.
* **Lack of Context:** Pure RBAC cannot make decisions based on real-time conditions (like IP address, device health, or time of day), which is why modern architectures often pair RBAC with Attribute-Based Access Control (ABAC).

Are you designing an RBAC schema for a specific application or cloud platform (like Kubernetes, AWS IAM, or a custom web app) that you would like to explore?
