# ⚡ Amazin – Vulnerable E-Commerce Web Application  
![Status](https://img.shields.io/badge/Project-Intentionally%20Vulnerable-red?style=for-the-badge)
![Language](https://img.shields.io/badge/PHP-8.x-blue?style=for-the-badge)
![Database](https://img.shields.io/badge/SQLite-Included-lightgrey?style=for-the-badge)
![WAF](https://img.shields.io/badge/WAF-Built--In-success?style=for-the-badge)
![Education](https://img.shields.io/badge/Purpose-Security%20Training-orange?style=for-the-badge)

Amazin is a purposely vulnerable PHP-based online store built for **penetration testing**, **web security training**, and **demo purposes**.  
It mimics a real e-commerce platform — except the vulnerabilities are intentional.

> ⚠️ **Never deploy this publicly.** Local lab use only.

---

# 📚 Table of Contents

- [✨ Overview](#-overview)
- [🕳️ Vulnerabilities Included](#️-vulnerabilities-included)
- [🛠️ Setup Guide (Windows + PHP + SQLite)](#️-setup-guide-windows--php--sqlite)
- [🔓 Making the App Vulnerable](#making-the-app-vulnerable)
- [🔑 Default Credentials](#-default-credentials)
- [🛡 Built-In Web Application Firewall (WAF)](#-built-in-web-application-firewall-waf)
- [📁 WAF Log Viewer](#-waf-log-viewer)
- [⚠️ Known Limitations](#️-known-limitations)
- [📛 Legal Notice](#-legal-notice)

---

# ✨ Overview

Amazin simulates a simple online storefront with users, uploads, and admin features.  
It's intentionally designed to demonstrate:

- exploitation (insecure state)  
- mitigation (secured state using WAF)

The integrated WAF lets you switch between **vulnerable** and **protected** modes instantly.

---

# 🕳️ Vulnerabilities Included

The application intentionally includes:

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

---

# 🛠️ Setup Guide (Windows + PHP + SQLite)

## 1. Install PHP (Windows)

Download PHP from the official Windows downloads page:

👉 **https://windows.php.net/download/**

Extract PHP, then:

- Duplicate `php.ini-development` → rename to `php.ini`
- Enable SQLite modules:

```ini
extension=pdo_sqlite
extension=sqlite3
2. Extract the project
Unzip the folder (e.g., AmazinVulnShop).

3. Start the development server
Run this inside the folder:

bash
Copy code
php -S localhost:8000
Open the site:

👉 http://localhost:8000

🔓 Making the App Vulnerable
The app ships with the WAF turned ON by default (BLOCK mode).
This means attacks are blocked unless you disable the firewall.

To enable full vulnerability mode:

Login as admin

Open the Admin Dashboard

Change WAF Mode → OFF

All vulnerabilities become active again

Use this to demo before/after scenarios.

🔑 Default Credentials
👑 Admin
Username: admin

Password: admin

👤 User Accounts
michael / michael

john / john

🛡 Built-In Web Application Firewall (WAF)
This fork includes a lightweight, fully integrated WAF (waf.php) that intercepts every request.

🌐 Default Behavior
WAF is ON by default

Mode = BLOCK

Attacks are blocked with a styled WAF block page

All events logged to /waf_logs/waf.log

Toggle modes via Admin Dashboard

⚙️ WAF Modes
Mode	Description
BLOCK	Blocks & logs attacks
DETECT	Logs only (no blocking)
OFF	App becomes fully vulnerable

🧠 WAF Provides Protection Against:
SQL Injection payloads

XSS vectors (<script>, onerror=, javascript:)

Command injection attempts

Execution of uploaded .php files

Unsafe file uploads (only jpg/jpeg/png allowed when WAF is ON)

IDOR on profile.php?id=

GET-based credential leaks

Admin/user dashboard access restrictions

The WAF exists for demonstration — not for real security.

📁 WAF Log Viewer
The Admin Dashboard includes a WAF Logs section showing the latest 50 events, including:

Timestamp

Rule ID

Block reason

Requested URI

IP address

Raw logs live here:

bash
Copy code
/waf_logs/waf.log
Great for teaching intrusion detection and viewing real-time attack attempts.

⚠️ Known Limitations
Not responsive

Designed for 1920×1080 (Full HD)

WAF is intentionally simple (regex-based)

Educational/CTF tool, not production software

📛 Legal Notice
Not affiliated with Amazon

Branding & names are parodies

For ethical and educational use only

