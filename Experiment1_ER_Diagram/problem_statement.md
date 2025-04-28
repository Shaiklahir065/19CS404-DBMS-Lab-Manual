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
University / Hospital (choose one)

## ER Diagram:
![er diagram](https://github.com/user-attachments/assets/ff8acca6-2788-4a3c-b928-d8f52a9ca9f7)


## Entities and Attributes:
- Doctor: Doctor id, Name, Phone, Specialization

- Patient: Patient id, Name, DOB, Phone, Address, Gender

- Department: Dept id, Dept name, Dept head

- Appointment: Appointment id, Appointment date and time, Reason for wait, Doctor id, Patient id

- Medical cover: Record id, Patient id, Doctor id, Prescribed medicine, Diagnoses

...

## Relationships and Constraints:
- Assigned to (Doctor–Department):

- Cardinality: Many Doctors → One Department

- Participation: Total (Doctor), Partial (Department)

- Conducts (Doctor–Appointment):

- Cardinality: One Doctor → Many Appointments

- Participation: Partial (Doctor), Total (Appointment)

- Schedule (Patient–Appointment):

- Cardinality: One Patient → Many Appointments

- Participation: Total (Patient), Total (Appointment)

- Has records (Appointment–Medical cover):

- Cardinality: One Appointment → One Medical cover

- Participation: Partial (Appointment), Total (Medical cover)

...

## Extension (Prerequisite / Billing):
- Extension: Billing
- New Entity: Billing
- Attributes:

  Billing id

  Appointment id (FK)

  Patient id (FK)

  Amount

  Payment status

  Payment method

  Billing date

- New Relationship:
- Billed for (Appointment–Billing):

   - Cardinality: One Appointment → One Billing

   - Participation: Partial (Appointment), Total (Billing)

- Why This Works:
  Billing is logically tied to an appointment.

It references the patient who is billed and can track whether payment is complete, partially paid, or pending.



## Design Choices:
- Design Choices
Entities:
- Doctor, Patient, Department, Appointment, Medical Cover
- These were chosen as entities because they represent core, real-world objects with multiple attributes and independent existence within a healthcare domain.

- Doctor and Patient are obvious primary actors.

- Department organizes doctors and provides structure.

- Appointment is a central event where interaction occurs between doctors and patients.

- Medical Cover (essentially medical records) captures diagnosis and prescriptions linked to appointments.

Relationships:
- Assigned to (Doctor–Department):
- Doctors work in departments, and this relationship ensures organizational hierarchy.

Conducts (Doctor–Appointment):
- Doctors conduct appointments. This shows the service aspect of their role.

Schedule (Patient–Appointment):
- Patients initiate the interaction by scheduling appointments.

Has Records (Appointment–Medical Cover):
- Every appointment may result in medical documentation. Capturing this ensures accurate tracking of treatment history.

Assumptions:
- Each appointment is with one doctor and one patient.

- A medical record is tied directly to an appointment, not existing independently.

- Doctors can belong to only one department, simplifying organizational structure.

- Patients can have multiple appointments, and likewise, a doctor can conduct many appointments.

- No billing or insurance is shown, so assumed out of scope unless extended later.



## RESULT

The resulting ER diagram effectively captured the structure and constraints of the system and served as a blueprint for further database design.
