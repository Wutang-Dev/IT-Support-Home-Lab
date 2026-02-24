# Day 19 – Implementing HTTPS with Self-Signed Certificate (Apache2 on Ubuntu)

## Objective

Secure the internal web portal (`web01.it.support.lab`) using HTTPS with a self-signed SSL certificate.

This exercise focuses on proper infrastructure practice:

- Generating SSL certificates
- Configuring Apache VirtualHosts
- Enabling SSL module
- Redirecting HTTP to HTTPS
- Validating network and TLS functionality

---

## Environment

**Domain:** IT.Support.Lab  
**Web Server:** Ubuntu Server (Domain Joined)  
**Web Service:** Apache2  
**Server FQDN:** web01.it.support.lab  
**IP Address:** 192.168.10.102  
**Domain Controller:** DC01 (192.168.10.10)

---

## Step 1 – Generate Self-Signed SSL Certificate

```bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-keyout /etc/ssl/private/web01.key \
-out /etc/ssl/certs/web01.crt
```

Certificate Details Used:

- Country: UK  
- State: London  
- Organization: IT.Support.Lab  
- Common Name (CN): web01.it.support.lab  

---

## Step 2 – Create SSL VirtualHost Configuration

```bash
sudo tee /etc/apache2/sites-available/web01-ssl.conf > /dev/null << 'EOF'
<VirtualHost *:443>
    ServerName web01.it.support.lab

    DocumentRoot /var/www/html

    SSLEngine on
    SSLCertificateFile /etc/ssl/certs/web01.crt
    SSLCertificateKeyFile /etc/ssl/private/web01.key

    <Directory /var/www/html>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/web01_ssl_error.log
    CustomLog ${APACHE_LOG_DIR}/web01_ssl_access.log combined
</VirtualHost>
EOF
```

---

## Step 3 – Enable SSL Module

```bash
sudo a2enmod ssl
```

---

## Step 4 – Enable SSL Site

```bash
sudo a2ensite web01-ssl.conf
```

---

## Step 5 – Configure HTTP to HTTPS Redirect

```bash
sudo tee /etc/apache2/sites-available/000-default.conf > /dev/null << 'EOF'
<VirtualHost *:80>
    ServerName web01.it.support.lab
    Redirect permanent / https://web01.it.support.lab/
</VirtualHost>
EOF
```

---

## Step 6 – Reload Apache Configuration

```bash
sudo systemctl reload apache2
```

---

## Step 7 – Validate Configuration

Check Apache syntax:

```bash
sudo apache2ctl configtest
```

Expected output:

```
Syntax OK
```

Verify SSL module:

```bash
sudo apache2ctl -M | grep ssl
```

Expected:

```
ssl_module (shared)
```

Verify port 443 listening:

```bash
sudo ss -tupln | grep 443
```

---

## Step 8 – Network Validation from Domain Controller

From DC01:

```powershell
Test-NetConnection web01.it.support.lab -Port 443
```

Expected:

```
TcpTestSucceeded : True
```

---

## Final Result

Accessing:

```
```

Successfully loads the IT.Support.Lab Internal Portal over HTTPS.

Browser displays "Not Secure" warning (expected behavior for self-signed certificates).

Encryption is active and TLS handshake is successful.

---

## Key Skills Demonstrated


- Apache VirtualHost configuration
- TLS implementation with self-signed certificates
- HTTP to HTTPS redirection
- SSL module management
- Service validation and troubleshooting
- DNS-integrated internal web hosting
- Layered infrastructure validation (Service → Network → Browser)

---


## Outcome

The internal Ubuntu web server is now secured with HTTPS and properly integrated into the Active Directory environment.

This completes the secure internal web service implementation phase of the IT Support Home Lab.
