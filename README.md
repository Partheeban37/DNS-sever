---

# DNS-Based Website Hosting using Apache & Custom DNS

This project demonstrates how to host a website using **Apache HTTP Server** and access it through a **custom DNS name** instead of using an IP address.
It covers Apache configuration, DNS resolution setup, and verification using both CLI tools and a web browser.

---

## 📌 Project Overview

* Hosted a website using Apache HTTP Server
* Configured a custom document root
* Implemented DNS-based access using a local DNS server
* Verified DNS resolution using `dig`
* Accessed the website using `curl` and a browser

---

## 🛠️ Technologies Used

* Apache HTTP Server (httpd)
* Linux (RHEL/CentOS & Ubuntu)
* systemd
* DNS (BIND / systemd-resolved)
* curl
* dig
* VMware Workstation

---

## 🧱 Project Architecture

```text
Client (Browser / curl)
        |
        v
DNS Resolution (www.parthi.local)
        |
        v
Apache Web Server (192.168.145.139)
        |
        v
Website Content (/srv/site1/index.html)
```

---

## ⚙️ Configuration Details

### 1️⃣ Apache Web Server Setup

Apache service installed, enabled, and running:

```bash
systemctl status httpd
```

Custom document root created:

```bash
/srv/site1
```

Website content:

```html
<h1>This is my DNS-based Website</h1>
```

---

### 2️⃣ Website Verification (Local)

```bash
curl http://localhost
```

Output:

```text
This is my DNS-based Website
```

---

### 3️⃣ DNS Configuration (Client Side)

DNS configured using `systemd-resolved`.

Edited configuration file:

```bash
/etc/systemd/resolved.conf
```

DNS server entry:

```text
DNS=192.168.145.139
```

Restart DNS service:

```bash
systemctl restart systemd-resolved
```

Verify DNS status:

```bash
resolvectl status
```

---

### 4️⃣ DNS Resolution Test

```bash
dig www.parthi.local
```

Result:

```text
www.parthi.local.  IN  A  192.168.145.139
```

---

### 5️⃣ Website Access via DNS

Using curl:

```bash
curl http://www.parthi.local
```

Using browser:

```text
http://www.parthi.local
```

Output:

```html
<h1>This is my DNS-based Website</h1>
```

---

## 🎯 Key Learning Outcomes

* Understanding DNS name resolution
* Apache web server configuration
* Practical experience with `systemctl`, `curl`, and `dig`
* Hosting websites using DNS instead of IP addresses

---

## 🚀 Future Enhancements

* Apache Virtual Hosts
* BIND9 forward and reverse DNS zones
* HTTPS using SSL/TLS
* Multiple DNS-based websites
* Cloud deployment (AWS / Azure)

---

## 👤 Author

**Parthi**
Aspiring Linux / Cloud / DevOps Engineer

GitHub: [https://github.com/Partheeban37](https://github.com/Partheeban37)

---

## 📜 License

This project is created for **learning and educational purposes**.

---
