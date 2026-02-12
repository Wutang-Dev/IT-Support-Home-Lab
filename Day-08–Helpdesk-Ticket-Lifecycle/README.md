# Day 08 – Helpdesk Ticket Lifecycle & Remote Support Simulation

---

## 🧠 Objective

Simulate a real-world Helpdesk workflow including:

- Ticket logging and categorisation
- Incident prioritisation
- Structured troubleshooting
- Remote support session
- Customer communication
- Ticket resolution documentation

---

## 🏗 Lab Environment

Domain: IT.Support.Lab  
Ticketing Platform: Jira (Free Tier)  
Remote Tool: Zoho Assist  
Client Machine: CLIENT01  
Domain Controller: DC01  

---

## 🎫 Ticket Overview

| Ticket ID | Summary | Priority | Status |
|------------|---------|----------|--------|
| ITSUP-001 | Sales Drive Not Accessible | High | Closed |
| ITSUP-002 | Password Reset | Medium | Closed |
| ITSUP-003 | Printer Offline | Medium | Resolved |
| ITSUP-004 | Slow Wi-Fi | Low | Closed |
| ITSUP-005 | New User Creation | Medium | Closed |
| ITSUP-006 | MFA Setup | Low | Closed |
| ITSUP-007 | Software Installation | Medium | Closed |
| ITSUP-008 | VPN Not Connecting | High | Resolved |
| ITSUP-009 | Outlook Not Syncing | Medium | Resolved |
| ITSUP-010 | Blue Screen on Startup | Critical | In Progress |

---

## 🔎 Detailed Incident Example – ITSUP-001

### Summary
Sales user unable to access mapped drive (S:)

### Investigation Steps
- Checked network connectivity
- Verified DNS configuration
- Confirmed domain membership
- Flushed DNS cache
- Re-registered DNS
- Tested name resolution

### Root Cause
Client DNS incorrectly assigned via router DHCP instead of Domain Controller.

### Resolution
- Manually set DNS to 192.168.0.10
- Verified resolution using nslookup
- Confirmed drive mapping restored

### Preventative Action
Reserved IP address in router DHCP settings to prevent DNS misassignment.

---

## 🖥 Remote Support Session

Zoho Assist used to:

- Connect to CLIENT01
- Verify issue reproduction
- Apply configuration changes
- Confirm successful resolution with user

---

## 🧠 Key Skills Demonstrated

- Incident documentation
- Prioritisation & ticket lifecycle management
- Active Directory troubleshooting
- DNS dependency understanding
- Customer communication
- Remote support handling

---

## 🏁 Outcome

All simulated tickets processed using structured Helpdesk workflow.

Demonstrated both technical troubleshooting and customer service competency.
