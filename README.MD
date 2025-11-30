
# Amazin – Vulnerable E-Commerce Web Application  
![Status](https://img.shields.io/badge/Project-Intentionally%20Vulnerable-red?style=for-the-badge)
![Language](https://img.shields.io/badge/PHP-8.x-blue?style=for-the-badge)
![Database](https://img.shields.io/badge/SQLite-Included-lightgrey?style=for-the-badge)
![WAF](https://img.shields.io/badge/WAF-Built--In-success?style=for-the-badge)
![Education](https://img.shields.io/badge/Purpose-Security%20Training-orange?style=for-the-badge)

Amazin is a purposely vulnerable PHP-based online store built for **penetration testing**, **web security training**, and **demo purposes**.  
It mimics a real e-commerce platform — except the vulnerabilities are intentional.

> ⚠️ **Never deploy this publicly.** Local lab use only.


# ✨ Overview

Amazin simulates a simple online storefront with users, uploads, and admin features.  
It's intentionally designed to demonstrate:

- Exploitation (insecure state)  
- Mitigation (secured state using WAF)

The integrated WAF lets you switch between **vulnerable** and **protected** modes instantly.


## 🕳️ The Application Intentionally Includes

- SQL Injection (SQLi)
- Stored Cross-Site Scripting (XSS)
- Insecure Direct Object References (IDOR)
- Broken Access Control
- Unrestricted File Upload
- Remote Code Execution (RCE)
- Sensitive Data Exposure
- CSRF
- Weak Authentication

Each vulnerability behaves like it would in a real insecure PHP app.


## 🛠️ Setup Guide (Windows + PHP + SQLite)

### 1. Install PHP (Windows)

Download PHP from the official Windows downloads page:

👉 **https://windows.php.net/download/**

Install PHP, Go to `C:\php`

then,

- Duplicate `php.ini-development` → rename to `php.ini`
- Open `php.ini`
- Enable SQLite modules: <br>
**extension=pdo_sqlite** <br> **extension=sqlite3**

2. Unzip the folder **AmazinVulnShop.zip**

3. Navigate to the folder from the terminal and run this: 

   ```bash
   php -S localhost:80
Open the site:
👉 'http://127.0.0.1'


## 🔓 Making the App Vulnerable

The app ships with the WAF turned ON by default (BLOCK mode).
This means attacks are blocked unless you disable the firewall.

To enable full vulnerability mode:
- Login as admin
- Open the Admin Dashboard
- Change WAF Mode → OFF

All vulnerabilities become active again
Use this to demo before/after scenarios.


## 🔑 Default Credentials

**👑 Admin**  <br> Username: `admin` | Password: ` admin`  <br> **👤 User Accounts**  <br> Username: `michael` | Password: ` michael` <br> Username: `john` | Password: ` john `


## 🛡 Built-In Web Application Firewall (WAF)
This project includes a lightweight, fully integrated WAF (waf.php) that intercepts every request.

 **🌐 Default Behavior** <br> 
WAF is ON by default <br> 
Mode = BLOCK <br> 
Attacks are blocked with a styled WAF block page <br> 
All events logged to /waf_logs/waf.log <br> 
Toggle modes via Admin Dashboard <br> 

**⚙️ WAF Modes** <br> 
Mode	Description <br> 
BLOCK	Blocks & logs attacks <br> 
DETECT	Logs only (no blocking) <br> 
OFF	App becomes fully vulnerable <br> 


## 🧠 WAF Provides Protection Against:

- SQL Injection payloads
- XSS vectors `(<script>, onerror=, javascript:)`
- Command injection attempts
- Execution of uploaded .php files
- Unsafe file uploads (only jpg/jpeg/png allowed when WAF is ON)
- IDOR on profile.php?id=
- GET-based credential leaks
- Admin/user dashboard access restrictions

The WAF exists for demonstration, not for real security.


## 📁 WAF Log Viewer

The Admin Dashboard includes a WAF Logs section showing the latest 50 events, including:

- Timestamp
- Rule ID
- Block reason
- Requested URI
- IP address

Raw logs live here:
/waf_logs/waf.log

Great for teaching intrusion detection and viewing real-time attack attempts.


## ⚠️ Known Limitations
- Not responsive
-  Optimized for 1920x1080 (Full HD) screens, Zoom the webpage until it fits your screen properly.
-  May break on smaller or mobile displays
- WAF is intentionally simple (regex-based)
- Educational/CTF tool, not production software


## 📛 Legal  
- Not affiliated with Amazon  
- Logos, names, and branding are parodies  
- For ethical, educational use only


# 🔍 Vulnerabilities Included

This app includes several intentionally insecure features for training purposes. Here are examples, how to trigger them, and how to prevent them:

### 1. SQL Injection
- **Example Payload:** `admin' --`
- **Prevention:** Use prepared statements with parameterized queries to sanitize inputs and block SQL injection.

### 2. Stored Cross-Site Scripting (XSS)
- **Payload:** `<script>alert("XSS");</script>`
- **Prevention:** Escape output with `htmlspecialchars()` and validate/sanitize inputs to reject scripts.

### 3. Broken Access Control
- **Example:** Visit `http://localhost:8000/users.php` without logging in.
- **Bonus:** `robots.txt` exposes paths like `/users.php`, `/uploads/`
- **Prevention:** Add session checks to protect sensitive pages. Avoid listing sensitive routes in `robots.txt`.

### 4. Unrestricted File Upload
- **Example Upload:** `info.php`
- **Test URL:** `http://localhost:8000/uploads/info.php`
- **Prevention:** Validate file types, use `basename()` to block directory traversal, and store uploads outside the web root.

### 5. Remote Code Execution (RCE)
- **Example Upload:** `shell.php`
- **Test URL:** `http://localhost:8000/uploads/shell.php?cmd=dir`
- **Prevention:** Disable PHP execution in upload folders (e.g. via `.htaccess`), sanitize user input, and avoid using `eval()` or `system()` on raw data.

### 6. Insecure Direct Object Reference (IDOR)
- **Example:** `http://localhost:8000/profile.php?id=1`
- **Prevention:** Verify user ownership with session checks before exposing data tied to IDs. Prefer indirect references.

### 7. Sensitive Data Exposure
- **Example:** `http://localhost:8000/login.php?username=admin&password=admin`
- **Prevention:** Use `method="POST"` instead of GET for forms. Never log plaintext passwords. Hash with `password_hash()`.





