# Day 01 – Windows Server 2022 Deployment & Active Directory Domain Build

## 🎯 Objective

Deploy a Windows Server 2022 virtual machine in Hyper-V and configure it as a Domain Controller to simulate a real-world IT Support environment.

This lab focuses on:

- Server deployment
- Static IP configuration
- Active Directory installation
- Domain Controller promotion
- DNS verification

---

## 🖥️ Environment

- Hypervisor: Hyper-V
- OS: Windows Server 2022 (Desktop Experience)
- Server Name: DC01
- Static IP: 192.168.0.10
- Subnet Mask: 255.255.255.0
- Gateway: 192.168.0.1
- Domain Name: IT.Support.Lab

---

# 🛠️ Steps Performed

---

## 1️⃣ Created Virtual Machine in Hyper-V

![Hyper-V VM Settings](Screenshots/Day01-01-HyperV-VM-Settings.png)

---

## 2️⃣ Installed Windows Server 2022

![Server Installed](Screenshots/Day01-02-Server-Installed.png)

---

## 3️⃣ Renamed Server to DC01

![Original Server Name](Screenshots/Day01-03-Original-Server-Name.png)
![Server Rename](Screenshots/Day01-04-Server-Rename.png)
![Server Rename Complete](Screenshots/Day01-04-Server-Rename-Complete.png)

---

## 4️⃣ Configured Static IP Address

![Static IP 1](Screenshots/Day01-05-Configuring-Static-Ip-1.png)
![Static IP 2](Screenshots/Day01-06-Configuring-Static-Ip-2.png)
![Static IP 3](Screenshots/Day01-07-Assigning-Static-Ip-3.png)

---

## 5️⃣ Installed Active Directory Domain Services Role

![AD Install 1](Screenshots/Day01-08-Installing-Active-Directory-1.png)
![AD Install 2](Screenshots/Day01-08-Installing-Active-Directory-2.png)
![AD Install 3](Screenshots/Day01-08-Installing-Active-Directory-3.png)
![AD Install 4](Screenshots/Day01-08-Installing-Active-Directory-4.png)
![AD Install 5](Screenshots/Day01-09-Installing-Active-Directory-5.png)
![AD Install 6](Screenshots/Day01-10-Installing-Active-Directory-6.png)
![AD Install Final](Screenshots/Day01-11-Installing-Active-Directory-10.png)

---

# ✅ Verification

After promotion:

- Confirmed domain IT.Support.Lab created
- Verified Forward Lookup Zone in DNS Manager
- Confirmed static IP via `ipconfig /all`
- Confirmed DNS server points to 192.168.0.10
- Confirmed domain visible in Active Directory Users and Computers

---

# 🧠 What This Simulates

This lab mirrors real 1st Line IT Support tasks such as:

- Domain Controller deployment
- Static IP troubleshooting
- AD role installation
- DNS validation
- Basic infrastructure configuration

---

# 🚀 Outcome

A fully operational Active Directory Domain Controller has been successfully deployed.

This environment will be used for future labs involving:

- User account management
- Password resets
- Account lockouts
- Group Policy
- File share permissions
- Microsoft 365 hybrid scenarios
