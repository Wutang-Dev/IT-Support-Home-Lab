# Day 06 – Role-Based Share Permissions & Drive Mapping

---

# 🧠 Objective

Simulate a real-world helpdesk / junior sysadmin task by:

- Creating departmental users  
- Creating security groups  
- Assigning NTFS permissions  
- Testing access control  
- Mapping network drives  
- Validating least privilege access  

This lab demonstrates practical Active Directory and file server administration.

---

# 🏗 Lab Architecture

## Domain
`IT.Support.Lab`

## Users
- ITFloyd.Mayweather (Helpdesk)
- Muhammad.Ali (Sales)
- Mike.Tyson (Finance)

## Security Groups
- Sales-Users
- Finance-Users
- Helpdesk-Users (existing)

## Shared Folders
- `\\DC01\Sales`
- `\\DC01\Finance`

---

# 1️⃣ Creating Users

## 1.1 Create Ali User
![Create Ali User](screenshots/1-Create-Ali-User.png)

## 1.2 Create Tyson User
![Create Tyson User](screenshots/3-Create-Tyson-User.png)

## 1.3 Users Created
![Users Created](screenshots/4-Users-Created.png)

---

# 2️⃣ Creating Security Groups

## 2.1 Create Sales Security Group
![Create Sales Security Group](screenshots/5-Create-Sales-Security-Group.png)

## 2.2 Create Finance Security Group
![Create Finance Security Group](screenshots/6-Create-Finance-Security-Group.png)

---

# 3️⃣ Adding Users to Security Groups

## 3.1 Add Ali to Sales-Users
![Add Ali 1](screenshots/7-Add-Ali-To-Sales-Users-1.png)
![Add Ali 2](screenshots/7-Add-Ali-To-Sales-Users-2.png)

## 3.2 Add Tyson to Finance-Users
![Add Tyson 1](screenshots/8-Add-Tyson-To-Finance-Users-1.png)
![Add Tyson 2](screenshots/8-Add-Tyson-To-Finance-Users-2.png)

## 3.3 Remove Ali from All Users (Cleanup Step)
![Remove Ali](screenshots/11-Remove-Ali-Users.png)

---

# 4️⃣ Creating Shared Folders

## 4.1 Configure Sales Share Folder
![Sales Share Config](screenshots/13-Config-Sales-Share-Folder.png)

## 4.2 Finance Shared Folder Created
![Finance Share Folder](screenshots/15-Finance-Shared-Folder-1.png)

---

# 5️⃣ Configuring NTFS Permissions

## 🔐 Sales Folder Permissions

### Remove Inheritance
![Removing Inheritance](screenshots/10-Removing-Inheritance.png)

### Assign Sales-Users Modify Access
![Sales Permission 1](screenshots/12-Giving-Sales-Users-Permission-To-The-Drive-1.png)
![Sales Permission 2](screenshots/12-Giving-Sales-Users-Permission-To-The-Drive-2.png)
![Sales Permission 3](screenshots/12-Giving-Sales-Users-Permission-To-The-Drive-3.png)

---

## 🔐 Finance Folder Permissions

### Assign Finance-Users Modify Access
![Finance Permission 1](screenshots/14-Finance-Share-Permissions-1.png)
![Finance Permission 2](screenshots/14-Finance-Share-Permissions-2.png)
![Finance Permission 3](screenshots/14-Finance-Share-Permissions-3.png)

---

# 6️⃣ Access Testing (Validation Phase)

## 👤 Muhammad Ali (Sales User)

### 6.1 Sales Access – SUCCESS
![Ali Sales Success](screenshots/17-Ali-Access-Sales-Success.png)

### 6.2 Finance Access – DENIED
![Ali Finance Denied](screenshots/16-Ali-Access-Finance-Denied.png)

### 6.3 Sales Drive Mapped
![Ali Sales Drive Mapped](screenshots/21-Ali-Sales-Drive-Mapped.png)

---

## 👤 Mike Tyson (Finance User)

### 6.4 Sales Access – DENIED
![Tyson Sales Denied](screenshots/19-Tyson-Access-Sales-Denied.png)

### 6.5 Finance Access – SUCCESS
![Tyson Finance Success](screenshots/18-Tyson-Access-Finance-Success.png)

### 6.6 Finance Drive Mapped
![Tyson Finance Drive Mapped](screenshots/20-Tyson-Finance-Drive-Mapped.png)

---

# 🔎 Access Control Matrix

| User   | Sales        | Finance      |
|--------|-------------|--------------|
| Ali    | ✅ Allowed  | ❌ Denied    |
| Tyson  | ❌ Denied   | ✅ Allowed   |
| Floyd  | Helpdesk Group | Not Assigned |

---

# 🧠 Key Concepts Practiced

- Active Directory User Creation  
- Security Group Management  
- NTFS vs Share Permissions  
- Principle of Least Privilege  
- Access Testing & Validation  
- Manual Drive Mapping  
- Role-Based Access Control (RBAC)

---

# 🏁 Outcome

This lab successfully implemented department-based access control using security groups and NTFS permissions.  

Each user was restricted to only their appropriate departmental share, demonstrating proper RBAC implementation.

This simulates a real-world helpdesk / junior system administrator task involving file server access configuration and user validation.
