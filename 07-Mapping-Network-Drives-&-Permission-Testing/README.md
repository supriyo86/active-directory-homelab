
#  Network Drive Mapping & Permission Validation

## 📖 Overview

In this lab, I configured a shared folder on the Domain Controller (**DC01**) and mapped it as a network drive (**Z:**) on a domain-joined client machine (**CL01**).

This task demonstrates how centralized file access is implemented in a Windows Server environment using **Active Directory**, along with **Role-Based Access Control (RBAC)** through NTFS and Share permissions.

---

## 🧩 Environment

* **Server:** DC01 (Windows Server 2022)
* **Client:** CL01 (Windows 10/11)
* **Domain:** homelab.ca
* **Shared Folder:** `C:\Shared_Files`
* **Network Path:** `\\DC01\Shared_Files`
* **Mapped Drive:** `Z:`

---

## ⚙️ Step 1 — Create Shared Folder (DC01)

A folder named **Shared_Files** was created on the Domain Controller:

`C:\Shared_Files`

![Shared Folder Created](../screenshots/01-shared-folder-created.png)

---

## ⚙️ Step 2 — Configure Share Permissions

The folder was shared with specific Active Directory groups:

* **IT_Group → Full Control**
* **HR_Group → Read**

![Share Permissions](../screenshots/02-share-permissions.png)

---

## ⚙️ Step 3 — Configure NTFS Permissions

NTFS permissions were configured to enforce RBAC:

* **IT_Group → Modify**
* **HR_Group → Read & Execute**

![NTFS Permissions](../screenshots/03-ntfs-permissions.png)

---

## 🧪 Step 4 — Map Network Drive (CL01)

On the client machine, the shared folder was mapped as a network drive:

* **Drive Letter:** Z:
* **Folder Path:** `\\DC01\Shared_Files`

![Map Network Drive](../screenshots/04-map-network-drive.png)

---

## ✅ Step 5 — Verify Drive Mapping

The mapped drive appeared successfully under **This PC**:

![Mapped Drive](../screenshots/05-mapped-drive.png)

---

## 🧪 Step 6 — Permission Testing (IT Admin)

Logged in as **it.admin**:

* Created folder → ✅
* Modified files → ✅
* Deleted folder → ✅

![IT Admin Create](../screenshots/06-it-create.png)
![IT Admin Delete](../screenshots/07-it-delete.png)

---

## 🧪 Step 7 — Permission Testing (HR User)

Logged in as **j.smith**:

* Opened files → ✅
* Attempted to delete → ❌ (Access Denied)

![HR Access Denied](../screenshots/08-hr-access-denied.png)

---

## 🔐 Key Concept

Effective access is determined by:

**NTFS Permissions + Share Permissions → Most Restrictive Wins**

This ensures secure and controlled access to shared resources.

---

## 🎯 Outcome

* Successfully mapped a network drive from a domain-joined client
* Implemented secure file sharing using AD groups
* Validated RBAC through real user testing
* Simulated enterprise file server behavior

---
