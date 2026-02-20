# Day 16 – Deploying Ubuntu Web Server Inside Windows AD Lab

## 🎯 Objective

Integrate an Ubuntu Server into the existing Windows Server 2022 Active Directory lab and deploy an internal Apache web server accessible from domain-joined machines.

This lab focused on hybrid infrastructure — combining Windows AD services with a Linux-based web server inside the same segmented lab network.

---

## 🏗 Lab Architecture

**Hyper-V Environment**

- DC01 – Windows Server 2022 (AD DS + DNS)
- CLIENT01 – Domain-joined Windows client
- UBUNTU-DEV01 – Ubuntu Server 24.04 LTS

**Networking**

- `eth0` → Lab_Private vSwitch (192.168.10.0/24)
- `eth1` → Hyper-V Default Switch (Internet/NAT)

This mirrors a real enterprise dual-homed server deployment model.

---

## 🧠 Configuration Steps

### 1️⃣ Configured Dual NIC Using Netplan

Edited:

```bash
/etc/netplan/00-installer-config.yaml
```

Configuration used:

```yaml
network:
  version: 2
  ethernets:
    eth0:
      dhcp4: yes
    eth1:
      dhcp4: yes
```

Applied configuration:

```bash
sudo chmod 600 /etc/netplan/00-installer-config.yaml
sudo netplan apply
```

Verified interfaces and routing:

```bash
ip a
ip route
```

Result:

- `eth0` → 192.168.10.x (Internal AD Network)
- `eth1` → 192.168.0.x (Internet Access)
- Dual default routes via DHCP

---

### 2️⃣ Verified Internal DNS Resolution

Tested connectivity to the Domain Controller:

```bash
ping dc01.it.support.lab
```

Confirmed successful DNS resolution via Windows DNS server.

---

### 3️⃣ Installed Apache Web Server

Updated packages:

```bash
sudo apt update
```

Installed Apache:

```bash
sudo apt install apache2 -y
```

Verified service status:

```bash
sudo systemctl status apache2
```

Result:

```
Active: active (running)
```

---

### 4️⃣ Tested Internal Web Access

From DC01 browser:

```
http://192.168.10.102
```

Successfully loaded:

**Apache2 Ubuntu Default Page – "It works!"**

This confirmed:

- Internal network connectivity
- Service listening correctly
- Cross-platform communication
- Proper segmentation between internal lab and internet

---

## 🔥 What This Lab Demonstrates

- Windows + Linux hybrid infrastructure
- Hyper-V virtual networking design
- Dual-homed server configuration
- Enterprise-style network segmentation
- Linux service management (`systemctl`)
- Apache deployment inside AD environment
- DNS-based name resolution between platforms

---

## 🚀 Planned Enhancements

- Create DNS A record (`web01.it.support.lab`)
- Replace default Apache page with internal company portal
- Optional: Join Ubuntu server to Active Directory
- Implement HTTPS using self-signed certificates

---

## 📌 Summary

Day 16 marks a transition from pure IT Support lab work into infrastructure-level systems engineering.

The lab now includes:

- Active Directory Domain Controller
- DNS Services
- Domain-joined Windows client
- Linux server integrated into the network
- Internal web server deployment

This simulates a real-world hybrid enterprise environment combining Windows Server and Linux systems.
