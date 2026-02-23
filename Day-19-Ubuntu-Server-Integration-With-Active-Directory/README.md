# Day 19 – Joining Ubuntu Server to Active Directory (IT.Support.Lab)

## 🎯 Objective

Integrate an Ubuntu Server into the **IT.Support.Lab** Active Directory domain to enable centralized authentication using Kerberos and SSSD.

This simulates real-world enterprise Linux domain integration.

---

## 🖥️ Lab Environment

- **Domain Controller:** DC01.IT.Support.Lab  
- **Domain Name:** IT.Support.Lab  
- **Ubuntu Server Hostname:** ubuntu-dev01  
- **AD Computer Object:** UBUNTU-DEV01  
- **Lab Network (Private):** 192.168.10.0/24  
- **External Network (Updates):** 192.168.0.0/24  

Ubuntu Server configured with:
- `eth0` → Lab Private (AD communication)
- `eth1` → External Switch (Internet access)

---

## 🌐 DNS Verification

Confirmed Ubuntu is using Active Directory DNS for domain resolution.

### Check Resolver Configuration

```bash
cat /etc/resolv.conf
```

### Verify DNS and Domain Configuration

```bash
resolvectl status
```

Verified:
- DNS Server: `192.168.10.10`
- DNS Domain: `IT.Support.Lab`

---

## 🔎 Validate AD SRV Records

Confirmed LDAP SRV records are discoverable.

```bash
host it.support.lab
```

```bash
host -t SRV _ldap._tcp.it.support.lab
```

Result confirmed:
- Domain resolves correctly
- LDAP SRV record points to `dc01.it.support.lab`

---

## 🔍 Discover Active Directory Realm

```bash
realm discover it.support.lab
```

Output confirmed:
- `server-software: active-directory`
- `client-software: sssd`
- Required packages identified
- Realm available but not yet configured

---

## 🔐 Join Ubuntu to Active Directory

Joined the Ubuntu server to the domain using domain administrator credentials.

```bash
sudo realm join it.support.lab -U Administrator
```

Password entered for `Administrator`.

---

## ✅ Verify Domain Membership

```bash
realm list
```

Output confirmed:
- `configured: kerberos-member`
- `server-software: active-directory`
- `client-software: sssd`
- `login-policy: allow-realm-logins`

---

## 👤 Test AD User Authentication from Linux

Validated identity resolution using an Active Directory user account.

```bash
id muhammad.ali@it.support.lab
```

Output confirmed:
- UID assigned dynamically
- Primary group: `domain users`
- Additional AD security group membership resolved correctly

This confirms:
- Kerberos authentication working
- SSSD integration functioning
- LDAP identity lookup operational
- Group-based access control available on Linux

---

## 🖥️ Active Directory Verification

On Domain Controller:

**Active Directory Users and Computers → Computers**

Verified new computer object:

```
UBUNTU-DEV01
Type: Computer
```

This confirms:
- Machine account successfully created
- Secure channel established between Ubuntu and AD
- Domain trust functioning correctly

---

## 🧠 Key Learning Points

- Linux systems can integrate directly with Active Directory using Kerberos and SSSD.
- Proper DNS configuration is critical for domain discovery.
- SRV record validation confirms AD service availability.
- Domain joining creates a computer object automatically in Active Directory.
- AD security groups are fully resolvable on Linux systems.
- Cross-platform identity management enables centralized authentication in hybrid environments.

---

## 🏁 Outcome

Ubuntu Server is now fully integrated into the **IT.Support.Lab** Active Directory domain.

This enables:
- Centralized identity management
- Group-based access control
- Kerberos-secured authentication
- Enterprise-style hybrid Windows/Linux infrastructure

---

**Wutang-Dev IT Support Home Lab – Enterprise Identity Integration Complete**
