# Day 17 – Creating Internal DNS A Record for Ubuntu Web Server

## 🎯 Objective

Move from IP-based access to proper hostname-based access by creating an internal DNS A record in Active Directory.

Goal:

```
web01.it.support.lab → 192.168.10.102
```

This improves infrastructure hygiene and mirrors real enterprise service naming standards.

---

## 🏗️ Environment

- **Domain Controller:** DC01  
- **Domain:** IT.Support.Lab  
- **Ubuntu Web Server IP:** 192.168.10.102  
- **DNS Role:** Hosted on DC01  

Apache was already confirmed running internally via IP address.

---

## 🛠️ Step 1 – Create DNS A Record

On DC01:

```
Server Manager → Tools → DNS
```

Navigate to:

```
Forward Lookup Zones
 └── it.support.lab
```

Right-click the zone → **New Host (A or AAAA)**

Configured:

- **Name:** web01  
- **IP Address:** 192.168.10.102  
- ✔ Create associated PTR record  

After creation, the following record appeared:

```
web01    Host (A)    192.168.10.102
```

---

## 🔄 Step 2 – Flush Client DNS Cache

On CLIENT01:

```bash
ipconfig /flushdns
```

This ensures no cached resolution interferes with testing.

---

## 🔎 Step 3 – Validate Name Resolution

Tested from CLIENT01:

```bash
ping web01.it.support.lab
```

Result:

Resolved successfully to:

```
192.168.10.102
```

---

## 🌐 Step 4 – Browser Validation

Accessed from DC01 and CLIENT01:

```
http://web01.it.support.lab
```

Result:

Apache default page loaded successfully.

This confirms:

- DNS resolution working
- Internal network routing functioning
- Apache listening correctly
- Cross-platform service accessibility

---

## 🔥 What This Lab Demonstrates

- Active Directory DNS management
- Internal service naming conventions
- Forward lookup zone configuration
- DNS cache handling
- Service validation through hostname
- Proper separation of identity vs IP access

---

## 📌 Why This Matters

In enterprise environments, services are never accessed by IP.

Using DNS:

- Improves maintainability
- Allows IP changes without service disruption
- Supports certificate-based HTTPS in future labs
- Aligns with real infrastructure standards

---

## 🚀 Next Steps

Planned progression:

- Replace Apache default page with internal company portal
- Join Ubuntu server to Active Directory
- Implement HTTPS using self-signed certificates
- Introduce SSL/TLS validation via hostname

---

## 📚 Summary

Day 17 reinforces proper infrastructure practices by implementing internal DNS-based service access.

The lab environment now supports:

- Active Directory DNS
- Windows clients
- Linux web server

The foundation for secure, identity-based service access is now in place.
