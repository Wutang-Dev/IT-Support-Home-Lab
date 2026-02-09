# Day 05 – Password Reset & Account Lockout Simulation

## 🎯 Objective
Simulate a real-world Helpdesk scenario involving:

- User password change
- Account lockout due to failed logon attempts
- Account unlock in Active Directory
- Forced password reset
- Successful user login verification

---

## 🖥️ Lab Environment

- Domain Controller: DC01
- Client Machine: CLIENT01 (Windows 11)
- Domain: ITSupportLab.local
- User: Floyd Mayweather

---

# 🔹 Scenario 1 – User Changes Password

### Step 1 – Initial Password Change Attempt
User initiates password change.

📸 Screenshot:
`screenshots/1-Change-Password.png`

---

### Step 2 – Password Successfully Updated
Password change processed successfully.

📸 Screenshot:
`screenshots/2-Change-Password.png`

---

# 🔹 Scenario 2 – Account Lockout Simulation

To simulate a real Helpdesk ticket, incorrect passwords were entered multiple times.

### Step 3 – Account Locked
User receives lockout message after exceeding threshold.

📸 Screenshot:
`screenshots/3-Account-Lockout.png`

---

# 🔹 Scenario 3 – Helpdesk Unlocks Account

### Step 4 – Unlock Account in Active Directory

Steps:
1. Open Active Directory Users and Computers
2. Locate user
3. Open Properties
4. Unlock account checkbox
5. Apply changes

📸 Screenshot:
`screenshots/4-Account-Unlock-In-Active-Directory.png`

---

# 🔹 Scenario 4 – Force Password Reset

### Step 5 – User Must Change Password at Next Logon

Helpdesk sets:
☑ User must change password at next logon

📸 Screenshot:
`screenshots/5-User-Must-Change-Their-Password-Before-Signin.png`

---

### Step 6 – User Changes Password Before Login
User is prompted to create a new password.

📸 Screenshot:
`screenshots/6-Change-Users-Password-Before-Login.png`

---

### Step 7 – Password Successfully Changed
User login successful.

📸 Screenshot:
`screenshots/7-Password-changed.png`

---

# 🧠 Skills Practiced

- Active Directory user management
- Account lockout troubleshooting
- Unlocking accounts
- Forcing password resets
- Understanding lockout threshold policy
- End-user support workflow
- Realistic Helpdesk ticket simulation

---

# 📝 Real-World Helpdesk Workflow Demonstrated

1. User reports login issue
2. Helpdesk verifies account status
3. Account unlocked in AD
4. Password reset enforced
5. User changes password
6. Access verified

---

# ✅ Outcome

User access restored successfully after account lockout and password reset procedure.

---

