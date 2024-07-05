# Guvi Zen Class Database Design

## Introduction

The Guvi Zen Class project requires a robust database to manage various aspects of a learning management system. This document outlines the database schema designed to efficiently handle students, instructors, courses, class sessions, assignments, grades, attendance, CodeKata exercises, topics, tasks, company drives, and additional functionalities.

## Entities and Attributes

### 1. Students
- **student_id**: Unique identifier for each student.
- **name**: The student's name.
- **email**: The student's email address.
- **phone_number**: The student's phone number.

### 2. Instructors
- **instructor_id**: Unique identifier for each instructor.
- **name**: The instructor's name.
- **email**: The instructor's email address.
- **phone_number**: The instructor's phone number.

### 3. Courses
- **course_id**: Unique identifier for each course.
- **title**: The title of the course.
- **description**: A brief description of the course.
- **instructor_id**: References the instructor teaching the course (Foreign Key).

### 4. Class Sessions
- **session_id**: Unique identifier for each class session.
- **course_id**: References the course being taught in this session (Foreign Key).
- **date**: The date of the class session.
- **time**: The time when the class session starts.
- **duration**: The duration of the class session in minutes.

### 5. Assignments
- **assignment_id**: Unique identifier for each assignment.
- **course_id**: References the course for which the assignment is given (Foreign Key).
- **title**: The title of the assignment.
- **description**: A brief description of the assignment.
- **due_date**: The due date for the assignment submission.

### 6. Grades
- **grade_id**: Unique identifier for each grade record.
- **student_id**: References the student who received the grade (Foreign Key).
- **assignment_id**: References the assignment for which the grade is given (Foreign Key).
- **grade**: The grade received by the student.

### 7. Attendance
- **attendance_id**: Unique identifier for each attendance record.
- **session_id**: References the class session (Foreign Key).
- **student_id**: References the student attending the session (Foreign Key).
- **status**: The attendance status (e.g., Present, Absent).

### 8. CodeKata
- **kata_id**: Unique identifier for each CodeKata exercise.
- **title**: The title of the CodeKata exercise.
- **description**: A brief description of the exercise.
- **difficulty_level**: The difficulty level of the exercise (e.g., Easy, Medium, Hard).

### 9. Topics
- **topic_id**: Unique identifier for each topic.
- **course_id**: References the course to which the topic belongs (Foreign Key).
- **title**: The title of the topic.
- **description**: A brief description of the topic.

### 10. Tasks
- **task_id**: Unique identifier for each task.
- **course_id**: References the course to which the task belongs (Foreign Key).
- **title**: The title of the task.
- **description**: A brief description of the task.
- **due_date**: The due date for the task completion.

### 11. Company Drives
- **drive_id**: Unique identifier for each company drive.
- **company_name**: The name of the company conducting the drive.
- **date**: The date of the drive.
- **time**: The time when the drive starts.
- **location**: The location where the drive is conducted.
- **eligibility_criteria**: The criteria for students to be eligible for the drive.

### 12. CodeKata Grades
- **id**: Unique identifier for each CodeKata grade record.
- **student_id**: References the student who received the grade (Foreign Key).
- **kata_id**: References the CodeKata exercise (Foreign Key).
- **grade**: The grade received by the student for the CodeKata exercise.

### Additional Tables

### 13. Feedback
- **feedback_id**: Unique identifier for each feedback record.
- **course_id**: References the course to which the feedback is related (Foreign Key).
- **student_id**: References the student who provided the feedback (Foreign Key).
- **feedback**: The feedback provided by the student.

### 14. Certificates
- **certificate_id**: Unique identifier for each certificate record.
- **course_id**: References the course for which the certificate is issued (Foreign Key).
- **student_id**: References the student who earned the certificate (Foreign Key).
- **issue_date**: The date when the certificate was issued.

### 15. Payments
- **payment_id**: Unique identifier for each payment record.
- **student_id**: References the student who made the payment (Foreign Key).
- **amount**: The amount paid by the student.
- **payment_date**: The date when the payment was made.

