# MIST4610 Project 1

Group Members: Justus Nour, Jackson Boyer, Rong Xin Hu, Trey Trotti, Sophie Yoo

Scenario Description: Our team designed a hospital management system that tracks patient care, appointments, billing, and staff operations. The database supports key functions like scheduling, prescriptions, lab tests, and insurance processing. It helps management monitor patient flow, department performance, and financial outcomes.

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

Relationships:
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

Data Dictionary

Table: Appointment
| Column Name | Description                                               | Data Type | Size | Format     | Key?    |
| ----------- | --------------------------------------------------------- | --------- | ---- | ---------- | ------- |
| appID       | Unique number indicating the patient’s appointment number | INT       |      |            | **Yes** |
| app_date    | Date of the appointment                                   | DATE      |      | YYYY/MM/DD |         |
| app_time    | Time of the appointment                                   | TIME      |      | HH:MM:SS   |         |
| app_reason  | Reason for the appointment                                | TEXT      | 45   |            |         |

Table: Bill
| Column Name | Description                                        | Data Type | Size | Format     | Key?    |
| ----------- | -------------------------------------------------- | --------- | ---- | ---------- | ------- |
| billID      | Unique number indicating the patient’s bill number | INT       |      |            | **Yes** |
| bill_amount | Amount to be paid                                  | DECIMAL   | 45   |            |         |
| bill_date   | The date the patient was billed                    | DATE      |      | YYYY/MM/DD |         |
| bill_status | Status of the bill (paid or not)                   | TEXT      | 45   |            |         |

Table: Department
| Column Name  | Description                              | Data Type | Size | Format | Key?    |
| ------------ | ---------------------------------------- | --------- | ---- | ------ | ------- |
| departmentID | Unique number identifying the department | INT       |      |        | **Yes** |
| dept_name    | Name of the department                   | TEXT      | 45   |        |         |
| dept_floor   | Floor of the department                  | TEXT      | 45   |        |         |
| dept_head    | Name of the department head              | TEXT      | 45   |        |         |

Table: Doctor
| Column Name   | Description                          | Data Type | Size | Format        | Key?    |
| ------------- | ------------------------------------ | --------- | ---- | ------------- | ------- |
| doctorID      | Unique number to identify the doctor | INT       |      |               | **Yes** |
| doc_firstname | First name of the doctor             | TEXT      | 45   |               |         |
| doc_lastname  | Last name of the doctor              | TEXT      | 45   |               |         |
| doc_specialty | Doctor’s specialty                   | TEXT      | 45   |               |         |
| doc_phone     | Doctor’s phone number                | TEXT      | 10   | (XXX)XXX-XXXX |         |
| doc_email     | Doctor’s email                       | TEXT      | 45   |               |         |

Table: Insurance
| Column Name      | Description                         | Data Type | Size | Format | Key?    |
| ---------------- | ----------------------------------- | --------- | ---- | ------ | ------- |
| insuranceID      | Unique number to identify insurance | INT       |      |        | **Yes** |
| provider         | Insurance provider name             | TEXT      | 45   |        |         |
| ins_policynumber | Insurance policy number             | TEXT      | 45   |        |         |
| ins_coverage     | Insurance coverage type             | TEXT      | 45   |        |         |

Table: Lab_Test
| Column Name | Description                            | Data Type | Size | Format     | Key?    |
| ----------- | -------------------------------------- | --------- | ---- | ---------- | ------- |
| testID      | Unique number to identify the lab test | INT       |      |            | **Yes** |
| test_type   | Type of lab test                       | TEXT      | 45   |            |         |
| test_result | Result of the lab test                 | TEXT      | 45   |            |         |
| test_date   | Date of the lab test                   | DATE      |      | YYYY/MM/DD |         |

Table: Med_Record
| Column Name     | Description                               | Data Type | Size | Format     | Key?    |
| --------------- | ----------------------------------------- | --------- | ---- | ---------- | ------- |
| recordID        | Unique number used to identify the record | INT       |      |            | **Yes** |
| med_diagnosis   | The diagnosis of the patient              | TEXT      | 45   |            |         |
| med_treatment   | The suggested treatment for the patient   | TEXT      | 45   |            |         |
| med_record_date | Date the record was created               | DATE      |      | YYYY/MM/DD |         |

Table: Patient
| Column Name       | Description                           | Data Type | Size | Format        | Key?    |
| ----------------- | ------------------------------------- | --------- | ---- | ------------- | ------- |
| patientID         | Unique number to identify the patient | INT       |      |               | **Yes** |
| first_name        | First name of the patient             | TEXT      | 45   |               |         |
| last_name         | Last name of the patient              | TEXT      | 45   |               |         |
| patient_dob       | Date of birth                         | DATE      |      | YYYY/MM/DD    |         |
| patient_gender    | Gender                                | TEXT      | 45   |               |         |
| patient_phone     | Phone number                          | TEXT      | 10   | (XXX)XXX-XXXX |         |
| patient_address   | Address                               | TEXT      | 45   |               |         |
| emergency_contact | Emergency contact name                | TEXT      | 45   |               |         |
| patient_bloodtype | Blood type                            | TEXT      | 45   |               |         |

Table: Prescription
| Column Name       | Description                                     | Data Type | Size | Format | Key?    |
| ----------------- | ----------------------------------------------- | --------- | ---- | ------ | ------- |
| prescriptionID    | Unique number used to identify the prescription | INT       |      |        | **Yes** |
| drug_name         | Name of the drug                                | TEXT      | 45   |        |         |
| drug_dosage       | Correct dosage of the drug                      | TEXT      | 45   |        |         |
| drug_frequency    | How often the drug should be taken              | TEXT      | 45   |        |         |
| drug_instructions | Instructions on how to take the drug            | TEXT      | 45   |        |         |

Table: Room
| Column Name       | Description                                | Data Type | Size | Format | Key?    |
| ----------------- | ------------------------------------------ | --------- | ---- | ------ | ------- |
| roomID            | Unique number to identify the room         | INT       |      |        | **Yes** |
| room_number       | Room number                                | TEXT      | 45   |        |         |
| room_type         | Type of room                               | TEXT      | 45   |        |         |
| room_availability | Room availability status (vacant/occupied) | TEXT      | 45   |        |         |



Description and Justification of your Queries:

  Our group chose to design a database for a hospital management system that helps organize and track patient care, staff activity, and billing information. The goal of this database is to store and manage key information about patients, doctors, appointments, treatments, prescriptions, and financial transactions in a way that supports hospital operations and managerial decision-making. The database allows the hospital to record basic details about patients, insurance providers, and the doctors who treat them. Each doctor is assigned to a specific department, and each patient may have multiple appointments with different doctors. During those appointments, doctors can issue prescriptions, request lab tests, and add new entries to the patient’s medical record. Every patient is assigned to a room during their stay, and each visit creates a bill that is linked to their insurance provider. The billing information helps hospital management track outstanding payments and monitor total revenue. This data model captures the essential operational data of a hospital and supports queries that managers may use to make better decisions—such as identifying the most frequently visited departments, tracking doctor workloads, monitoring patient admissions, and reviewing financial performance.

  
