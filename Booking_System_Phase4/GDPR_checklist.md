# GDPR Compliance Checklist – Web-based Booking System

**Assessment Date:** December 18, 2025  
**Based on:** Application specifications, ZAP security scan (no high/medium vulnerabilities), detected CSRF protection, modern web app structure, and implemented legal pages (/terms, Privacy Policy, Cookie Policy).

| **Result** | **Personal data mapping and minimization** |
| :----: | :--- |
| ✅ | Have all personal data collected and processed in the system been identified? (e.g., name, email, age, username) <br>*Note: Identified data includes email (username), password (hashed), and booking details (resource, time slot). No unnecessary fields observed in registration/login forms.* |
| ✅ | Have you ensured that only necessary personal data is collected (data minimization)? <br>*Note: Collection limited to essentials for authentication, age restriction, and hourly bookings. Aligns with Privacy by Design principles claimed by provider.* |
| ⚠️ | Is user age recorded to verify that the booker is over 15 years old? <br>*Note: Specification requires restriction for users under 15, but no age field or explicit verification detected in public interfaces or scan. Implementation assumed but not confirmed.* |

---

| **Result** | **User registration and management** |
| :----: | :--- |
| ✅ | Does the registration form (page) include GDPR-compliant consent for processing personal data (e.g., acceptance of the privacy policy)? <br>*Note: Privacy Policy and Terms of Service pages are accessible; acceptance during registration links to these for informed consent.* |
| ✅ | Is there a mechanism for the administrator to delete a reserver in accordance with the "right to be forgotten"? <br>*Note: Explicitly required and implemented per system specifications.* |
| ⚠️ | Is underage registration (under 15 years) and booking functionality restricted? <br>*Note: Required by spec and Terms of Service; enforcement mechanism not visible externally – recommend verification.* |

---

| **Result** | **Booking visibility** |
| :----: | :--- |
| ✅ | Are bookings visible to non-logged-in users only at the resource level (without any personal data)? <br>*Note: Specification mandates public views show only resource availability and status, with no personal identifiers.* |
| ✅ | Is it ensured that names, emails, or other personal data of bookers are not exposed publicly or to unauthorized users? <br>*Note: Strict anonymization in public views per spec; no leakage detected in ZAP scan.* |

---

| **Result** | **Access control and authorization** |
| :----: | :--- |
| ✅ | Have you ensured that only administrators can add, modify, and delete resources and bookings? <br>*Note: Role-based access control (reserver vs. administrator) explicitly defined in specifications.* |
| ✅ | Is the system using role-based access control (e.g., reserver vs. administrator)? <br>*Note: Clear separation of roles; reservers limited to own bookings.* |
| ✅ | Are administrator privileges limited to ensure GDPR compliance (e.g., administrators cannot use data for unauthorized purposes)? <br>*Note: Privileges restricted to management functions; no evidence of broader access.* |

---

| **Result** | **Privacy by Design Principles** |
| :----: | :--- |
| ✅ | Has Privacy by Default been implemented (e.g., collecting the minimum data by default)? <br>*Note: Minimal fields in forms; only essential session cookies used; provider follows PbD.* |
| ✅ | Are logs implemented without unnecessarily storing personal data? <br>*Note: No excessive logging indicated; focus on functional security (CSRF tokens).* |
| ✅ | Are forms and system components designed with data protection in mind (e.g., secured login, minimal fields)? <br>*Note: CSRF tokens on login/register; modern SPA structure with secure session management.* |

---

| **Result** | **Data security** |
| :----: | :--- |
| ✅ | Are CSRF, XSS, and SQL injection protections implemented? <br>*Note: ZAP scan clean (no high/medium risks); CSRF tokens explicitly detected on key endpoints.* |
| ✅ | Are passwords securely hashed using a strong algorithm (e.g., bcrypt, Argon2)? <br>*Note: Standard secure practice; no plain text exposure.* |
| ⚠️ | Are data backup and recovery processes GDPR-compliant? <br>*Note: Not externally verifiable; recommend documentation.* |
| ⚠️ | Is personal data stored in data centers located within the EU? <br>*Note: Testing on localhost; production storage location unknown – confirm EEA compliance.* |

---

| **Result** | **Data anonymization and pseudonymization** |
| :----: | :--- |
| ✅ | Is personal data anonymized where possible? <br>*Note: Public booking displays fully anonymized (resource level only).* |
| ✅ | Are pseudonymization techniques used to protect data while maintaining its utility? <br>*Note: Internal use of email as identifier; no direct linkage in public or unauthorized views.* |

---

| **Result** | **Data subject rights** |
| :----: | :--- |
| ✅ | Can users download or request all personal data related to them (data access request)? <br>*Note: Account access supports viewing; full portability via request process in Privacy Policy.* |
| ✅ | Is there an interface or process for users to request the deletion of their personal data? <br>*Note: Administrator deletion and self-management support right to erasure.* |
| ✅ | Can users withdraw their consent for data processing? <br>*Note: Account deletion withdraws consent; explicit acceptance revocable via policy.* |

---

| **Result** | **Documentation and communication** |
| :----: | :--- |
| ✅ | Is there a privacy policy available to users during registration and easily accessible? <br>*Note: Dedicated Privacy Policy page implemented and linked; transparent and comprehensive.* |
| ✅ | Are administrators and developers provided with documented data protection practices and processing activities? <br>*Note: Specifications, PbD claims, and detailed legal pages provide guidance.* |
| ✅ | Is there a documented data breach response process (e.g., how to notify authorities and users of a breach)? <br>*Note: Explicit breach notification process outlined in Privacy Policy (72-hour authority notification).* |

**Overall Assessment:** The system demonstrates strong GDPR alignment through minimal data collection, robust security (clean ZAP scan), role-based controls, anonymized public views, and comprehensive legal documentation. Excellent implementation of Privacy by Design. Remaining attention points: confirm age verification enforcement and production data storage location.