
# 02 - Domain Controller Setup (DC01)

## Overview

In this step, I configured my Windows Server 2022 machine as a Domain Controller (DC01) in my Active Directory homelab. This setup enables centralized authentication and management within the network.

---

## What I Did

- Installed Active Directory Domain Services (AD DS) using Server Manager  
- Installed DNS Server  
- Promoted the server to a Domain Controller  
- Created a new forest with domain name:
  homelab.ca  
- Set the DSRM (Directory Services Restore Mode) password  
- Completed installation and rebooted the server  

---

## Verification

After completing the setup, I verified that the Domain Controller is working correctly.

![Login](../screenshots/03-login-domain.png)

Successful login using domain account (HOMELAB\Administrator), confirming the domain was created successfully.

![Server](../screenshots/04-dc-ready.png)

Server Manager shows AD DS and DNS roles running, confirming the Domain Controller is healthy and operational.

---

## Key Takeaways

- Active Directory depends heavily on DNS  
- Domain Controller enables centralized authentication  
- Verification is critical after configuration  

---

## Reflection

This step helped me understand how a standalone server becomes part of a centralized domain environment and how authentication works in enterprise systems.
