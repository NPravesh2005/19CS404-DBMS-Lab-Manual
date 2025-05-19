# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - Student Name

## Scenario Chosen:

HOSPITAL

## ER Diagram:
![DBMS workshop](https://github.com/user-attachments/assets/149897cd-fd2e-4d85-a1cc-f805bf8ffaa8)

## Entities & Attributes:
Department: DepartmentID (PK), DepartmentName, DepartmentHead

Doctor: DoctorID (PK), FullName, PhoneNumber, Email, Specialization, WorkSchedule

Patient: PatientID (PK), FullName, DOB, Gender, Address, PhoneNumber, Email, InsuranceDetails

Appointment: AppointmentID (PK), AppointmentDate, Time, ReasonForVisit

MedicalRecord: MedicalRecordID (PK), Diagnosis, Treatments, Medications, TestResults, OtherInfo

Billing: BillID (PK), TotalAmount, PaymentStatus, BillingDate

Payment: PaymentID (PK), PaymentDate, AmountPaid, PaymentMethod

## Relationships:
Employs (1:N): Department → Doctor

Schedules (1:N): Patient → Appointment

Assigned To (1:N): Doctor → Appointment

Generates (1:1): Appointment → MedicalRecord

Results In (1:1): Appointment → Billing

Settles (1:1): Billing → Payment

## Billing Extension:
Each appointment leads to a billing, which is settled by a payment. Billing and Payment are connected 1:1 for clear transaction tracking.

## Design Notes:
Core entities reflect hospital roles.

Relationships and cardinality match real-world hospital workflows.

Billing handled via Appointment → Billing → Payment chain.

## RESULT:
Thus, the Entity-Relationship (ER) Diagram have been created successfully.
