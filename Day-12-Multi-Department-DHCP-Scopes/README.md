# Day 12 – Multi-Department Network Segmentation & Routing Preparation

## 📁 Lab Location

```
Ravi/Labs/IT-Support-Lab/Day-12-Multi-Department-DHCP-Scopes/
```

---

# 🧱 Stage 1 – Create Internal Virtual Switches

Created two new internal virtual switches in Hyper-V:

- `Lab_Sales_Internal`
- `Lab_Finance_Internal`

These switches simulate isolated departmental LAN segments.

## 📸 Screenshots

![Sales Internal Switch Created](screenshots/1-Sales-Internal-Switch-Created.png)

![Finance Internal Switch Created](screenshots/2-Finance-Switch-Created.png)

---

# 🔌 Stage 2 – Add Department Switches to DC01

Added additional network adapters to DC01:

- Connected one adapter to `Lab_Sales_Internal`
- Connected one adapter to `Lab_Finance_Internal`

DC01 is now multi-homed.

## 📸 Screenshots

![Add Sales Switch to DC01](screenshots/3-Add-Sales-Internal-To-DC01.png)

![Add Finance Switch to DC01](screenshots/4-Add-Finance-Internal-To-DC01.png)

---

# 🏷️ Stage 3 – Rename Network Adapters on DC01

Renamed adapters for clarity:

- `Helpdesk_Net`
- `Sales_Net`
- `Finance_Net`

## 📸 Screenshot

![Renamed Network Adapters](screenshots/5-Renamed-Network-Adapters-ON-DC01.png)

---

# 🌐 Stage 4 – Configure Static IP Addresses

Configured static IP addresses for each departmental subnet.

---

## 🟢 Sales Network Configuration

```bash
IP Address: 192.168.20.10
Subnet Mask: 255.255.255.0
Default Gateway: (blank)
DNS Server: 192.168.10.10
```

### 📸 Screenshot

![Configure Static IP Sales](screenshots/6-Configure-Static-IP-Sales.png)

---

## 🔵 Finance Network Configuration

```bash
IP Address: 192.168.30.10
Subnet Mask: 255.255.255.0
Default Gateway: (blank)
DNS Server: 192.168.10.10
```

### 📸 Screenshot

![Configure Static IP Finance](screenshots/7-Configure-Static-IP-Finance.png)

---

# 🔎 Stage 5 – Verify Multi-NIC Configuration

Verified all network adapters using:

```bash
ipconfig
```

Confirmed:

- Helpdesk → 192.168.10.10  
- Sales → 192.168.20.10  
- Finance → 192.168.30.10  

## 📸 Screenshot

![IP Configuration Check](screenshots/8-Ipconfig-DC01-Config-Check.png)

---

# 🚦 Stage 6 – Install Routing Role

Installed Routing role on Windows Server.

```bash
Install-WindowsFeature Routing -IncludeManagementTools
```

## 📸 Screenshot

![Install Routing Role](screenshots/9-Install-Routing-Role.png)

---

# 🔁 Stage 7 – Enable IP Routing (RRAS)

Enabled routing functionality and IP forwarding.

```bash
Install-RemoteAccess -VpnType RoutingOnly
```

```bash
Set-Service RemoteAccess -StartupType Automatic
```

```bash
Start-Service RemoteAccess
```

```bash
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters" `
-Name IPEnableRouter `
-Value 1
```

## 📸 Screenshots

![Enable IP Routing](screenshots/10-Enable-Ip-Routing.png)

![Enable IP Forwarding](screenshots/11-Enable-IP-Forwarding.png)

---

# 🧠 Network Architecture Overview

## Subnets

| Department | Subnet | DC01 IP |
|------------|--------|----------|
| Helpdesk | 192.168.10.0/24 | 192.168.10.10 |
| Sales | 192.168.20.0/24 | 192.168.20.10 |
| Finance | 192.168.30.0/24 | 192.168.30.10 |

DC01 is now acting as:

- Domain Controller  
- DNS Server  
- DHCP Server  
- Software Router (RRAS)  

---

# 🎯 Next Steps (Day 13)

- Deploy Sales VM  
- Deploy Finance VM  
- Assign correct default gateway per subnet:
  - Sales → 192.168.20.10  
  - Finance → 192.168.30.10  
- Validate inter-subnet communication  
- Test DNS resolution across subnets  
- Capture routing validation screenshots  

---

# 🔥 Summary

Day 12 transitioned the lab from a single-subnet environment to a segmented multi-subnet architecture.

This lab demonstrates:

- Multi-homed Windows Server configuration  
- Internal network segmentation  
- Subnet boundary implementation  
- Layer 3 routing using RRAS  
- Enterprise-style departmental network design  
