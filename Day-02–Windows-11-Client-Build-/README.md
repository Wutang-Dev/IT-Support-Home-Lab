# Day 02 – Windows 11 Client Deployment & Domain Join

## 🎯 Objective

Deploy a Windows 11 client virtual machine and join it to the Active Directory domain created on Day 01.

This simulates a real-world 1st Line IT task of onboarding a workstation into a corporate environment.

---

## 🖥️ Environment

- Hypervisor: Hyper-V
- Client OS: Windows 11
- Machine Name: CLIENT01
- Domain: ITSUPPORT.LAB
- Domain Controller IP: 192.168.0.10
- DNS Server: 192.168.0.10

---

## 🔧 Steps Performed

### 1️⃣ Created Windows 11 VM

![VM Config](Screenshots/1-Hyper-V-VM-Config.png)

---

### 2️⃣ Renamed Machine to CLIENT01

![Rename 1](Screenshots/2-Renaming-VM-1.png)
![Rename 2](Screenshots/3-Renaming-VM-2.png)

---

### 3️⃣ Configured DNS to Point to Domain Controller

![DNS 1](Screenshots/4-Assigning-DNS-1.png)
![DNS 2](Screenshots/5-Assigning-DNS-2.png)

---

### 4️⃣ Verified DNS Resolution

![Test DNS](Screenshots/6-Test-DNS.png)

---

### 5️⃣ Joined Machine to Domain

![Add to Domain 1](Screenshots/7-Adding-Computer-To-The-Domain.png)
![Add to Domain 2](Screenshots/8-Adding-Computer-To-The-Domain-2.png)
![Add to Domain 3](Screenshots/9-Adding-Computer-To-The-Domain-3.png)

---

### 6️⃣ Confirmed Successful Domain Join

![Joined](Screenshots/10-Joined-To-The-Domain.png)

---

## ✅ Verification

- Successfully authenticated using domain credentials
- Machine visible in Active Directory Users and Computers
- DNS resolution confirmed
- Domain trust established

---

## 🧠 What This Simulates

- Workstation onboarding
- DNS troubleshooting
- Domain authentication
- Corporate endpoint configuration

---

## 📌 Outcome

CLIENT01 is now successfully joined to the ITSUPPORT.LAB domain and fully integrated into the lab environment.
