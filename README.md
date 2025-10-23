# MIST4610 Project 1

Group Members: Jackson Boyer, Rong Xin Hu, Justus Nour, Trey Trotti, Sophie Yoo

Our team designed a hospital management system that tracks patient care, appointments, billing, and staff operations. The database supports key functions like scheduling, prescriptions, lab tests, and insurance processing. It helps management monitor patient flow, department performance, and financial outcomes.

Data Model: Hospital 
Entities
1. Patient
2. Doctor
3. Department
4. Room
5. Appointment
6. Med_Record
7.Prescription
8. Lab_Test
9. Bill
10. Insurance

| #  | Relationship                            | Type                  | Identifying / Non-Identifying | Description                                                    |
| -- | --------------------------------------- | --------------------- | ----------------------------- | -------------------------------------------------------------- |
| 1  | **Insurance → Patient**                 | 1-to-Many             | Non-Identifying               | One insurance policy can cover many patients.                  |
| 2  | **Department → Doctor**                 | 1-to-Many             | Non-Identifying               | A department employs many doctors.                             |
| 3  | **Doctor → Doctor (Supervisor)**        | 1-to-Many (Recursive) | Non-Identifying               | A doctor may supervise multiple junior doctors.                |
| 4  | **Patient ↔ Doctor (via Appointment)**  | Many-to-Many          | Identifying                   | Appointments depend on both the patient and the doctor.        |
| 5  | **Appointment → Bill**                  | 1-to-1                | Identifying                   | Each appointment generates exactly one bill.                   |
| 6  | **Patient → Medical_Record**            | 1-to-Many             | Identifying                   | Each patient can have multiple medical records.                |
| 7  | **Patient ↔ Doctor (via Prescription)** | Many-to-Many          | Identifying                   | Prescriptions depend on both the patient and the doctor.       |
| 8  | **Patient ↔ Doctor (via Lab_Test)**     | Many-to-Many          | Identifying                   | Lab tests depend on both the patient and the doctor.           |
| 9  | **Department → Room**                   | 1-to-Many             | Non-Identifying               | Each department has multiple rooms.                            |
| 10 | **Room → Patient**                      | 1-to-Many             | Non-Identifying               | Each room can hold one or more patients.                       |
| 11 | **Doctor → Department**                 | 1-to-1                | Identifying                   | Each department has one doctor serving as the department head. |




Description and Justification of your Queries
Our group chose to design a database for a hospital management system that helps organize and track patient care, staff activity, and billing information. The goal of this database is to store and manage key information about patients, doctors, appointments, treatments, prescriptions, and financial transactions in a way that supports hospital operations and managerial decision-making. The database allows the hospital to record basic details about patients, insurance providers, and the doctors who treat them. Each doctor is assigned to a specific department, and each patient may have multiple appointments with different doctors. During those appointments, doctors can issue prescriptions, request lab tests, and add new entries to the patient’s medical record. Every patient is assigned to a room during their stay, and each visit creates a bill that is linked to their insurance provider. The billing information helps hospital management track outstanding payments and monitor total revenue. This data model captures the essential operational data of a hospital and supports queries that managers may use to make better decisions—such as identifying the most frequently visited departments, tracking doctor workloads, monitoring patient admissions, and reviewing financial performance.

  
