# CareNest Clinic Booking System - QA & Security Audit

🔗 **Live Target Application:** [CareNest Clinic Booking](https://ahmedsayed28.github.io/Clinic-Booking-App/index.html)

---

## 📌 Project Overview

A comprehensive Manual Quality Assurance and Client-Side Security Assessment for the "CareNest" healthcare appointment booking platform. This project demonstrates strict adherence to Software Testing Life Cycle (STLC) principles, blending Functional validation with Web Penetration Testing methodologies.

---

## 🎯 Scope of Work

* **Functional Testing:** Validated core features (Registration, Authentication, Booking Engine, Payment Gateways, Lifecycle Management) using Boundary Value Analysis (BVA) and Equivalence Partitioning (EP).
* **Security Testing:** Conducted client-side vulnerability assessments focusing on state persistence, authentication flaws, and sensitive data exposure.
* **Responsive/UI Testing:** Ensured layout integrity and user experience across multiple device viewports.
* **Defect Management:** Documented and tracked bugs using Jira with full traceability back to original requirements.

---

## 🔍 Key Discoveries & Bug Reports Overview

| Bug ID | Summary / Title | Severity | Priority | Category / Module | Reporter | Assignee | Status |
| :--- | :--- | :---: | :---: | :--- | :--- | :--- | :---: |
| **HLTHCR3-114** | The Appointment Status Can Change From Available to Booked After Losing Connection With Internet | Medium | Medium | Booking Engine & Checkout (`HLTHCR3-4`) | Mustafa Mohamed | Ahmed Sayed | Done |
| **HLTHCR3-115** | The Appointment Status Can Not Change to Available After Cancellation | Medium | Medium | Post-Booking Lifecycle (`HLTHCR3-5`) | Mustafa Mohamed | Ahmed Sayed | Done |
| **HLTHCR3-116** | The Cancel Booking Is Enabled When Appointment Time Is Less Than or Equal to 24 Hours | Medium | Medium | Post-Booking Lifecycle (`HLTHCR3-5`) | Mustafa Mohamed | Ahmed Sayed | Done |
| **HLTHCR3-117** | The Slot Status Does Not Change From Available to Booked in Doctor's Page After Successful Transaction | Medium | Medium | Booking Engine & Checkout (`HLTHCR3-4`) | Mustafa Mohamed | Ahmed Sayed | Done |

---

## 🐛 Detailed Bug Reports

### HLTHCR3-114 — The Appointment Status Can Change From Available to Booked After Losing Connection With Internet

#### Meta Data

| Field | Value |
| :--- | :--- |
| **Bug ID** | HLTHCR3-114 |
| **Status** | Done |
| **Priority** | Medium |
| **Severity** | Medium |
| **Type** | Bug |
| **Reporter** | Mustafa Mohamed |
| **Assignee** | Ahmed Sayed |
| **Resolution** | Done |
| **Environment** | Lenovo-LOQ-15IRX9-Gaming-Laptop. |
| **Linked Test Case** | Relates to HLTHCR3-59- Verify that the date status can not c... (Done) |
| **Created / Resolved** | 09/Sep/26 — 11/Sep/26 |

#### Description
The system fails to properly handle a loss of network connectivity during the booking process. It allows a booking to be finalized even when the internet connection is dropped mid-transaction, violating the business requirement that incomplete or unverifiable transactions must not be confirmed.

#### Steps to Reproduce
1. Log into the application.
2. Select an available doctor and appointment slot.
3. Proceed with the booking process.
4. Disconnect the internet connection before completing the booking.
5. Continue and confirm the booking process.

#### Expected Result
The booking process should be stopped and the appointment status should be available after the internet is working, and the application should display an error message or the system should show a website error page stating the page cannot be reached.

#### Actual Result
The booking process is completed successfully even after the internet connection is disconnected.

#### Attachments Reference
* 📹 Bug slot status change from Available to Booked.mp4

---

### HLTHCR3-115 — The Appointment Status Can Not Change to Available After Cancellation

#### Meta Data

| Field | Value |
| :--- | :--- |
| **Bug ID** | HLTHCR3-115 |
| **Status** | Done |
| **Priority** | Medium |
| **Severity** | Medium |
| **Type** | Bug |
| **Reporter** | Mustafa Mohamed |
| **Assignee** | Ahmed Sayed |
| **Resolution** | Done |
| **Environment** | Lenovo-LOQ-15IRX9-Gaming-Laptop. |
| **Linked Test Case** | Relates to HLTHCR3-84- Verify that the appointment status ch... (Done) |
| **Created / Resolved** | 10/Sep/26 — 11/Sep/26 |

#### Description
The system fails to release a cancelled appointment slot back to the schedule. It continues to treat the slot as booked and blocks new reservations for it even after the original booking has been cancelled, violating the business requirement that a cancelled slot must immediately become available again.

#### Steps to Reproduce
1. Open the booking page and cancel an upcoming booking with Dr. Amelia Carter on 10 September at 01:00 PM.
2. The booking shows in past/cancelled bookings.
3. Go to Find a Doctor and choose the same doctor with the same slot (Dr. Amelia Carter on 10 September at 01:00 PM).
4. The application system showed an error message "This slot has just been booked. Please choose another time."

#### Expected Result
The system should successfully confirm the booking for the time slot, because the booking was cancelled and the slot should be available.

#### Actual Result
The system blocks the booking and shows an error message saying that the appointment slot is already booked, although it was cancelled.

#### Attachments Reference
* 📹 Bug slot status change remain booked after cancellation.mp4

---

### HLTHCR3-116 — The Cancel Booking Is Enabled When Appointment Time Is Less Than or Equal to 24 Hours

#### Meta Data

| Field | Value |
| :--- | :--- |
| **Bug ID** | HLTHCR3-116 |
| **Status** | Done |
| **Priority** | Medium |
| **Severity** | Medium |
| **Type** | Bug |
| **Reporter** | Mustafa Mohamed |
| **Assignee** | Ahmed Sayed |
| **Resolution** | Done |
| **Environment** | Lenovo-LOQ-15IRX9-Gaming-Laptop. |
| **Linked Test Case** | Verify that the cancel booking is dis... (Done) Relates to HLTHCR3-85 |
| **Created / Resolved** | 10/Sep/26 — 11/Sep/26 |

#### Description
The system fails to enforce the 24-hour cancellation window. It allows a patient to cancel an upcoming appointment even when the appointment is scheduled within the next 24 hours, violating the business requirement that cancellations must be blocked once that window is reached.

#### Steps to Reproduce
1. Selected an appointment with Dr. Noah Williams for 10 September at 9:00 AM.
2. Went to the booking page, kept 'Booking for myself' and 'Pay at clinic (Cash)' selected, and clicked on "Confirm Appointment."
3. Clicked on "My bookings" and selected "Cancel booking" for this upcoming appointment (scheduled the same day, and less than or equal to 24 hours away).
4. Confirmed the cancellation, and the system successfully allowed the cancellation instead of blocking it due to the 24-hour requirement before cancelling.

#### Expected Result
The system application should prevent the cancellation if it is applied within a short time (less than or equal to 24 hours) before the appointment.

#### Actual Result
The system application allowed the cancellation without checking any time restrictions.

#### Attachments Reference
* 📹 Bug booking is enabled when appointment less than 24 after cancellation.mp4

---

### HLTHCR3-117 — The Slot Status Does Not Change From Available to Booked in Doctor's Page After Successful Transaction

#### Meta Data

| Field | Value |
| :--- | :--- |
| **Bug ID** | HLTHCR3-117 |
| **Status** | Done |
| **Priority** | Medium |
| **Severity** | Medium |
| **Type** | Bug |
| **Reporter** | Mustafa Mohamed |
| **Assignee** | Ahmed Sayed |
| **Resolution** | Done |
| **Environment** | Lenovo-LOQ-15IRX9-Gaming-Laptop. |
| **Linked Test Case** | Verify that the slot status change fr... (Done) Relates to HLTHCR3-58 |
| **Created / Resolved** | 10/Sep/26 — 11/Sep/26 |

#### Description
The system fails to update the appointment slot status after a booking is completed. It allows a slot to remain marked as available on the doctor's page even though the transaction was completed successfully, violating the business requirement that slot availability must always reflect the current booking state.

#### Steps to Reproduce
1. Went to "My bookings", where there is already a confirmed booking with Dr. Sofia Patel on 11 September at 12:30 PM.
2. Opened "Find doctors", selected Dr. Sofia Patel and looked at her available schedule.
3. Noticed that the slot for 11 September at 12:30 PM was still clickable, so clicked on it.
4. Was redirected to the "Confirm your booking" page and clicked on "Confirm appointment."
5. The system blocked the booking at the final stage with the message "This slot has just been booked. Please choose another time."

#### Expected Result
The slot status should automatically change from "Available" to "Booked" on the doctor's page after completing a successful transaction.

#### Actual Result
The slot status remains "Available" on the doctor's page after completing a successful transaction.

#### Attachments Reference
* 📹 Bug slot status not change from available to booked.mp4

---

## 📂 Repository Structure

```text
├── /Requirements
│   └── SRS_CareNest_Booking.pdf        # Software Requirements Specification
├── /Bug_Reports
│   ├── HLTHCR3_Bug_Reports_1.pdf        # Bug Reports for HLTHCR3-114 & HLTHCR3-117
│   ├── HLTHCR3_Bug_Reports_2.pdf        # Bug Reports for HLTHCR3-115 & HLTHCR3-116
│   └── /Video_Evidence
│       ├── Bug_slot_status_change_from_Available_to_Booked.mp4
│       ├── Bug_slot_status_not_change_from_available_to_booked.mp4
│       ├── Bug_slot_status_change_remain_booked_after_cancellation.mp4
│       └── Bug_booking_is_enabled_when_appointment_less_than_24_after_cancellation.mp4
└── README.md                            # Comprehensive Audit Overview & Documentation
```

---

## 🛠️ Tools & Methodologies Used

* **Testing Techniques:** Black-box testing, Boundary Value Analysis (BVA), Equivalence Partitioning (EP).
* **Security & Inspection:** Chrome Developer Tools (Network & Application tabs), State Persistence Analysis.
* **Test Management & Tracking:** Jira (Test Execution, Bug Tracking, Traceability).
