# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="1327" height="994" alt="Screenshot 2025-09-26 111526" src="https://github.com/user-attachments/assets/5d89050f-51e2-4d0e-ab85-342ecc35d84b" />


### Entities and Attributes
1.MEMBER-
member_id(Primary key)
name
membershiptype
startdate

2.PROGRAM-
programID(Primary key)
programname
description
schedule

3.TRAINER-
trainderID(Primary key)
name
specialisation
experience

4.PAYMENT-

paymentID(Primary  Key)
amount
paymentdate
paymenttype

5.SESSION-
sessionID (Primary key)
date
time
type

6.ATTENDENCE(Attendance)-
attendance_id (Primary Key)
status(values: present/absent)


### Relationships and Constraints
MEMBER — pays → PAYMENT One member can make many payments. Each payment
belongs to one member. (1-to-Many)

MEMBER — Enrollment → PROGRAM A member can enroll in multiple programs.
A program can have many members. (Many-to-Many)

PROGRAM — teaches → TRAINER A trainer can teach multiple programs. A program
can be taught by one or more trainers. (Many-to-Many)

MEMBER — attends → SESSION A member can attend many sessions. A session can be
attended by many members. (Many-to-Many)

SESSION — has → ATTENDENCE A session can have many attendance records. Each
attendance record belongs to a session. (1-to-Many)



### Assumptions
Each member must have a valid membership (with start date and type).

A program may be taught by more than one trainer.

Enrollment is required before a member can attend sessions of a program.

Payments are linked directly to members, not to programs or sessions.

Attendance is tracked per session per member.

Status in attendance is limited to "present" or "absent".

A trainer may teach multiple programs but must have at least one specialization.

A member can attend multiple sessions but must be enrolled in at least one program.

## RESULT

Hence,the concepts of ER diagram is understood and applied by creating an ER diagram
for a real world application.


