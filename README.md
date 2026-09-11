# CareNest Clinic Booking System - QA & Security Audit

🔗 **Live Target Application:** [CareNest Clinic Booking](https://ahmedsayed28.github.io/Clinic-Booking-App/index.html)

---

## 📌 Project Overview

A comprehensive Manual Quality Assurance and Client-Side Security Assessment for the "CareNest" healthcare appointment booking platform. This project demonstrates strict adherence to Software Testing Life Cycle (STLC) principles, blending Functional validation with Web Penetration Testing methodologies.

---

## 🎯 Scope of Work

* **Functional Testing:** Validated core features (Registration, Authentication) using Boundary Value Analysis (BVA) and Equivalence Partitioning (EP).
* **Security Testing:** Conducted client-side vulnerability assessments focusing on state persistence, authentication flaws, and sensitive data exposure.
* **Responsive/UI Testing:** Ensured layout integrity and user experience across multiple device viewports.
* **Defect Management:** Documented and tracked bugs using Jira with full traceability back to original requirements.

---

## 🔍 Key Discoveries & Bug Reports

| Bug ID | Vulnerability / Defect | Severity | Category | Description |
| :--- | :--- | :---: | :--- | :--- |
| **HLTHCR3-114** | Connection Loss Booking Acceptance | Medium | Booking Engine (`HLTHCR3-4`) | System finalized booking even when network connection dropped mid-transaction. |
| **HLTHCR3-117** | Unupdated Doctor Slot Status | Medium | Booking Engine (`HLTHCR3-4`) | Slot status remained `Available` on doctor page after successful booking. |
| **HLTHCR3-115** | Cancelled Slot Lock Persistence | Medium | Post-Booking Lifecycle (`HLTHCR3-5`) | System failed to release cancelled appointment slot back to available schedule. |
| **HLTHCR3-116** | 24-Hour Cancellation Window Bypass | Medium | Post-Booking Lifecycle (`HLTHCR3-5`) | System allowed cancelling appointments within the restricted 24-hour window. |

---

## 📁 Repository Structure

* `/Bug_Report 1` : Contains bug reports and video evidence for `HLTHCR3-114` & `HLTHCR3-117` under the **Booking Engine & Checkout** module (`HLTHCR3-4`).
* `/Bug_Report 2` : Contains bug reports and video evidence for `HLTHCR3-115` & `HLTHCR3-116` under the **Post-Booking Lifecycle Management** module (`HLTHCR3-5`).
* `/Requirements` : Contains the original Software Requirements Specification (SRS) document, serving as the baseline for all test cases and traceability.
* `/Test_Case 1` : Covers 15 test execution scenarios for **Appointment Booking Methods** (Cash, Credit Card), card field validations (16 digits, MM/YY, CVV), and reference/receipt generation.
* `/Test_Case 2` : Covers 6 test execution scenarios for **Post-Booking Lifecycle Management**, including dashboard views (upcoming/cancelled), cancellation eligibility (>24h vs <=24h), and slot status updates upon cancellation.

---

## 🛠 Tools & Methodologies Used

* **Testing Techniques:** Black-box testing, Boundary Value Analysis, Equivalence Partitioning.
* **Security & Inspection:** Chrome Developer Tools (Network & Application tabs), State Persistence Analysis.
* **Test Management:** Jira (Test Execution, Bug Tracking, Traceability).
