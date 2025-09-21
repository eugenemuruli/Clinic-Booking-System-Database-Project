Clinic Booking System   
Use Case: Clinic Booking & Patient Management System  
Technology: MySQL Relational Database

📌 Overview

This project implements a fully relational Clinic Booking System designed to manage patients, doctors, appointments, medical records, billing, and services offered. It demonstrates core database concepts including:

- Proper table normalization
- Primary & Foreign Key constraints
- One-to-One, One-to-Many, and Many-to-Many relationships
- Data integrity via NOT NULL, UNIQUE, and CHECK constraints

The system is suitable for small to medium-sized clinics and can be extended into a full-stack application with a frontend and backend API.

🗃️ Database Schema Summary

The database contains **8 core tables**:

| Table             | Purpose                                                                 |
|-------------------|-------------------------------------------------------------------------|
| `Patients`        | Stores patient personal and contact information                         |
| `Doctors`         | Stores doctor profiles, specialization, and license info                |
| `Services`        | Lists medical services offered (e.g., Consultation, Vaccination.)  |
| `DoctorServices`  | Junction table linking doctors to the services they provide (M:N)       |
| `Appointments`    | Tracks scheduled visits: who, when, with whom, and for what service     |
| `MedicalRecords`  | Stores diagnosis and notes per appointment (1:1 with Appointments)      |
| `Billing`         | Manages payment status and amounts for each appointment (1:1)           |
| `Users`           | System login accounts for clinic staff (optional extension point)       |

Key Relationships Explained
One-to-Many Relationships

- **One Patient → Many Appointments**  
  A patient can book multiple appointments over time.

- **One Doctor → Many Appointments**  
  A doctor sees many patients through scheduled appointments.

- **One Service → Many Appointments**  
  A service (e.g., “Dental Checkup”) can be booked multiple times.
 Many-to-Many Relationship

- Doctors  Services  
  A doctor can offer multiple services, and a service can be provided by multiple doctors.  
  → Resolved via the `DoctorServices` junction table.

One-to-One Relationships

- Appointment → MedicalRecord 
  Each appointment has at most one medical record (created after visit).

- Appointment → Billing  
  Each appointment generates one bill.

- User → Staff/Doctor (Conceptual) 
  The `Users` table is designed to support login for staff. In an extended system, it could link 1:1 to a `Staff` or `Doctor` record.
   Constraints & Data Integrity
Primary Keys: Auto-incrementing IDs ensure unique identification.
Foreign Keys: Enforce referential integrity (e.g., you can’t book an appointment for a non-existent patient).
NOT NULL: Critical fields (e.g., names, phone, dates) must be provided.
UNIQUE: Prevents duplicate emails, phone numbers, usernames, or license numbers.
CHECK Constraints:
  - `duration_minutes > 0`
  - `base_price >= 0`
  - `start_time < end_time`
  - `amount_paid <= total_amount`


How to Use The Database

1. Setup  
   Save the `.sql` file (e.g., `clinic_booking_schema.sql`) and run it in MySQL:

   ```bash
   mysql -u root -p < clinic_booking_schema.sql
   ```

2. Connect  
   Use any MySQL client (MySQL Workbench, phpMyAdmin, CLI, or programming language like Python/Node.js).

3. Populate Sample Data
   You can write `INSERT` statements to add sample patients, doctors, and services.

4. Query & Extend 
   Build queries for reports, dashboards, or integrate with an application backend.



