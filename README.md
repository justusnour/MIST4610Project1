# MIST4610 Project 1 Group 7

## Group Members: 
Justus Nour, Jackson Boyer, Rong Xin Hu, Trey Trotti, Sophie Yoo [Sophie Yoo](https://github.com/sophieyoo)

http://github.com/sophieyoo/MIST4610Project1

https://github.com/Jackson9812/MIST4610Project1

https://github.com/RongX02/MIST-4610-Project-1

## Scenario Description: 
Our team designed a hospital management system that tracks patient care, appointments, billing, and staff operations. The database supports key functions like scheduling, prescriptions, lab tests, and insurance processing. It helps management monitor patient flow, department performance, and financial outcomes.

## Data Model Explanation: 
Our data model represents how a real hospital functions day to day, capturing the connections between patients, doctors, departments, and the many services that keep a hospital running smoothly. At the core of the model is the Patient entity, since nearly every process in the hospital revolves around the patient. Each patient can have multiple medical records that track their diagnoses and treatments, and they can also make many appointments with different doctors. Because an appointment depends on both the patient and the doctor, it forms a many-to-many relationship, showing how patients and doctors interact throughout the care process. Every appointment results in one Bill, which records the cost and payment details, and since each patient’s bill is tied to their insurance provider, there’s a one-to-many relationship between Insurance and Patient, showing that one insurance plan can cover multiple individuals.
Doctors are organized within Departments such as Cardiology, Pediatrics, or Neurology. A department can have many doctors, and each doctor belongs to one department, forming a one-to-many relationship. Within this, some doctors may supervise others, creating a recursive relationship that reflects real hospital hierarchies. Each department also has one designated department head, connecting a one-to-one relationship between Department and Doctor. Departments are also responsible for multiple Rooms, which represent hospital spaces where patients stay during treatment. Because one room can host several patients over time, this creates a one-to-many relationship between Room and Patient.
Beyond daily appointments, doctors can issue Prescriptions or order Lab Tests for their patients. These depend on both the patient and doctor, forming many-to-many relationships, since multiple patients can receive prescriptions or lab tests from multiple doctors. Altogether, this model mirrors the complex but organized structure of a hospital—how patients move through departments, meet with doctors, receive treatments, get billed, and stay in rooms. By capturing all these interactions, the data model helps ensure that every piece of information works together to support efficient and effective patient care.

<img width="619" height="626" alt="Screenshot 2025-10-23 at 2 35 38 PM" src="https://github.com/user-attachments/assets/b9c066d5-f1b9-444a-9d1c-57ac4c06ad78" />



## Relationships:
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

## Data Dictionary

The following Data Dictionary defines the attributes, data types, and key designations for each entity in our hospital database schema.

### Table: Appointment
| Column Name | Description                                               | Data Type | Size | Format     | Key?    |
| ----------- | --------------------------------------------------------- | --------- | ---- | ---------- | ------- |
| apptID       | Unique number indicating the patient’s appointment number | INT       |      |            | **Yes** |
| appt_date    | Date of the appointment                                   | DATE      |      | YYYY/MM/DD |         |
| appt_time    | Time of the appointment                                   | TIME      |      | HH:MM:SS   |         |
| appt_reason  | Reason for the appointment                                | TEXT      | 45   |            |         |

### Table: Bill
| Column Name | Description                                        | Data Type | Size | Format     | Key?    |
| ----------- | -------------------------------------------------- | --------- | ---- | ---------- | ------- |
| billID      | Unique number indicating the patient’s bill number | INT       |      |            | **Yes** |
| bill_amount | Amount to be paid                                  | DECIMAL   | (10,2)   |            |         |
| bill_date   | The date the patient was billed                    | DATE      |      | YYYY/MM/DD |         |
| bill_status | Status of the bill (paid or not)                   | TEXT      | 45   |            |         |

### Table: Department
| Column Name  | Description                              | Data Type | Size | Format | Key?    |
| ------------ | ---------------------------------------- | --------- | ---- | ------ | ------- |
| departmentID | Unique number identifying the department | INT       |      |        | **Yes** |
| dept_name    | Name of the department                   | TEXT      | 45   |        |         |
| dept_floor   | Floor of the department                  | TEXT      | 45   |        |         |
| dept_head    | Name of the department head              | TEXT      | 45   |        |         |

### Table: Doctor
| Column Name   | Description                          | Data Type | Size | Format        | Key?    |
| ------------- | ------------------------------------ | --------- | ---- | ------------- | ------- |
| doctorID      | Unique number to identify the doctor | INT       |      |               | **Yes** |
| doc_firstname | First name of the doctor             | TEXT      | 45   |               |         |
| doc_lastname  | Last name of the doctor              | TEXT      | 45   |               |         |
| doc_speciality | Doctor’s specialty                   | TEXT      | 45   |               |         |
| doc_phone     | Doctor’s phone number                | TEXT      | 10   | (XXX)XXX-XXXX |         |
| doc_email     | Doctor’s email                       | TEXT      | 45   |               |         |

### Table: Insurance
| Column Name      | Description                         | Data Type | Size | Format | Key?    |
| ---------------- | ----------------------------------- | --------- | ---- | ------ | ------- |
| insuranceID      | Unique number to identify insurance | INT       |      |        | **Yes** |
| provider         | Insurance provider name             | TEXT      | 45   |        |         |
| ins_policynumber | Insurance policy number             | TEXT      | 45   |        |         |
| ins_coverage     | Insurance coverage type             | TEXT      | 45   |        |         |

### Table: Lab_Test
| Column Name | Description                            | Data Type | Size | Format     | Key?    |
| ----------- | -------------------------------------- | --------- | ---- | ---------- | ------- |
| labtestID      | Unique number to identify the lab test | INT       |      |            | **Yes** |
| test_type   | Type of lab test                       | TEXT      | 45   |            |         |
| test_result | Result of the lab test                 | TEXT      | 45   |            |         |
| test_date   | Date of the lab test                   | DATE      |      | YYYY/MM/DD |         |

### Table: Med_Record
| Column Name     | Description                               | Data Type | Size | Format     | Key?    |
| --------------- | ----------------------------------------- | --------- | ---- | ---------- | ------- |
| recordID        | Unique number used to identify the record | INT       |      |            | **Yes** |
| med_diagnosis   | The diagnosis of the patient              | TEXT      | 45   |            |         |
| med_treatment   | The suggested treatment for the patient   | TEXT      | 45   |            |         |
| med_record_date | Date the record was created               | DATE      |      | YYYY/MM/DD |         |

### Table: Patient
| Column Name       | Description                           | Data Type | Size | Format        | Key?    |
| ----------------- | ------------------------------------- | --------- | ---- | ------------- | ------- |
| patientID         | Unique number to identify the patient | INT       |      |               | **Yes** |
| first_name        | First name of the patient             | TEXT      | 45   |               |         |
| last_name         | Last name of the patient              | TEXT      | 45   |               |         |
| patient_dob       | Date of birth                         | DATE      |      | YYYY/MM/DD    |         |
| patient_gender    | Gender                                | TEXT      | 45   |               |         |
| patient_phone     | Phone number                          | TEXT      | 10   | (XXX)XXX-XXXX |         |
| patient_addy   | Address                               | TEXT      | 45   |               |         |
| emergency_contact | Emergency contact name                | TEXT      | 45   |               |         |
| patient_bloodtype | Blood type                            | TEXT      | 45   |               |         |

### Table: Prescription
| Column Name       | Description                                     | Data Type | Size | Format | Key?    |
| ----------------- | ----------------------------------------------- | --------- | ---- | ------ | ------- |
| prescriptionID    | Unique number used to identify the prescription | INT       |      |        | **Yes** |
| drug_name         | Name of the drug                                | TEXT      | 45   |        |         |
| drug_dosage       | Correct dosage of the drug                      | TEXT      | 45   |        |         |
| drug_frequency    | How often the drug should be taken              | TEXT      | 45   |        |         |
| drug_instructions | Instructions on how to take the drug            | TEXT      | 45   |        |         |

### Table: Room
| Column Name       | Description                                | Data Type | Size | Format | Key?    |
| ----------------- | ------------------------------------------ | --------- | ---- | ------ | ------- |
| roomID            | Unique number to identify the room         | INT       |      |        | **Yes** |
| room_num       | Room number                                | TEXT      | 45   |        |         |
| room_type         | Type of room                               | TEXT      | 45   |        |         |
| room_availability | Room availability status (vacant/occupied) | TEXT      | 45   |        |         |



## Description and Justification of your Queries:

  Our group chose to design a database for a hospital management system that helps organize and track patient care, staff activity, and billing information. The goal of this database is to store and manage key information about patients, doctors, appointments, treatments, prescriptions, and financial transactions in a way that supports hospital operations and managerial decision-making. The database allows the hospital to record basic details about patients, insurance providers, and the doctors who treat them. Each doctor is assigned to a specific department, and each patient may have multiple appointments with different doctors. During those appointments, doctors can issue prescriptions, request lab tests, and add new entries to the patient’s medical record. Every patient is assigned to a room during their stay, and each visit creates a bill that is linked to their insurance provider. The billing information helps hospital management track outstanding payments and monitor total revenue. This data model captures the essential operational data of a hospital and supports queries that managers may use to make better decisions—such as identifying the most frequently visited departments, tracking doctor workloads, monitoring patient admissions, and reviewing financial performance.

  
