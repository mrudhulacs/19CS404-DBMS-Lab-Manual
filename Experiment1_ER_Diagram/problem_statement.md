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

# ER Diagram Submission - CHITTOOR SARAVANA MRUDHULA (212224040056)

## Scenario Chosen:
University / Hospital (choose one)

## ER Diagram:

University :

![Screenshot 2025-04-29 135342](https://github.com/user-attachments/assets/c99cfd61-86c2-4d70-9ed5-7106a05ff704)


## Entities and Attributes:

```
USER: ID, NAME, PHNO, ADDRESS
REGISTRATION: STU_ID, REG_ID, DATE, TYPE, DATE
STUDENT: REG_NO, ID, NAME, DOB, DEPT, YEAR, YEAR_ENROLLED, CREDITS, FEE
PROGRAM: PROG_NAME, PROG_ID, CREDIT_POINTS
COURSE: NAME, ID, PREREQUISIT
ATTEMPTS: YEAR, SEM, MARK, GRADE
MANAGEMENT: (This appears to be a relationship, not an entity with its own attributes in this diagram)
ENROLL: (This appears to be a relationship, not an entity with its own attributes in this diagram)
CONTAINS: (This appears to be a relationship, not an entity with its own attributes in this diagram)
ENROLLMENT: STATUS (This appears to be a relationship, not an entity with its own attributes in this diagram)

```



## Relationships and Constraints:

```
MANAGEMENT: USER manages REGISTRATION (Cardinality and Participation are not explicitly shown, but it implies
a one-to-many relationship where one user can manage multiple registrations, and a registration is managed by 
one user. Participation likely total for REGISTRATION and partial for USER).

REGISTRATION: STUDENT has REGISTRATION (Cardinality and Participation are not explicitly shown, but it implies 
a one-to-many relationship where one student can have multiple registrations, and a registration belongs to one
student. Participation likely total for REGISTRATION and partial for STUDENT).

ENROLL: STUDENT enrolls in PROGRAM (Cardinality and Participation are not explicitly shown, but it implies a many-to-many 
relationship since a student can enroll in multiple programs, and a program can have multiple students. Participation is likely total for both).

CONTAINS: PROGRAM contains COURSE (Cardinality and Participation are not explicitly shown, but it implies a one-to-many
relationship where one program can contain multiple courses, and a course belongs to one program. Participation likely total for COURSE and partial for PROGRAM).

ATTEMPTS: STUDENT has ATTEMPTS (Cardinality and Participation are not explicitly shown, but it implies a one-to-many relationship
where one student can have multiple attempts for different courses, and an attempt belongs to one student. Participation likely 
total for ATTEMPTS and partial for STUDENT).

ENROLLMENT: STUDENT enrolls in COURSE (Cardinality and Participation are not explicitly shown, but it implies a many-to-many relationship
with an attribute 'STATUS', indicating the enrollment status of a student in a course. Participation is likely total for both).

PREREQUISIT: COURSE has PREREQUISIT (This is a reflexive relationship on the COURSE entity, indicating that one course can be a
prerequisite for another. Cardinality and Participation are not explicitly shown, but it's likely an optional many-to-many relationship,
as a course can have multiple prerequisites and can be a prerequisite for multiple other courses, and some courses might not have any prerequisites).
 ```




## Extension (Prerequisite / Billing):

```
Prerequisite: Prerequisites are modeled through a reflexive relationship on the COURSE entity. The attribute
PREREQUISIT (which should likely be PREREQ_ID to reference another course's ID) in the COURSE entity indicates which course(s)
are required before taking a particular course. This structure allows for defining chains or multiple prerequisites for a single course.

Billing: Billing information is partially modeled through the FEE attribute in the STUDENT entity. This suggests that each student
has an associated fee. However, the diagram doesn't provide details on when or how these fees are applied (e.g., per program, per
semester, per course) or any information about payment status, due dates, or billing history. To model billing more comprehensively,
 you might need additional entities like BILL, PAYMENT, or a more detailed structure within the REGISTRATION or a new enrollment-specific entity to track financial aspects.
```

## Design Choices:


This ER diagram provides a good foundation for a student registration system, capturing key entities and their relationships.
However, depending on the specific requirements, further refinement might be needed, especially in areas like billing and a clearer
definition of the 'TYPE' attribute in the REGISTRATION entity.



## RESULT

The ERD effectively models the hospital appointment system, clearly separating key aspects like scheduling, department assignment, and medical history tracking, ensuring scalability and ease of future extensions like billing and lab test integration.
