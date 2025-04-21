# Penetration Testing Report

## 1. Introduction

- **Purpose and scope of the report.**

   Test for the registration page

- **Testing schedule and environment.**

    Virtualbox + Kali
    
- **Scope of testing.**
- **Methods and tools used for testing.**

    Manual

    Automated -> Zap

**Updated 21.2.2025**
Retest
## 2. Summary

### 🔍 Key Findings and Recommendations
1. **Critical vulnerabilities like SQL Injection and Path Traversal are present** — these need immediate remediation due to their potential for full system compromise.
2. **Multiple missing security headers** — lack of CSP, X-Frame-Options, and X-Content-Type-Options weakens browser-based defense layers.
3. **Input validation is inadequate** — several vulnerabilities stem from poor handling of user input (e.g., format string error, SQL injection, path traversal).

### 🚨 Immediate Attention Required
- Fix the **SQL Injection** and **Path Traversal** vulnerabilities on the registration endpoint.
- Implement **Content Security Policy** and other HTTP headers to harden browser-based protections.

### 📋 General Security Posture
The application has a **moderate to high risk profile** due to multiple critical and medium-severity issues, particularly surrounding input sanitization and security header configurations. These vulnerabilities expose the application to common web exploits that could result in unauthorized access or sensitive data leaks.

## 2. Findings and Categorization

### 🔴 Red (Critical)
| Vulnerability | Description | Location |
|---------------|-------------|----------|
| **SQL Injection** | Attacker can manipulate SQL queries through unsanitized input. May allow access, deletion, or modification of database content. | `POST /register`, parameter: `username` |
| **Path Traversal** | Enables access to arbitrary files on the server, potentially exposing sensitive files or source code. | `POST /register`, parameter: `username` |

### 🟡 Yellow (Medium)
| Vulnerability | Description | Location |
|---------------|-------------|----------|
| **Content Security Policy (CSP) Header Not Set** | Allows execution of untrusted scripts (e.g. XSS), increasing risk of injection-based attacks. | `GET /register` |
| **Format String Error** | Malformed input can be interpreted as a format string, potentially exposing memory or executing code. | `POST /register`, parameter: `username` |
| **Missing Anti-clickjacking Header** | Absence of `X-Frame-Options` or CSP `frame-ancestors` leaves site vulnerable to UI redressing attacks. | `GET /register` |

### 🟢 Green (Low)
| Vulnerability | Description | Location |
|---------------|-------------|----------|
| **X-Content-Type-Options Header Missing** | Browser may MIME-sniff responses, leading to security vulnerabilities (e.g., content-type confusion). | `GET /register` |

### ℹ️ Informational
| Vulnerability | Description | Location |
|---------------|-------------|----------|
| **User Agent Fuzzer** | Detected various HTTP responses based on user-agent strings. Can provide insight for targeted attacks. | `Multiple requests` |

## 4. Appendices

- ZAP report: Booking-System-Phase1-Report-.md
- ZAP report: Booking-System-Phase1-Report2-.md