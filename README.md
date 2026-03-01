# 🎓 University Department Database System

A comprehensive Relational Database Management System (RDBMS) designed to handle the core academic and administrative operations of a University Department. 

Developed as Phase A of the "Databases (PLH 303)" course at the Technical University of Crete (TUC), this project focuses on advanced database concepts including complex schema design, stored procedures, triggers, and views using **PostgreSQL**.


## 🚀 Project Overview

The database models a fully functional polytechnic department. It tracks and manages data across various interconnected entities such as:
* **Personnel & Students**: Professors, Lab Teaching Staff, and Students (with auto-generated registration details, AMKA, etc.).
* **Academics**: Sectors, Laboratories, Courses (Core & Electives), and Semesters.
* **Graduation & Theses**: Diploma requirements, Thesis titles, Supervisor Committees, and final grade calculations.
* **Laboratory Operations**: Lab Modules, Student Workgroups, and Lab grading rules.

## ⚙️ Core Features & Implementations

### 1. Schema Extension (DDL)
* Translated a complex Entity-Relationship (ER) model into a normalized relational schema.
* Created and linked tables for Diplomas, Graduation Rules, Committees, Lab Modules, and Workgroups.

### 2. Stored Procedures & Functions (PL/pgSQL)
Implemented custom PostgreSQL functions for automated data management and complex queries:
* **Automated Data Generation:** Auto-assigned random Diploma Theses to eligible senior students.
* **Workgroup Management:** Randomly distributed students into Lab Workgroups while strictly enforcing maximum capacity constraints.
* **Grade Management:** Automated random grade insertions for exams and lab modules for enrolled students.
* **Advanced Analytics:** * Calculated the exact teaching workload (in hours) for lab staff based on their supported courses and active lab groups.
  * Identified the academic sector producing the highest number of Diploma Theses.
  * Retrieved maximum grades per course dynamically.

### 3. Business Logic Enforcement (Triggers)
Leveraged PostgreSQL Triggers to enforce complex university regulations at the database level:
* **Capacity Limits:** Prevented the insertion of members into Thesis Committees or Lab Workgroups if maximum limits were exceeded.
* **Automated Grading & Status:** Dynamically calculated the final course grade by combining exam and lab grades (applying specific weights and minimum threshold rules). Automatically updated student registration states to `pass` or `fail`.
* **Enrollment Validation:** Intercepted student course registration requests to verify prerequisite fulfillment and ensure the student did not exceed the maximum allowed credits (20) or courses (6) per semester. Allowed or rejected the insertion automatically.
* **Semester Initialization:** Automatically generated `CourseRun` instances, assigned professors, and allocated labs whenever a new 'future' Semester was inserted into the database.

## 💻 Tech Stack

* **Database Engine:** PostgreSQL (v13.6)
* **Languages:** SQL, PL/pgSQL
* **Management Tool:** pgAdmin 4
* **Concepts:** DDL, DML, ER to Relational Mapping, Triggers, Views, Stored Procedures, Constraints.
