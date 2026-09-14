# HealthCare3 — Bug Report Log

**Module:** Post-Booking Lifecycle Management (HLTHCR3-5)

---

## HLTHCR3-115 — The Appointment Status Can Not Change to Available After Cancellation

### Meta Data

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

### Description

The system fails to release a cancelled appointment slot back to the schedule. It continues to treat the slot as booked and blocks new reservations for it even after the original booking has been cancelled, violating the business requirement that a cancelled slot must immediately become available again.

### Steps to Reproduce

1. Open the booking page and cancel an upcoming booking with Dr. Amelia Carter on 10 September at 01:00 PM.
2. The booking shows in past/cancelled bookings.
3. Go to Find a Doctor and choose the same doctor with the same slot (Dr. Amelia Carter on 10 September at 01:00 PM).
4. The application system showed an error message "This slot has just been booked. Please choose another time."

### Expected Result

The system should successfully confirm the booking for the time slot, because the booking was cancelled and the slot should be available.

### Actual Result

The system blocks the booking and shows an error message saying that the appointment slot is already booked, although it was cancelled.

### Attachments Reference

* 📹 [Bug slot status change remain booked after cancellation.mp4](https://github.com/mustafamohamed-21/Healthcare-Clinic-Booking-Platform/blob/main/Bug_Report%202/Bug%20slot%20status%20change%20remain%20booked%20after%20cancellation.mp4)

---

## HLTHCR3-116 — The Cancel Booking Is Enabled When Appointment Time Is Less Than or Equal to 24 Hours

### Meta Data

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

### Description

The system fails to enforce the 24-hour cancellation window. It allows a patient to cancel an upcoming appointment even when the appointment is scheduled within the next 24 hours, violating the business requirement that cancellations must be blocked once that window is reached.

### Steps to Reproduce

1. Selected an appointment with Dr. Noah Williams for 10 September at 9:00 AM.
2. Went to the booking page, kept 'Booking for myself' and 'Pay at clinic (Cash)' selected, and clicked on "Confirm Appointment."
3. Clicked on "My bookings" and selected "Cancel booking" for this upcoming appointment (scheduled the same day, and less than or equal to 24 hours away).
4. Confirmed the cancellation, and the system successfully allowed the cancellation instead of blocking it due to the 24-hour requirement before cancelling.

### Expected Result

The system application should prevent the cancellation if it is applied within a short time (less than or equal to 24 hours) before the appointment.

### Actual Result

The system application allowed the cancellation without checking any time restrictions.

### Attachments Reference

* 📹 [Bug booking is enabled when appointment less than 24 after cancellation.mp4](https://github.com/mustafamohamed-21/Healthcare-Clinic-Booking-Platform/blob/main/Bug_Report%202/Bug%20booking%20is%20enabled%20when%20appointment%20less%20than%2024%20after%20cancellation.mp4)
