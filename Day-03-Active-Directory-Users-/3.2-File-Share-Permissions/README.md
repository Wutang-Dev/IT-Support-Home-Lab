# Day 03 – 3.2 File Share Permissions & Drive Mapping

---

## 🎫 Ticket Scenario

**User:** Floyd Mayweather  
**Department:** Helpdesk  
**Issue:** New starter requires access to the Helpdesk shared drive.

Floyd’s account has already been created in Active Directory and added to the **Helpdesk Users** security group (configured in 3.1).  
This task focuses on configuring file share permissions and validating user access.

---

# 🏗️ Step 1 – Create Helpdesk Shared Folder on DC01

A new shared folder named **Helpdesk** was created on the Domain Controller.

### 1. Create Folder
![](Screenshots/1-Create-The-Shared-Folder-1.png)

### 2. Configure Sharing
![](Screenshots/2-Create-The-Shared-Folder-2.png)

### 3. Enable Advanced Sharing
![](Screenshots/3-Create-The-Shared-Folder-3.png)

### 4. Confirm Share Name
![](Screenshots/4-Create-The-Shared-Folder-4.png)

### 5. Configure Share Permissions
![](Screenshots/5-Create-The-Shared-Folder-5.png)

### 6. Confirm Share Setup
![](Screenshots/6-Create-The-Shared-Folder-6.png)

### 8. Verify Share
![](Screenshots/8-Create-The-Shared-Folder-8.png)

---

# 🔐 Step 2 – Configure NTFS Permissions

NTFS permissions were configured so that the **Helpdesk Users** security group has access to the folder.

### 7. Set NTFS Permissions
![](Screenshots/7-Set-NTFS-permissions-7.png)

### 10. Verify NTFS Permissions
![](Screenshots/10-Checking-NTFS-Permissions-1.png)

### 10 (Continued). Confirm Effective Permissions
![](Screenshots/10-Checking-NTFS-Permissions-2.png)

---

# 🖥️ Step 3 – Validate Access from Client01

Logged into the domain-joined Windows 11 machine as:

`Floyd.Mayweather@IT.Support.Lab`

### Access Share via UNC Path

Tested access using:

```
\\DC01\Helpdesk
```

---

# 🔗 Step 4 – Map Network Drive (H:)

Mapped the Helpdesk share as a persistent network drive.

### 11. Map Network Drive
![](Screenshots/11-Mapping-Helpdesk-Drive-1.png)

### 11 (Continued). Drive Mapping Wizard
![](Screenshots/11-Mapping-Helpdesk-Drive-2.png)

### 11 (Final). H: Drive Successfully Mapped
![](Screenshots/11-Mapping-Helpdesk-Drive-3.png)

---

# ✅ Result

- Shared folder successfully created
- Share permissions configured
- NTFS permissions configured
- User accessed share via UNC path
- Drive mapped as **H:**
- Drive reconnects at sign-in

---

# 🧠 Skills Demonstrated

- File share creation on Windows Server
- Share vs NTFS permission configuration
- Security group-based access control
- Domain authentication validation
- UNC path troubleshooting
- Network drive mapping for end users
- Helpdesk-level access confirmation workflow
