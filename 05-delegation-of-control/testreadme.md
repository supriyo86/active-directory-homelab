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
# 🔐 05 - Delegation of Control (Password Reset)

## 📖 Overview

In this step, I implemented **Delegation of Control** in my Active Directory home lab to simulate real-world IT support operations using **Role-Based Access Control (RBAC)**.

---

## 🎯 Objective

Allow a non-administrative user (**IT support role**) to reset passwords for other users **without granting Domain Admin privileges**.

---

## ⚙️ Environment Setup

### 👥 Security Groups Created

- **HR_Group**
- **IT_Group**

### 👤 User Assignment

- `John Smith` → **HR_Group**  
- `it.admin` → **IT_Group**

---

## 🛠️ Delegation Configuration

### Step 1 — Start Delegation Wizard

I initiated the **Delegation of Control Wizard** on the **Employees OU**.

![Step 1](../screenshots/20-delegation-start.png)

---

### Step 2 — Select IT_Group

I selected **IT_Group** as the group to delegate permissions to.

![Step 2](../screenshots/21-select-itgroup.png)

---

### Step 3 — Assign Permissions

I selected the following permissions:

- Reset user passwords  
- Force password change at next logon  

![Step 3](../screenshots/22-permission.png)

---

## 💻 RSAT Configuration (Client Machine)

I installed **Remote Server Administration Tools (RSAT)** on the client machine (**WIN11-CL01**) to allow remote management of Active Directory.

---

## ✅ Verification

### Step 4 — Reset Password from Client

I logged into the client machine as: HOMELAB\it.admin


Then opened **Active Directory Users and Computers (ADUC)** and reset the password for `John Smith`.

![Step 4](../screenshots/23-reset-password.png)

---

### Step 5 — Confirmation

The password reset was successfully applied across the domain.

![Step 5](../screenshots/24-success.png)

---

## 🔍 Access Validation

- ✅ Allowed action → Password reset works  
- ❌ Restricted actions → Still blocked  

This confirms proper delegation without over-privileging.

---

## 🧠 Key Concepts Demonstrated

- 🔐 Role-Based Access Control (RBAC)  
- 🛡️ Principle of Least Privilege  
- 🖥️ Remote Administration (RSAT)  
- 🧑‍💼 IT Support Workflow Simulation  

---

## 📊 Supporting Evidence (Group Membership)

### Group Membership Verification

![Members Tab](../screenshots/17-group-members-tab.png)

![Members Confirmation](../screenshots/18-group-members-confirmation.png)

### User Membership (Member Of Tab)

![User Member Of](../screenshots/19-user-member-of-tab.png)

---

## 🧾 Result

✔️ Delegated password reset permissions successfully  
✔️ IT support user can perform tasks without admin rights  
✔️ Security boundaries maintained  

---

## 💡 Why This Matters

This setup mirrors real enterprise environments where:

- Helpdesk teams reset passwords  
- Admin privileges are restricted  
- Tasks are delegated securely  

---

## 🚀 Next Steps

- Group Policy (GPO) configuration  
- Folder permissions & access control  
- Auditing group membership changes  
- Security event monitoring  

---
