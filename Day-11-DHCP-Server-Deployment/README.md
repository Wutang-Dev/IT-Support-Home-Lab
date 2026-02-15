# Day 11 – DHCP Server Deployment (Active Directory Integrated)

---

# 🧠 Objective

Deploy and configure a fully functional DHCP server within an Active Directory domain environment.

This lab demonstrates:

- DHCP role installation
- DHCP authorization in Active Directory
- Scope creation and configuration
- DHCP option configuration (Gateway + DNS)
- Client migration from Static IP to DHCP
- Lease validation and DNS resolution testing
- End-to-end infrastructure verification

---

# 🏗 Lab Environment

**Domain:** IT.Support.Lab  
**Domain Controller:** DC01 (192.168.10.10)  
**Client Machine:** CLIENT01 (Windows 11)  
**Virtualization:** Hyper-V  
**Virtual Switch:** Lab_Private  
**Network Range:** 192.168.10.0/24  

---

# 🔌 Phase 1 – Network Preparation

## 1. Create Internal Virtual Switch

![Create Internal Switch](screenshots/1-Internal-Switch.png)

---

## 2. Attach Switch to DC01

![Add Internal Switch To DC01](screenshots/2-Add-Internal-Switch-To-DC01.png)

---

## 3. Attach Switch to CLIENT01

![Add Internal Switch To CLIENT01](screenshots/3-Add-Internal-Switch-To-CLIENT01.png)

---

## 4. Reconfigure DC01 to Static IP

Configured:

- IP Address: 192.168.10.10  
- Subnet Mask: 255.255.255.0  
- Default Gateway: 192.168.10.1  
- DNS Server: 192.168.10.10  

![Reconfigure DC01 Static IP](screenshots/4-Reconfigure-DC01-Static-Ip.png)

---

## 5. Confirm Domain Health

![Confirm DC01 Healthy](screenshots/5-Confirming-DC01-Is-Healthy.png)

![Check Domain Health](screenshots/7-Checking-Domain-Health.png)

---

## 6. Enable ICMP (Ping Testing)

![Enable ICMP DC01](screenshots/8-Enable-ICMP-DC01.png)

![Enable ICMP DC01](screenshots/9-Enable-ICMP-DC01.png)

![Enable ICMP CLIENT01](screenshots/10-Enable-ICMP-CLIENT01.png)

![Enable ICMP CLIENT01](screenshots/11-Enable-ICMP-CLIENT01.png)

---

# 🖥 Phase 2 – DHCP Server Installation

## 7. Install DHCP Role on DC01

```bash
Install-WindowsFeature DHCP -IncludeManagementTools
```

![Install DHCP Role 1](screenshots/12-Install-DHCP-Role-1.png)

![Install DHCP Role 2](screenshots/13-Install-DHCP-Role-2.png)

![Install DHCP Role 3](screenshots/14-Install-DHCP-Role-3.png)

![DHCP Server Installed](screenshots/15-DHCP-Server-Installed.png)
```

---

## 8. Authorize DHCP in Active Directory

```bash
Add-DhcpServerInDC -DnsName DC01.IT.Support.Lab -IpAddress 192.168.10.10
Restart-Service DHCPServer
Get-DhcpServerInDC
```

DHCP successfully authorized in the domain.

---

# 📡 Phase 3 – DHCP Scope Creation

## 9. Create DHCP Scope

Network:

```
192.168.10.0/24
```

![Create DHCP Scope 1](screenshots/16-Create-DHCP-Scope-1.png)

![Create DHCP Scope 2](screenshots/17-Create-DHCP-Scope-2.png)

![Validate Scope Creation](screenshots/18-Validate-Scope-Creation.png)

---

## Scope Options Configured

- Default Gateway → 192.168.10.1  
- DNS Server → 192.168.10.10  
- Domain Name → IT.Support.Lab  

---

# 🖥 Phase 4 – Client Migration to DHCP

## 10. Convert CLIENT01 to Automatic DHCP

![Set CLIENT01 Automatic DHCP](screenshots/19-Set-CLIENT01-Automatic-DHCP.png)

---

## 11. Release and Renew IP Address

```bash
ipconfig /release
ipconfig /renew
```

![IPConfig Renew](screenshots/20-Ipconfig-Renew.png)
```

CLIENT01 successfully received:

- IP Address: 192.168.10.100  
- DHCP Server: 192.168.10.10  
- DNS Server: 192.168.10.10  
- Default Gateway: 192.168.10.1  

---

# ✅ Phase 5 – Validation Testing

## 12. Connectivity & DNS Testing

```bash
ping 192.168.10.10
ping dc01
nslookup dc01
```

![DHCP Confirmation](screenshots/21-Confirmation-DHCP-Is-Working.png)
```

---

# 🏁 Results

✔ DHCP role successfully installed  
✔ DHCP authorized in Active Directory  
✔ Scope created and activated  
✔ CLIENT01 received valid lease  
✔ DNS resolution functioning  
✔ Domain controller reachable by hostname  
✔ Zero packet loss observed  
✔ End-to-end infrastructure validated  

---

# 🧠 Technical Explanation

- DHCP distributes IP configuration dynamically to clients.
- DHCP must be authorized in Active Directory to prevent rogue DHCP servers.
- Scope defines the range of addresses available for distribution.
- Scope options provide essential network parameters (Gateway, DNS).
- DNS integration ensures proper domain communication.
- Lease renewal confirms proper client-server DHCP handshake.

---

# 💼 Skills Demonstrated

- Windows Server DHCP deployment
- AD-integrated infrastructure configuration
- DHCP authorization process
- Scope creation and management
- DHCP options configuration
- IP lease validation
- DNS troubleshooting
- Enterprise network validation workflow

---

# 🚀 Real-World Relevance

This mirrors real enterprise environments where:

- Domain Controllers provide DNS
- DHCP servers distribute network configuration
- Clients automatically receive network parameters
- Infrastructure is validated through structured testing

---

Lab Completed: Day 11  
Focus Area: DHCP Deployment & Active Directory Integration
