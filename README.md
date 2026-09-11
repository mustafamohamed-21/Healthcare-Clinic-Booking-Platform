# CareNest Clinic Booking System - QA & Security Audit

🔗 **Live Target Application:** CareNest Clinic Booking

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

## 🧪 QA Test Case Repository

### 📊 Suite 1: Appointment Booking & Payment (15 Test Cases)

* **Total Test Cases:** 15
* **✓ Passed:** 13
* **X Failed/Blocked:** 2
* **▲ Linked Defects:** 2 (`HLTHCR3-114`, `HLTHCR3-117`)

| Test ID | Summary | Test Steps | Expected Result | Status | Defect / Link |
| :--- | :--- | :--- | :--- | :---: | :--- |
| **HLTHCR3-46** | verify that patient can booking using pay at clinic (Cash) Payment Method | **Pre-conditions:**<br>1. user is logged in.<br>2. patient selected an available date.<br>3. user is on the payment page.<br><br>**Steps:**<br>1. select pay at clinic (cash) as payment method.<br>2. click on 'Confirm appointment' button and completed booking. | 1. the booking is successfully completed, the appointment status is updated to booked.<br>2. the patient receive a message receipt with the payment details and a unique reference ID. | Pass | |
| **HLTHCR3-49** | verify that patient can booking using Credit Card payment Method | **Pre-conditions:**<br>1. user is logged in.<br>2. patient selected an available date.<br>3. user is on the payment page.<br><br>**Steps:**<br>1. select pay using credit card as payment method.<br>2. enter a valid card name (4532 7120 3984 1234).<br>3. enter a valid expiry date (04/28) and a valid (355) CVV.<br>4. ensure it is valid for payment using credit card.<br>5. click on 'Confirm appointment' button and completed booking. | 1. the booking is successfully completed, the appointment status is updated to booked.<br>2. the patient receives a message receipt containing the completed payment details and a unique reference ID. | Pass | |
| **HLTHCR3-52** | verify that Credit Card accepts a valid 16 numeric digits | **Pre-conditions:**<br>1. user is logged in.<br>2. user is on the payment page.<br>3. Credit Card is selected as payment method.<br><br>**Steps:**<br>1. enter all valid data in other required field in Credit Card payment.<br>2. enter a valid credit card number (4532 7120 3984 1234) in the card number field.<br>3. continue the payment process.<br>4. click on 'Confirm appointment' button. | 1. the system successfully accepted the credit card with 16digit -card number and processed to the next step. | Pass | |
| **HLTHCR3-53** | verify that system rejected the Credit Card due to invalid card numbers (fewer than 16 digits, more than 16 digits, special symbols characters) | **Pre-conditions:**<br>1. user is logged in.<br>2. user is on the payment page.<br>3. Credit Card is selected as payment method.<br><br>**Steps:**<br>1. enter all valid data in other required field in Credit Card payment.<br>2. enter a short number less than 16 digits (4532 7120 3984) in the card number field.<br>3. click on 'Confirm appointment' button.<br>4. enter a long number more than 16 digits (4532 7120 3984 1234 56) in the card number field.<br>5. click on 'Confirm appointment' button.<br>6. enter a non-numeric 16 digits (4532-ABCD-3984-1234) in the card number field.<br>7. click on 'Confirm appointment' button. | 1. the system rejects the entry card number in all scenarios.<br>2. the system displays an error message told the patient that the card number is invalid and must contain only 16 numeric digits. | Pass | |
| **HLTHCR3-54** | verify that system accepts expiry date valid MM/YY format | **Pre-conditions:**<br>1. user is logged in.<br>2. user is on the payment page.<br>3. Credit Card is selected as payment method.<br><br>**Steps:**<br>1. enter all valid data in other required field in Credit Card payment.<br>2. enter a valid expiry date format (02/29) that is equal to or later than the current date of the system.<br>3. continue the payment process.<br>4. click on 'Confirm appointment' button and completed booking. | 1. the system successfully accepted the credit card expiry date format and processed to the next step. | Pass | |
| **HLTHCR3-55** | verify that system rejects invalid MM/YY format and dates earlier than current month and year | **Pre-conditions:**<br>1. user is logged in.<br>2. user is on the payment page.<br>3. Credit Card is selected as payment method.<br><br>**Steps:**<br>1. enter all valid data in other required field in Credit Card payment.<br>2. enter an invalid expiry date format (01/24) that is earlier than the current date and try to continue the payment process.<br>3. click on 'Confirm appointment' button.<br>4. enter an invalid expiry date format (13/26 or AB/CD) and try to continue the payment process.<br>5. click on 'Confirm appointment' button. | 1. the system rejects both invalid formats and expired dates.<br>2. the system displays an error message requiring a valid MM/YY format and a non-expired date. | Pass | |
| **HLTHCR3-56** | verify that the system accepts a valid 3-digit numeric CVV value | **Pre-conditions:**<br>1. user is logged in.<br>2. user is on the payment page.<br>3. Credit Card is selected as payment method.<br><br>**Steps:**<br>1. enter all valid data in Credit Card payment.<br>2. enter exactly 3-digits into CVV field (123).<br>3. continue the payment process.<br>4. click on 'Confirm appointment' button and completed booking. | 1. the system successfully accepted the credit card 3-digit CVV and processed to the next step. | Pass | |
| **HLTHCR3-57** | verify that system rejected the Credit Card due to invalid CVV (fewer than 3 digits, more than 3 digits, special symbols characters) | **Pre-conditions:**<br>1. user is logged in.<br>2. user is on the payment page.<br>3. Credit Card is selected as payment method.<br><br>**Steps:**<br>1. enter other valid data in Credit Card field.<br>2. enter a short number less than 3 digits (12) in the CVV field.<br>3. click on 'Confirm appointment' button.<br>4. enter a long number more than 3 digits (1234) in the CVV field.<br>5. click on 'Confirm appointment' button.<br>6. enter a non-numeric 3 digits (AB1) in the card number field.<br>7. click on 'Confirm appointment' button. | 1. the system rejects the entry CVV number in all scenarios.<br>2. the system displays an error message told the patient that the CVV number is invalid and must contain only 3 numeric digits. | Pass | |
| **HLTHCR3-58** | verify that the slot status change from Available to Booked after successful Transaction | **Pre-conditions:**<br>1. user is logged in.<br>2. an available date exists.<br>3. user selected the date that exists.<br><br>**Steps:**<br>1. continue to the payment page.<br>2. enter all valid payment details and complete the payment process.<br>3. click to "confirm" button once to record the booking and check the status update.<br>4. check the slot status in the system dashboard. | 1. the transaction completes successfully with a confirmation message and a booking reference ID.<br>2. the slot status updates immediately from available to booked.<br>3. the slot is successfully locked and is not visible or selectable as available for other patients. | **Fail** | `HLTHCR3-117` |
| **HLTHCR3-59** | verify that the date status can not change from Available to Booked after losing connection with internet | **Pre-conditions:**<br>1. user is logged in.<br>2. an available date exists.<br>3. user selected the date that exists.<br><br>**Steps:**<br>1. select an "available" slot status and proceed to payment.<br>2. enter invalid payment details (e.g., insufficient funds, expired card) or simulate a payment gateway failure.<br>3. complete the transaction and observe the error message.<br>4. check the slot status.<br>5. complete a valid payment process, but suddenly lose your internet connection or system failure.<br>6. user return to the system and check the slot/status. | 1. The transaction fails or remains incomplete, displaying an error message or timeout message.<br>2. The slot status remains strictly as "Available". | **Fail** | `HLTHCR3-114` |
| **HLTHCR3-60** | verify that a unique 8-character reference ID is generated after successful booking | **Pre-conditions:**<br>1. user is logged in.<br>2. user selected an available slot.<br>3. user is on the payment page.<br><br>**Steps:**<br>1. complete the payment successfully.<br>2. finalize the booking.<br>3. check the generated receipt/reference ID (#BK-89A12).<br>4. verify the reference ID. | 1. the system generated a unique Reference ID containing 8-characters is generated and sent a message after the successful booking. | Pass | |
| **HLTHCR3-61** | verify that each successful booking generates unique reference ID | **Pre-conditions:**<br>1. user is logged in.<br>2. user selected an available slot.<br>3. user can complete multiple bookings successfully.<br><br>**Steps:**<br>1. complete a successful booking.<br>2. receives a message that has the generated reference ID (#BK-89A12).<br>3. complete another successful booking.<br>4. receives another message that has the generated reference ID (#BL-8CA14).<br>5. compare the generated reference IDs. | 1. each successful booking generates a unique reference ID different from other bookings. | Pass | |
| **HLTHCR3-62** | verify that the receipt displays all required details | **Pre-conditions:**<br>1. user is logged in.<br>2. user selected an available slot.<br>3. user is on the payment page.<br><br>**Steps:**<br>1. complete the payment successfully.<br>2. finalize the booking.<br>3. receives a receipt detail and verifies the generated booking receipt. | 1. the receipt is displayed with ID, Doctor, Date/Time, Address, Total Paid, and payment Method. | Pass | |
| **HLTHCR3-63** | verify that the receipt details match the completed booking data | **Pre-conditions:**<br>1. user has successfully completed a booking.<br>2. user receives a booking receipt.<br><br>**Steps:**<br>1. open the receipt.<br>2. compare the receipt details with the booking and payment data. | 1. all receipt details match the completed booking and payment data. | Pass | |
| **HLTHCR3-64** | verify that the booking receipt is not generated when booking is unsuccessful | **Pre-conditions:**<br>1. user is logged in.<br>2. user has selected an available slot.<br>3. user is on the payment page.<br><br>**Steps:**<br>1. cancel the booking or payment process.<br>2. check whether a receipt is generated or not. | 1. no booking receipt is generated when the booking is not completed successfully. | Pass | |

---

### 📊 Suite 2: Post-Booking Lifecycle Management (6 Test Cases)

* **Total Test Cases:** 6
* **✓ Passed:** 4
* **X Failed/Blocked:** 2
* **▲ Linked Defects:** 2 (`HLTHCR3-115`, `HLTHCR3-116`)

| Test ID | Summary | Test Steps | Expected Result | Status | Defect / Link |
| :--- | :--- | :--- | :--- | :---: | :--- |
| **HLTHCR3-80** | verify that the upcoming booking shown in dashboard views | **Pre-conditions:**<br>1. user is logged in.<br>2. user has selected an available slot.<br>3. user successfully completed the payment process.<br><br>**Steps:**<br>1. open the user dashboard view.<br>2. open upcoming view.<br>3. check the booking is shown. | 1. the upcoming bookings are displayed correctly in upcoming view.<br>2. the booking details are shown correctly. | Pass | |
| **HLTHCR3-81** | verify that the past/cancelled booking shown in dashboard views | **Pre-conditions:**<br>1. user is logged in.<br>2. user has selected an available slot.<br>3. user has successfully completed the payment process.<br><br>**Steps:**<br>1. open the user dashboard view.<br>2. click 'cancel' booking button.<br>3. open past/cancelled view. | 1. the past/cancelled bookings are displayed correctly in past/cancelled view.<br>2. the cancelled booking is not shown as an upcoming booking. | Pass | |
| **HLTHCR3-82** | verify that the cancellation booking button is active when appointment time is more than 24 hours | **Pre-conditions:**<br>1. user is logged in.<br>2. user has an upcoming booking.<br>3. appointment time is more than 24 hours from the current time.<br><br>**Steps:**<br>1. open upcoming bookings.<br>2. find the booking you want to delete.<br>3. click the 'cancel' booking button. | 1. cancel booking button is enabled.<br>2. user can delete booking. | Pass | |
| **HLTHCR3-83** | verify that the cancellation confirmation model is generated when click the cancellation button | **Pre-conditions:**<br>1. user is logged in.<br>2. user has an upcoming booking.<br>3. appointment time is more than 24 hours from the current time.<br>4. cancel booking button is enabled.<br><br>**Steps:**<br>1. open upcoming booking.<br>2. click 'cancel' booking button.<br>3. check the confirmation model. | 1. user received a cancellation confirmation model and displayed correctly.<br>2. the system updates booking status to cancelled. | Pass | |
| **HLTHCR3-84** | verify that the appointment status changes to available after cancellation | **Pre-conditions:**<br>1. user is logged in.<br>2. user open upcoming bookings and has a booked appointment.<br>3. appointment time is more than 24 hours from the current time.<br><br>**Steps:**<br>1. click the 'cancel' booking button.<br>2. check the cancellation is done. | 1. appointment status changes from booked to available. | **Blocked** | `HLTHCR3-115` |
| **HLTHCR3-85** | verify that the cancel booking is disabled when appointment time is less than or equal 24 hours | **Pre-conditions:**<br>1. user is logged in.<br>2. user has an upcoming booking.<br>3. appointment time is less than or equal 24 hours from the current time.<br><br>**Steps:**<br>1. user open upcoming bookings.<br>2. find the booking.<br>3. check the cancel booking.<br>4. open upcoming bookings.<br>5. find the booking.<br>6. hover your mouse over the disabled 'cancel' booking button. | 1. cancel booking button is disabled.<br>2. user cannot click the button and delete booking.<br>3. the system displays a message "Cancellations are only allowed up to 24 hours before the appointment" when hover your mouse. | **Fail** | `HLTHCR3-116` |

---

## 📂 Repository Structure

```text
├── /Requirements
│   └── SRS_CareNest_Booking.pdf        # Software Requirements Specification
├── /Test_Cases
│   ├── Test_Case_1.pdf                  # 15 Test Cases for Booking & Payment Engine
│   └── Test_Case_2.pdf                  # 6 Test Cases for Post-Booking Lifecycle
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