### 16. Discussions
- **discussion_id**: Unique identifier for each discussion post.
- **course_id**: References the course in which the discussion took place (Foreign Key).
- **student_id**: References the student who posted the discussion (Foreign Key).
- **topic**: The topic of the discussion.
- **message**: The content of the discussion post.

### 17. Project Teams
- **team_id**: Unique identifier for each project team.
- **course_id**: References the course to which the project team belongs (Foreign Key).
- **team_name**: The name of the project team.
- **project_description**: Description of the project the team is working on.

### 18. User Role Assignments
- **assignment_id**: Unique identifier for each user role assignment.
- **user_id**: References the user (student or instructor) to whom the role is assigned (Foreign Key).
- **role_id**: The role assigned to the user (e.g., Student, Instructor).

### 19. Course Materials
- **material_id**: Unique identifier for each course material.
- **course_id**: References the course to which the material belongs (Foreign Key).
- **material_name**: The name or title of the course material.
- **material_type**: The type of the material (e.g., Slide, Document).
- **material_url**: The URL or location of the course material.

### 20. Course Ratings
- **rating_id**: Unique identifier for each course rating.
- **course_id**: References the course that was rated (Foreign Key).
- **student_id**: References the student who provided the rating (Foreign Key).
- **rating**: The rating given by the student (e.g., on a scale of 1 to 5).
- **review**: Optional review or comment provided by the student.

## Relationships

1. **Instructors and Courses**: An instructor can teach multiple courses, establishing a one-to-many relationship.
2. **Courses and Class Sessions**: Each course can have multiple class sessions, forming a one-to-many relationship.
3. **Courses and Assignments**: Each course can have multiple assignments, forming a one-to-many relationship.
4. **Students and Grades**: A student can receive multiple grades, creating a one-to-many relationship.
5. **Assignments and Grades**: Each assignment can have multiple grades associated with it, forming a one-to-many relationship.
6. **Class Sessions and Attendance**: Each class session can have multiple attendance records, forming a one-to-many relationship.
7. **Students and Attendance**: Each student can have multiple attendance records, forming a one-to-many relationship.
8. **Courses and Topics**: Each course can have multiple topics, forming a one-to-many relationship.
9. **Courses and Tasks**: Each course can have multiple tasks, forming a one-to-many relationship.
10. **Courses and Company Drives**: Each course can have multiple company drives, forming a one-to-many relationship.
11. **Students and CodeKata**: Students can have multiple grades for different CodeKata exercises, creating a many-to-many relationship via the `CodeKata Grades` table.
12. **CodeKata and CodeKata Grades**: Each CodeKata exercise can have multiple grades associated with it, forming a one-to-many relationship.
13. **Courses and Feedback**: Each course can have multiple feedback entries, forming a one-to-many relationship.
14. **Courses and Certificates**: Each course can issue multiple certificates, forming a one-to-many relationship.
15. **Students and Payments**: Each student can make multiple payments, forming a one-to-many relationship.
16. **Courses and Discussions**: Each course can have multiple discussions, forming a one-to-many relationship.
17. **Courses and Project Teams**: Each course can have multiple project teams, forming a one-to-many relationship.
18. **Students and User Role Assignments**: Each student can be assigned multiple roles, forming a one-to-many relationship.
19. **Instructors and User Role Assignments**: Each instructor can be assigned multiple roles, forming a one-to-many relationship.
20. **Courses and Course Materials**: Each course can have multiple course materials, forming a one-to-many relationship.
21. **Courses and Course Ratings**: Each course can receive multiple ratings, forming a one-to-many relationship.

## Summary

This database design effectively captures the necessary entities and their relationships for managing a learning management system, including additional functionalities such as feedback, certificates, payments, discussions, project teams, user roles, course materials, and course ratings. The tables and their relationships ensure data integrity and support the various functionalities required by the Guvi Zen Class project.
