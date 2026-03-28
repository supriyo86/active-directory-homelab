# 🧪 Active Directory Homelab (Windows Server 2022)

This project documents my hands-on experience building an **Active Directory home lab** using **Windows Server 2022** and **VirtualBox**.

The goal is to simulate a real-world IT environment and develop practical skills in:

- System administration  
- Active Directory management  
- User and access control  
- Troubleshooting and problem-solving  

---

# 01 - Windows Server Installation & Troubleshooting

## 📖 Overview

As part of building my Active Directory homelab, I began by installing **Windows Server 2022** on **Oracle VM VirtualBox**.

---

## ❌ Issue Encountered

![License Error](../screenshots/01-license-error.png)

**Figure 1:** Windows setup error — "Microsoft Software License Terms not found"

---

## 🔍 Troubleshooting Process

- Verified BIOS virtualization settings  
- Adjusted VM RAM and CPU  
- Reviewed Windows security features  

---

## 🧠 Root Cause

**VirtualBox Unattended Installation** was enabled, which interfered with setup.

---

## ✅ Resolution

- Recreated VM  
- Disabled unattended installation  
- Restarted setup  

---

## ✔️ Result

![Server Installed](../screenshots/02-server-installed.png)

**Figure 2:** Successful installation

---

# 02 - Domain Controller Setup (DC01)

## 📖 Overview

Configured Windows Server as a **Domain Controller (DC01)** for centralized authentication.

---

## ⚙️ Configuration Steps

- Installed AD DS  
- Installed DNS  
- Promoted server to Domain Controller  
- Created forest: `homelab.ca`  
- Set DSRM password  

---

## 🔐 Verification

![Domain Login](../screenshots/03-login-domain.png)

**Figure 3:** Domain login successful (HOMELAB\Administrator)

![DC Ready](../screenshots/04-dc-ready.png)

**Figure 4:** AD DS and DNS roles active

---

# 03 - Client Setup & Domain Join

## 💻 Client Configuration

- Created client VM: **WIN11-CL01**  
- Set DNS to DC01 IP  
- Verified connectivity  

---

## 🔗 Domain Join

![Domain Join](../screenshots/05-domain-join.png)

**Figure 5:** Joining client to domain

![Domain Joined](../screenshots/06-domain-joined.png)

**Figure 6:** Client successfully joined

---

## 🗂️ Active Directory Structure

![OU Structure](../screenshots/07-ou-structure.png)

**Figure 7:** Organizational Units created

---

## ✔️ Verification

![Computer Added](../screenshots/08-computer-added.png)

**Figure 8:** Client visible in AD

![Client Login](../screenshots/09-client-login.png)

**Figure 9:** Successful domain login from client

---

# 04 - Security Groups & Access Control

## 🎯 Objective

- Create security groups  
- Assign users  
- Verify group membership  

---

## 🛠️ Step 1 - Open ADUC

![Open ADUC](../screenshots/10-open-active-directory-users-and-computers.png)

---

## 🗂️ Step 2 - Review Domain Structure

![Domain Structure](../screenshots/11-domain-structure-overview.png)

---

## ➕ Step 3 - Create New Group

![Create Group Menu](../screenshots/12-create-new-group-menu.png)

---

## 👨‍💻 Step 4 - Create IT Group

![IT Group](../screenshots/13-create-it-group.png)

---

## 👥 Step 5 - Create Employees Group

![Employees Group](../screenshots/14-create-employees-group.png)

---

## 📁 Step 6 - Verify OU

![Employees OU](../screenshots/15-employees-ou-structure.png)

---

## ➕ Step 7 - Add User to Group

![Add User](../screenshots/16-add-user-to-group.png)

---

## ✔️ Step 8 - Verify Group Membership

![Members Tab](../screenshots/17-group-members-tab.png)

![Members Confirmation](../screenshots/18-group-members-confirmation.png)

---

## 🔍 Step 9 - Verify from User Side

![User Member Of](../screenshots/19-user-member-of-tab.png)

---

## ✅ Result

- Created Security Groups  
- Assigned users to groups  
- Verified membership from both perspectives  

---

## 🧠 Key Takeaways

- Groups simplify access management  
- OUs keep environment organized  
- Always verify configurations  

---

## 🧰 Skills Practiced

- Active Directory Users and Computers  
- Security Group Management  
- User Administration  
- Domain Management  
- Troubleshooting  

---

## 🚀 Future Improvements

- Group Policy (GPO) implementation  
- Shared folders & permissions  
- Auditing & logging (security monitoring)  
- Privilege escalation detection  

---
