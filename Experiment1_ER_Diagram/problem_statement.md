# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:Hospital Database

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
Hospital (choose one)

## ER Diagram:
![Untitled](https://github.com/user-attachments/assets/fdc05bdf-328e-471f-baa9-0f3754048e39)


## Entities and Attributes:
```
1.Patient
   Patient_ID (PK)
   Name
   DOB
   Address
   Phone
   Insurance_Provider
   Insurance_Number 
   
2.Doctor
   Doctor_ID (PK)
   Name
   Phone
   Department
   Specialization

3.Appointment
   Appointment_ID (PK)
   Date_Time
   Reason
   Patient_ID (FK)
   Doctor_ID (FK)

4.Medical_Record
   Record_ID (PK)
   Diagnosis
   Treatment
   Test_Results
   Appointment_ID (FK)

5.Billing
   Bill_ID (PK)
   Appointment_ID (FK)
   Amount
   Payment_Status
   Payment_Date
```
## Relationships and Constraints:
```
Patient — "makes" —> Appointment (One-to-Many)

Doctor — "attends" —> Appointment (One-to-Many)

Appointment — "has" —> Medical_Record (One-to-One)

Appointment — "generates" —> Billing (One-to-One)

```
## Extension (Prerequisite / Billing):
```
Billing has a 1:1 relationship with Appointment because:

Every appointment results in a bill.

A bill includes the amount, payment status (Paid/Unpaid/Pending), and payment date.

This avoids redundancy and links the financial side cleanly with clinical activity.
```
## Design Choices:
```
Patient and Doctor are natural entities — real-world actors.

Appointment links Patient and Doctor because an appointment is an interaction between them.

Medical Record is tied to an Appointment, because diagnosis and treatment happen during an appointment.

Billing is directly tied to Appointment, as each visit generates a billing entry.
```
## RESULT
Thus the the concepts of ER modeling by creating an ER diagram for a real-world application is created.
