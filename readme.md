# Attendance Management System

A simple attendance management system with GUI interfaces for instructors and students, built using Python's Tkinter and MySQL. It allows teachers to manage student records and attendance, while students can view their class routine.

---

## Features

### Instructor Interface
- Register students with student ID, name, course, and class ID.
- Record daily attendance using a GUI.
- Mark students as Present/Absent by double-clicking.
- Save and update attendance records to MySQL.
- View saved attendance data filtered by class and date.

### Student Interface
- View class routine in a tabular format.
- Read-only access for students to check schedules.

---

## Technologies Used

- **Frontend:** Python (Tkinter, ttk)
- **Backend:** MySQL
- **Calendar UI:** `tkcalendar`
- **Environment Management:** `.env` with `python-dotenv`

---

## Database Schema

```sql
CREATE DATABASE IF NOT EXISTS attendance_system;
USE attendance_system;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('teacher', 'student') NOT NULL
);

CREATE TABLE students (
    student_id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    course VARCHAR(100),
    date DATE,
    PRIMARY KEY (student_id)
);

CREATE TABLE attendance (
    attendance_id INT NOT NULL AUTO_INCREMENT,
    student_id INT,
    present INT,
    class_id INT NOT NULL,
    PRIMARY KEY (attendance_id),
    FOREIGN KEY (student_id) REFERENCES students(student_id)
);

