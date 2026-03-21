# 03 - Client Domain Join & User Authentication

## Overview

In this step, I configured a Windows client machine and connected it to my Active Directory domain (homelab.ca). This demonstrates how client systems communicate with a Domain Controller and how users authenticate in a domain environment.

---

## What I Did

- Created a Windows client VM (CL01) in VirtualBox  
- Configured network settings and set DNS to the Domain Controller (DC01)  
- Joined the client machine to the domain:
  homelab.ca  
- Created Organizational Units (OUs) in Active Directory:
  - Employees  
  - Computers  
  - Users  
- Created a test user account:
  John Smith (jsmith)  
- Verified the client machine appeared in Active Directory after domain join  

---

## Verification

![Domain Join](../screenshots/05-domain-join.png)

Client machine successfully joined to the domain (WIN11-CL01 → homelab.ca).

![OU Structure](../screenshots/06-ou-structure.png)

Organizational Units created to structure users and computers within Active Directory.

![User Created](../screenshots/07-user-created.png)

Test user account (John Smith) created for authentication testing.

![Computer Added](../screenshots/08-computer-added.png)

Client machine appears in Active Directory, confirming successful domain join.

---

## Key Takeaways

- DNS configuration is essential for domain communication  
- Active Directory allows centralized management of users and computers  
- Domain join enables authentication across multiple machines  

---

## Reflection

This step completed my Active Directory homelab by connecting a client system to the domain. It helped me understand how authentication works across systems in a centralized environment, similar to real enterprise infrastructure.
