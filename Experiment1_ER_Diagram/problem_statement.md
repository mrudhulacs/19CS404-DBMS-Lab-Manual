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

![image](https://github.com/user-attachments/assets/a89c35af-b919-412c-a2d6-42ec2d5f6ca1)



## Entities and Attributes:

- Entity1: Attributes
  
University

Attributes: uni_id, uni_name, location

Department

Attributes: dept_id, dept_name, uni_id (foreign key)

Program

Attributes: prog_id, prog_code, dept_id (foreign key)

Student

Attributes: reg_no, name, DOB

Instructor

Attributes: emp_id, name

Course

Attributes: course_code, course_name, credits

Enrollment

Attributes: enrol_id, reg_no, course_code ...



## Relationships and Constraints:
- Relationship1 (Cardinality, Participation)

University - Department
   Relationship: has
   Cardinality: 1:N (One university has many departments)
   Participation: Total on Department
   
Department - Program
   Relationship: Offers
   Cardinality: 1:N (One department offers many programs)
   Participation: Total on Program
   
Program - Student
   Relationship: contains
   Cardinality: 1:N (One program contains many students)
   Participation: Total on Student

Student - Enrollment
   Relationship: enrolls
   Cardinality: 1:N (One student can enroll in many courses)
   Participation: Partial on Student

Enrollment - Course
   Relationship: enrolled to
   Cardinality: M:1 (Many enrollments point to one course)

Course - Instructor
   Relationship: taught by
   Cardinality: M:1 (Many courses may be taught by one instructor) ...



## Extension (Prerequisite / Billing):

1 . To represent course prerequisites, a recursive relationship is used on the Course entity. 
    This models the situation where a course may depend on the completion of one or more other 
    courses prior to enrollment.

2 . Relationship Name: has_prerequisite

3 . Entity Involved: Course (linked to itself)

4 . Relationship Type: Recursive – the same entity (Course) is involved twice, once as the 
    dependent course and once as the prerequisite.

5 . Cardinality: Many-to-Many (M:N)
    * A course can have multiple prerequisites.
    * A course can be a prerequisite for multiple other courses.

    
This structure ensures that academic requirements are properly enforced and allows tracking of dependencies between courses.

## Design Choices:

1 . Entity Identification: Chose key real-world actors like Student, Instructor, Course because 
    they reflect essential components in a university environment.

2 . Relationship Logic: Courses are taught by instructors and enrolled in by students, so those 
    relationships model natural academic interactions.

3 . Normalization and Keys: Included foreign keys like dept_id, prog_id, uni_id for referential 
    integrity and normalization.

4 . Scalability: The recursive relationship for prerequisites supports flexible course planning.

## RESULT

The ER diagram successfully models a real-world university scenario, capturing the hierarchy of departments and programs, course management, student enrollments, and instructor roles. The model is extendable with a recursive relationship for prerequisites, fulfilling all stated requirements.
