# [Simple Banking App]


### Group Members: 
- Ruby Joy Belgado
- Donn Robert De Lima
- Marevel Regaspi

## **Introduction**
The Simple Banking App is a web-based application designed to facilitate secure and efficient basic banking operations for both regular users and administrators. Developed using the Flask framework and powered by a MySQL database, the app allows users to create accounts, log in securely, manage their personal and financial information, and perform transactions such as sending money to other users. Each user is assigned a unique account number and can view their current balance and transaction history. The application features robust security mechanisms including password hashing with bcrypt, session management with Flask-Login, CSRF protection, and rate limiting to prevent abuse. Administrators and managers have special access rights to monitor user activity and manage the system. The backend is configured through environment variables for flexibility across different deployment environments. Additionally, a well-structured SQL schema ensures data integrity and performance through the use of indexing and foreign key relationships. A reliable foundation for digital banking operations, balancing simplicity with the essential features needed in a secure financial platform.

## **Objecttives**

Provide secure authentication and authorization mechanisms.

Enable users to perform banking transactions safely.

Ensure administrative oversight via an admin interface.

Harden the application against common web vulnerabilities such as CSRF, rate limiting issues, and SQL injection.

## **Original Application Features**

User authentication using Flask-Login and bcrypt for password hashing.

Transaction logging and user account management.

CSRF protection with Flask-WTF.

Rate limiting using Flask-Limiter to prevent abuse of endpoints.

Database-backed with MySQL using SQLAlchemy.

## **Security Assessment Findings**

The security review of the system revealed several critical vulnerabilities and weaknesses that could expose it to both external and internal threats.

1. Weak Password Practices
  - Passwords stored with minimal validation.
  - Use of weak default credentials increases risk of unauthorized access.

2. Financial Calculation Risk
  - Use of floating-point values for balance calculations can lead to rounding errors.

3.  API Error Handling
  - Lack of error handling for PSGC API failures

4.   XSS Vulnerability
  - No output escaping on user-generated content (risk of Cross-Site Scripting).

5.  Data Transmission Security
  - No HTTPS enforcement; sensitive data may be intercepted.
  - Missing security headers reduce resistance to web attacks.

6.   Session and CSRF Issues
  - Incomplete session management.
  - CSRF token implementation is inconsistent or missing.

7.   Outdated Dependencies
  - Use of outdated third-party packages with known vulnerabilities.

8. Lack of Audit Logging
  - Admin/manager actions are untracked.
  - No audit trail exists for sensitive operations.


## **Security Improvements Implemented**


1. Password Security
  - Enforce minimum password length with required use of mixed characters, numbers, and uppercase letters.
  - Store all credentials using the **Bcrypt* hashing algorithm for strong protection.

2.  Financial Precision
  - Use decimal data types instead of float for all monetary computations to avoid rounding errors.

3.    CSRF Defense
  - Apply Flask-WTF CSRF protection across all forms in the application to prevent cross-site request forgery attacks.

4.    Rate Protection
  - Implement Flask-Limiter on critical endpoints  to prevent brute-force and request abuse.

5.  API Resilience**
  - Integrate timeout handling and fallback logic for PSGC API interactions to ensure system stability during failures.

6. Session Hardening
  - Configure secure session cookies with `HttpOnly`, `Secure`, and `SameSite` attributes to protect against hijacking.

- * Output Safety
  - Use **Jinja2 auto-escaping** with strict input sanitization to guard against injection attacks and XSS vulnerabilities.

- **📡 HTTP Security**
  - Enable **Flask-Talisman** to enforce HTTPS and add essential security headers such as `Content-Security-Policy` and `Strict-Transport-Security`.


## **Penetration Testing Report**

---
---

## **Remediation Plan**

---
---

## **Technology Stack**



## **Setup Instructions**

---
---
