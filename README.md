# [Simple Banking App]


### Group Members: 
- Ruby Joy Belgado
- Donn Robert De Lima
- Marevel Regaspi

---
---

## **Introduction**
The Simple Banking App is a web-based application designed to facilitate secure and efficient basic banking operations for both regular users and administrators. Developed using the Flask framework and powered by a MySQL database, the app allows users to create accounts, log in securely, manage their personal and financial information, and perform transactions such as sending money to other users. Each user is assigned a unique account number and can view their current balance and transaction history. The application features robust security mechanisms including password hashing with bcrypt, session management with Flask-Login, CSRF protection, and rate limiting to prevent abuse. Administrators and managers have special access rights to monitor user activity and manage the system. The backend is configured through environment variables for flexibility across different deployment environments. Additionally, a well-structured SQL schema ensures data integrity and performance through the use of indexing and foreign key relationships. A reliable foundation for digital banking operations, balancing simplicity with the essential features needed in a secure financial platform.

---
---

## **Objectives**

- Provide secure authentication and authorization mechanisms.
- Enable users to perform banking transactions safely.
- Ensure administrative oversight via an admin interface.
- Harden the application against common web vulnerabilities such as CSRF, rate limiting issues, and SQL injection.

---
---

## **Original Application Features**

User authentication using Flask-Login and bcrypt for password hashing.

Transaction logging and user account management.

CSRF protection with Flask-WTF.

Rate limiting using Flask-Limiter to prevent abuse of endpoints.

Database-backed with MySQL using SQLAlchemy.

---
---
<div align = 'center'>
<center>
<h1>Security Assessment Findings</h1>
</center>
</div>

### **OWASP ZAP Security QA Report**

### **Identified Vulnerabilities**

##### **Medium Priority**

| Vulnerability                          | Description                                                                 |
|----------------------------------------|-----------------------------------------------------------------------------|
| **Content Security Policy (CSP) Header Not Set** | The application does not set a CSP header, which helps prevent XSS and data injection attacks. |
| **Missing Anti-clickjacking Header**   | X-Frame-Options or Content-Security-Policy with frame-ancestors directive is missing, making the site vulnerable to clickjacking. |

#### **Low Priority**

| Vulnerability                          | Description                                                                 |
|----------------------------------------|-----------------------------------------------------------------------------|
| **Application Error Disclosure**       | The application reveals internal error messages that could help an attacker understand backend logic. |
| **Cookie Without Secure Flag**         | Cookies are set without the 'Secure' flag, meaning they could be transmitted over non-HTTPS connections. |
| **Cookie Without SameSite Attribute**  | Cookies are missing the SameSite attribute, which helps prevent CSRF attacks. |
| **Cross-Domain JavaScript Source File Inclusion** | External JavaScript files are included from different domains, increasing the risk of external code compromise. |
| **Information Disclosure - Debug Error Messages** | Debug-level error messages are exposed, potentially leaking sensitive information to attackers. |


The security review of the system also revealed several critical vulnerabilities and weaknesses that could expose it to both external and internal threats.

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

---
---

<div align = 'center'>
<center>
<h1>Security Improvements Implemented</h1>
</center>
</div>

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

---
---

## **Penetration Testing Report**

---
---

## **Remediation Plan**

---
---

## **Technology Stack**


### Backend
- **Python 3.x**
- **Flask 2.3.3** – Web framework
- **Flask-SQLAlchemy 3.0.5** – ORM for database interaction

### Database
- **MySQL / MariaDB** – Relational database system
  - Accessed via **PyMySQL 1.1.0**
  - Uses `DECIMAL` fields for precision in financial transactions

### Frontend
- **HTML5**, **CSS3**, **Bootstrap 5**
- **Jinja2 Templates** – Server-side rendering of dynamic content

### Security & Authentication
- **Flask-Bcrypt 1.0.1** – Password hashing
- **Flask-WTF 1.1.1** – Form handling with CSRF protection
- **WTForms 3.0.1** – Flexible form validation
- **Flask-Login 0.6.2** – User session management
- **itsdangerous 2.1.2** – Secure data serialization
- **cryptography** – General cryptographic functions

### Networking & API
- **requests 2.31.0** – HTTP requests for external APIs (e.g., PSGC GitLab)
- **email-validator** – Email format validation
- **Flask-Limiter 3.5.0** – Rate limiting for API and auth endpoints

###  Configuration & Environment
- **python-dotenv 1.0.0** – Environment variable management
- **Werkzeug 2.3.7** – Flask dependency for WSGI utilities


## **Setup Instructions**

---
---
