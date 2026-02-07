# Day 03.1 – Active Directory OU Structure, Users & Security Groups

## 🎯 Objective

Design and implement a structured Active Directory OU hierarchy to simulate a real-world IT support environment.  
Create standard users and security groups following best practice group-based access control.

---

## 🖥️ Environment

- Domain: IT.Support.Lab
- Domain Controller: Windows Server 2022
- Client Machine: Windows 11 (CLIENT01)

---

# 🔹 Step 1 – Create Organisational Units

Created a structured OU hierarchy to separate objects logically.

### Screenshots:

![Creating OUs 1](Screenshots/1-Creating-Organisational-Units-1.png)
![Creating OUs 2](Screenshots/1-Creating-Organisational-Units-2.png)
![OU Structure](Screenshots/2-OU-Structure.png)

### Structure Implemented:

IT.Support.Lab
├── Workstations
├── IT-Support-Lab-Users
└── Security-Groups

This structure allows easier delegation, policy management and troubleshooting.

---

# 🔹 Step 2 – Move Computer Objects

Moved CLIENT01 into the Workstations OU to maintain logical separation.

![Move CLIENT 1](Screenshots/3-Move-CLIENT01-1.png)
![Move CLIENT 2](Screenshots/3-Move-CLIENT01-2.png)
![Move CLIENT 3](Screenshots/5-Move-CLIENT01-3.png)

This ensures computer accounts are not left in the default "Computers" container.

---

# 🔹 Step 3 – Create Standard User Accounts

Created standard user accounts inside the IT-Support-Lab-Users OU.

![Create User 1](Screenshots/6-Create-Standard-User-1.png)
![Create User 2](Screenshots/7-Create-Standard-User-2.png)
![Create User 3](Screenshots/8-Create-Standard-User-3.png)
![Create User 4](Screenshots/9-Create-Standard-User-10.png)

Users were created following a consistent naming convention.

---

# 🔹 Step 4 – Create Security Groups

Created security groups to support role-based access control.

![Create Group 1](Screenshots/11-Create-Security-Group-1.png)
![Create Group 2](Screenshots/12-Create-Security-Group-2.png)
![Create Group 3](Screenshots/13-Create-Security-Group-3.png)
![Create Group 4](Screenshots/14-Create-Security-Group-4.png)

Groups created inside the Security-Groups OU.

---

# 🔹 Step 5 – Add Users to Security Groups

Assigned users to the appropriate security groups.

![Add User 1](Screenshots/15-Add-User-To-Group-1.png)
![Add User 2](Screenshots/16-Add-User-To-Group-2.png)
![Add User 3](Screenshots/17-Add-User-To-Group-3.png)

This follows best practice:
Access should be granted to groups — not directly to users.

---

# 🧠 Key Concepts Demonstrated

- Proper OU design
- Separation of Users, Computers, and Groups
- Role-based access control (RBAC)
- Best practice: Move objects out of default containers
- Group-based permission management

---

## ✅ Outcome

Successfully implemented:

- Structured OU hierarchy
- Organised computer accounts
- Created standard user accounts
- Implemented security groups
- Assigned users via group-based access model

This lab demonstrates practical Active Directory administration aligned with 1st Line / Service Desk responsibilities.
