# 04 - Delegation of Control (Password Reset)

In this step, I implemented Delegation of Control in my Active Directory home lab to simulate real-world IT support operations using role-based access control (RBAC).

---

## Objective

Allow a non-administrative user (IT support role) to reset passwords for other users without granting full domain admin privileges.

---

## Configuration

I created two security groups:

- **HR_Group**
- **IT_Group**

### Users:
- **John Smith (j.smith)** → HR_Group  
- **it.admin** → IT_Group  

---

## Delegation Setup

### Step 1 — Start Delegation Wizard

I initiated the Delegation of Control Wizard on the **Employees OU**.

![Step 1](../screenshots/10-delegation-start.png)

---

### Step 2 — Select IT_Group

I selected **IT_Group** as the group to delegate permissions to.

![Step 2](../screenshots/11-select-itgroup.png)

---

### Step 3 — Assign Permissions

I selected the following permissions:

- Reset user passwords  
- Force password change at next logon  

![Step 3](../screenshots/12-permissions.png)

---

## RSAT Setup (Client Machine)

I installed **Remote Server Administration Tools (RSAT)** on the client machine (**CL01**) to manage Active Directory remotely.

---

## Verification

### Step 4 — Reset Password

I logged into CL01 as `HOMELAB\it.admin`, opened ADUC, and attempted to reset the password for `j.smith`.

![Step 4](../screenshots/13-reset-password.png)

---

### Step 5 — Success Confirmation

The password reset was successful and applied in the domain.

![Step 5](../screenshots/14-success.png)

---

## Additional Testing

To validate proper delegation:

- Confirmed allowed actions (password reset) worked  
- Verified restricted actions were blocked  

---

## Key Learning

This lab demonstrates:

- Role-Based Access Control (RBAC)  
- Principle of Least Privilege  
- Remote administration using RSAT  
- Real-world IT support workflow using delegated permissions  

---

## Summary

Delegation of Control allows organizations to assign specific administrative tasks securely without over-privileging users. Combined with RSAT, this enables IT support teams to manage users efficiently from client machines without direct access to the Domain Controller.
