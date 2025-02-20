# Penetration Testing Report

## Introduction
- Purpose: To identify vulnerabilities in the booking system's registration page.
- Scope: Testing the registration functionality for security flaws and GDPR compliance.
- Environment: Kali Linux, Docker, ZAP, Burp Suite.
- Methods: Gray-box testing, manual and automated tools.

## Summary
- Key Findings:
  1. SQL injection vulnerability in the registration form.
  2. Weak password policy allowing insecure passwords.
  3. Lack of encryption for sensitive data during transmission.
- Recommendations:
  1. Implement input validation to prevent SQL injection.
  2. Enforce a strong password policy.
  3. Use HTTPS to encrypt data in transit.

## Findings and Categorization
- **Red (Critical)**:
  - SQL injection vulnerability allows unauthorized database access.
- **Yellow (Medium)**:
  - Weak password policy increases the risk of brute-force attacks.
- **Green (Low)**:
  - Error messages reveal stack traces, which could aid attackers.

## Appendices
- ZAP and Burp Suite reports.
- Screenshots of vulnerabilities.
