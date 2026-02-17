# Day 13 – Multi-Subnet Domain Join & DHCP Validation

## 🧠 Objective

- Configure Sales DHCP scope
- Validate DNS resolution
- Join SALES01 to IT.Support.Lab
- Troubleshoot multi-switch routing issue
- Implement correct OU structure

---

# 🖼️ Lab Walkthrough (Screenshots)

---

## 1️⃣ Create Sales Machine

![Create Sales Machine](screenshots/1-Create-Sales-Machine.png)

---

## 2️⃣ Rename Sales Machine

![Rename Sales Machine](screenshots/2-Rename-Sales-Machine.png)

---

## 3️⃣ Create Default Gateway on DC01

![Create Default Gateway](screenshots/3-Create-Default-Gateway-DC01.png)

---

## 4️⃣ Create Sales DHCP Scope on DC01

![Create Sales DHCP Scope](screenshots/3-Create-Sales-DHCP-Scope-DC01.png)

---

## 5️⃣ Configure DNS Server IP on DC01

![Set DNS Server IP](screenshots/4-Set-The-DNS-Server-IP-DC01.png)

---

## 6️⃣ Configure DNS Name on DC01

![Set DNS Name](screenshots/5-Set-The-DNS-Name-DC01.png)

---

## 7️⃣ Verify DC01 Configuration

![Verify Config](screenshots/6-Verify-Config-DC01.png)

---

## 8️⃣ Join SALES01 to Domain

![Joined to Domain](screenshots/7-Joined-Sales01-To-Domain.png)

---

## 9️⃣ SALES01 Receives DHCP Lease

![Receives DHCP](screenshots/8-Sales01-Recieves-DHCP.png)

---

## 🔟 Move SALES01 to Workstations OU

![Moved to Workstations OU](screenshots/9-Moved-Sales01-Workstation-OU.png)

---

# ✅ Validation Commands Used

```bash
ipconfig /all
ping 192.168.10.10
ping dc01
nslookup IT.Support.Lab
nslookup dc01.IT.Support.Lab
```

---

# 🏁 Final Result

- SALES01 successfully joined IT.Support.Lab
- DHCP lease automatically assigned
- DNS resolving correctly
- Machine placed inside Workstations OU
- Lab environment stabilised

---

# 📚 Key Learning

Active Directory depends heavily on DNS.

If DNS breaks:
- Domain join fails
- Authentication fails
- Group Policy fails

Infrastructure chain:

Routing → DHCP → DNS → Active Directory → Policy

---


