# HealthCare3 — Bug Report Log

**Module:** Booking Engine & Checkout Process (HLTHCR3-4)

---

## HLTHCR3-114 — The Appointment Status Can Change From Available to Booked After Losing Connection With Internet

### Meta Data

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

### Description

The system fails to properly handle a loss of network connectivity during the booking process. It allows a booking to be finalized even when the internet connection is dropped mid-transaction, violating the business requirement that incomplete or unverifiable transactions must not be confirmed.

### Steps to Reproduce

1. Log into the application.
2. Select an available doctor and appointment slot.
3. Proceed with the booking process.
4. Disconnect the internet connection before completing the booking.
5. Continue and confirm the booking process.

### Expected Result

The booking process should be stopped and the appointment status should be available after the internet is working, and the application should display an error message or the system should show a website error page stating the page cannot be reached.

### Actual Result

The booking process is completed successfully even after the internet connection is disconnected.

### Attachments Reference

* 📹 Bug slot status change from Available to Booked.mp4

---

## HLTHCR3-117 — The Slot Status Does Not Change From Available to Booked in Doctor's Page After Successful Transaction

### Meta Data

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

### Description

The system fails to update the appointment slot status after a booking is completed. It allows a slot to remain marked as available on the doctor's page even though the transaction was completed successfully, violating the business requirement that slot availability must always reflect the current booking state.

### Steps to Reproduce

1. Went to "My bookings", where there is already a confirmed booking with Dr. Sofia Patel on 11 September at 12:30 PM.
2. Opened "Find doctors", selected Dr. Sofia Patel and looked at her available schedule.
3. Noticed that the slot for 11 September at 12:30 PM was still clickable, so clicked on it.
4. Was redirected to the "Confirm your booking" page and clicked on "Confirm appointment."
5. The system blocked the booking at the final stage with the message "This slot has just been booked. Please choose another time."

### Expected Result

The slot status should automatically change from "Available" to "Booked" on the doctor's page after completing a successful transaction.

### Actual Result

The slot status remains "Available" on the doctor's page after completing a successful transaction.

### Attachments Reference

* 📹 Bug slot status not change from available to booked.mp4
