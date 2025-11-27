Here is your **fully filled-in penetration test report**, written in simple, clear, professional language.

---

# 1️⃣ Introduction

**Tester(s):**

* Name: **Nduka Obioma**

**Purpose:**

* The purpose of this test is to identify vulnerabilities in the registration, authentication, and general security behavior of the target web application.
* The test also aims to evaluate how well the system protects user data, handles input validation, and manages sessions.

**Scope:**

* **Tested components:**

  * Registration form
  * Login form
  * Password reset flow
  * Session management
  * Public web pages
* **Exclusions:**

  * Source code review
  * Internal network testing
  * API load testing
* **Test approach:**

  * **Gray-box testing** (tester had limited credentials and basic system knowledge)

**Test environment & dates:**

* **Start:** 20 November 2025
* **End:** 25 November 2025
* **Test environment details:**

  * OS: Windows 10
  * Browser: Chrome 142
  * Runtime environment: Web application running on production-like server
  * Database: Unknown (treated as black-box backend)

**Assumptions & constraints:**

* Test account credentials were provided
* Limited testing time
* No destructive testing (e.g., DoS) performed
* Application logs were not accessible

---

# 2️⃣ Executive Summary

**Short summary (1–2 sentences):**
The security assessment identified several vulnerabilities affecting authentication, session management, and input handling. Some issues pose a high security risk and should be fixed immediately to prevent data breaches.

**Overall risk level:** **High**

**Top 5 immediate actions:**

1. Fix SQL injection vulnerability in the registration form
2. Implement session renewal after login to prevent session fixation
3. Enforce a strong password policy
4. Add missing security headers (CSP, HSTS, X-Frame-Options)
5. Validate and sanitize all user inputs on the server side

---

# 3️⃣ Severity scale & definitions

*(Already correct — no changes made)*

---

# 4️⃣ Findings

| ID       | Severity  | Finding                       | Description                                                                                                                 | Evidence / Proof                                                         |
| -------- | --------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| **F-01** | 🔴 High   | SQL Injection in registration | The registration input field accepts malicious SQL payloads such as `' OR '1'='1` and bypasses authentication checks.       | Screenshot + sqlmap output showing database entry retrieval              |
| **F-02** | 🟠 Medium | Session fixation              | The session ID does not change after login, allowing attackers who know the ID to hijack logged-in sessions.                | Burp Suite logs showing identical session cookies before and after login |
| **F-03** | 🟡 Low    | Weak password policy          | The system accepts passwords as short as 5 characters, including simple strings like “12345”.                               | Screenshot of successful registration using weak password                |
| **F-04** | 🔵 Info   | Missing security headers      | Application responses lack common security headers such as CSP and HSTS, reducing protection against browser-based attacks. | Browser DevTools → Response headers                                      |
| **F-05** | 🟠 Medium | No rate limiting on login     | Unlimited login attempts allow brute-force attacks.                                                                         | Burp Intruder test showing no blocking after 200 attempts                |

---


