# 🧪 Active Directory Homelab (Windows Server 2022)

<p align="center">
  <img src="https://img.shields.io/badge/Project-Active%20Directory%20Lab-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Platform-Windows%20Server%202022-0078D6?style=for-the-badge&logo=windows" />
  <img src="https://img.shields.io/badge/Hypervisor-VirtualBox-183A61?style=for-the-badge&logo=virtualbox" />
  <img src="https://img.shields.io/badge/Focus-IT%20Support%20%7C%20SysAdmin-green?style=for-the-badge" />
</p>

---

## 📌 Project Overview

This project documents my hands-on experience building an **Active Directory home lab** using **Windows Server 2022** and **VirtualBox**.

The lab simulates a real-world IT environment and focuses on developing practical skills in:

- System administration  
- Active Directory management  
- User and access control  
- Troubleshooting  

---

## 🏗️ Lab Architecture
DC01 (Domain Controller)
│
├── Active Directory (homelab.ca)
├── DNS Server
│
└── Client Machine
└── WIN11-CL01 (Domain Joined)

---

# ⚙️ 01 - Windows Server Installation & Troubleshooting

## 📖 Overview

The first step was installing **Windows Server 2022** on **VirtualBox**.

---

## ❌ Issue Encountered

![License Error](../screenshots/01-license-error.png)

**Figure 1:** Windows setup error — *Microsoft Software License Terms not found*

---

## 🔍 Troubleshooting

- Verified virtualization settings  
- Adjusted VM resources (CPU, RAM)  
- Checked Windows security features  

---

## 🧠 Root Cause

The issue was caused by **VirtualBox Unattended Installation**, which interfered with the setup process.

---

## ✅ Resolution

- Recreated the virtual machine  
- Disabled unattended installation  
- Restarted installation  

---

## ✔️ Result

![Server Installed](../screenshots/02-server-installed.png)

**Figure 2:** Successful installation

---

## 🧠 Key Takeaways

- Not all issues are caused by corrupted files  
- Automation can introduce unexpected errors  
- Structured troubleshooting is essential  

---

# 🏢 02 - Domain Controller Setup (DC01)

## 📖 Overview

Configured the server as a **Domain Controller (DC01)** to enable centralized authentication.

---

## ⚙️ Configuration Steps

- Installed **Active Directory Domain Services (AD DS)**  
- Installed **DNS Server**  
- Promoted server to Domain Controller  
- Created domain: `homelab.ca`  
- Configured DSRM password  

---

## 🔐 Verification

![Domain Login](../screenshots/03-login-domain.png)

**Figure 3:** Successful domain login  

![DC Ready](../screenshots/04-dc-ready.png)

**Figure 4:** AD DS and DNS roles operational  

---

## 🧠 Key Takeaways

- Active Directory relies heavily on DNS  
- Domain Controllers centralize authentication  
- Always verify services after setup  

---

# 💻 03 - Client Setup & Domain Join

## 💻 Client Configuration

- Created client VM: **WIN11-CL01**  
- Configured DNS to point to DC01  
- Verified connectivity  

---

## 🔗 Domain Join

![Domain Join](../screenshots/05-domain-join.png)

**Figure 5:** Joining client to domain  

![Domain Joined](../screenshots/06-domain-joined.png)

**Figure 6:** Domain join successful  

---

## 🗂️ Organizational Structure

![OU Structure](../screenshots/07-ou-structure.png)

**Figure 7:** Organizational Units  

---

## ✔️ Verification

![Computer Added](../screenshots/08-computer-added.png)

**Figure 8:** Client appears in AD  

![Client Login](../screenshots/09-client-login.png)

**Figure 9:** Successful domain authentication  

---

## 🧠 Key Takeaways

- DNS is critical for domain communication  
- Domain join validates infrastructure  
- Authentication confirms correct setup  

---

# 🔐 04 - Security Groups & Access Control

## 🎯 Objective

- Create security groups  
- Assign users  
- Verify group membership  

---

## 🛠️ Steps

### Open ADUC
![Step](../screenshots/10-open-active-directory-users-and-computers.png)

### Review Domain Structure
![Step](../screenshots/11-domain-structure-overview.png)

### Create Group
![Step](../screenshots/12-create-new-group-menu.png)

### Create IT Group
![Step](../screenshots/13-create-it-group.png)

### Create Employees Group
![Step](../screenshots/14-create-employees-group.png)

### Verify OU
![Step](../screenshots/15-employees-ou-structure.png)

### Add User to Group
![Step](../screenshots/16-add-user-to-group.png)

### Verify Membership
![Step](../screenshots/17-group-members-tab.png)
![Step](../screenshots/18-group-members-confirmation.png)

### Verify from User Side
![Step](../screenshots/19-user-member-of-tab.png)

---

## ✅ Result

- Security groups created  
- Users assigned correctly  
- Membership verified  

---

## 🧠 Key Takeaways

- Groups simplify access control  
- OUs improve organization  
- Always verify membership  

---

# 🔐 05 - Delegation of Control (Password Reset)

## 📖 Overview

Implemented **Delegation of Control** to simulate real-world IT support using **RBAC**.

---

## 🎯 Objective

Allow IT support users to reset passwords **without full admin privileges**.

---

## ⚙️ Setup

### Groups

- **HR_Group**
- **IT_Group**

### Users

- `John Smith` → HR_Group  
- `it.admin` → IT_Group  

---

## 🛠️ Delegation Steps

### Start Delegation Wizard
![Step](../screenshots/20-delegation-start.png)

### Select IT_Group
![Step](../screenshots/21-select-itgroup.png)

### Assign Permissions
![Step](../screenshots/22-permission.png)

---

## 💻 RSAT Setup

Installed **RSAT** on client machine for remote administration.

---

## ✅ Verification

### Reset Password

Logged in as:
HOMELAB\it.admin


![Step](../screenshots/23-reset-password.png)

### Confirmation
![Step](../screenshots/24-success.png)

---

## 🔍 Validation

- ✅ Password reset works  
- ❌ Other admin actions blocked  

---

## 📊 Supporting Evidence

![Step](../screenshots/17-group-members-tab.png)
![Step](../screenshots/18-group-members-confirmation.png)
![Step](../screenshots/19-user-member-of-tab.png)

---

## 🧠 Key Concepts

- Role-Based Access Control (RBAC)  
- Principle of Least Privilege  
- Remote administration (RSAT)  

---

## 🧾 Final Outcome

✔️ Delegation successfully configured  
✔️ IT support role functional  
✔️ Security maintained  

---

## 🚀 Next Steps

- Group Policy (GPO)  
- Shared folders & permissions  
- Auditing & monitoring  
- Security event tracking  

---

## 💡 Why This Project Matters

This lab demonstrates real-world IT skills:

- Domain setup  
- User management  
- Access control  
- Troubleshooting  

It reflects the responsibilities of an **IT Support / System Administrator role**.

---

## 👨‍💻 Author

**Supriyo Talukder**  
Aspiring IT Support / Cybersecurity Professional  

---
