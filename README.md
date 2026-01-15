# College Course Scheduler

A Java-based college course registration and enrollment management system that handles students, faculty, course sessions, and automated enrollment with capacity constraints.

## Overview

This console application simulates a college registration system where students can be enrolled into course sessions taught by faculty members. The system enforces enrollment rules such as maximum class capacity, minimum enrollment thresholds, and prevents duplicate course registrations.

## Features

### Core Functionality
- **Student Management** - Track student information, GPA, and course enrollments (max 4 courses per student)
- **Faculty Management** - Manage faculty members, tenure status, and teaching assignments
- **Course & Session Handling** - Create courses with multiple sessions, each with unique ticket IDs
- **Smart Enrollment** - Automatic validation to prevent duplicate enrollments and enforce capacity limits

### Enrollment Options
- **Sequential Auto-Enrollment** - Automatically fills all sessions with available students in order
- **Manual Class Selection** - Choose specific classes and fill them to minimum, maximum, or median capacity

### Report Generation
The system generates detailed output files:
| Report | Description |
|--------|-------------|
| `OutScheduledCourseSessions.txt` | Courses that met minimum enrollment with full rosters |
| `OutUnscheduledCourseSessions.txt` | Sessions that didn't meet minimum student requirements |
| `FacultyOut.txt` | Faculty details with their teaching assignments |
| `ScheduledStudents.txt` | Students with their enrolled courses |
| `UnscheduledStudents.txt` | Students who couldn't be placed in any courses |

## Project Structure

```
src/
├── App.java                 # Main application entry point
├── Attendees.java           # Base class for Students and Faculty
├── CollegeClass.java        # Course and Session definitions
├── DataDisplayAndManip.java # UI display and enrollment logic
├── DataStream.java          # File I/O operations
├── Students.txt             # Student data input
├── Faculty.txt              # Faculty data input
└── class.txt                # Course catalog input
```

## Class Hierarchy

```
Attendees (Base Class)
├── Student
│   └── Tracks: GPA, enrolled sessions, enrollment limits
└── Faculty
    └── Tracks: Tenure status, teaching sessions

CollegeClass
└── Session
    └── Tracks: Ticket ID, enrollment count, capacity limits
```

## How It Works

1. **Data Loading** - System reads student, faculty, and course data from text files
2. **Session Creation** - Each course can have multiple sessions assigned to different faculty
3. **Enrollment Process** - Users choose between automatic or manual enrollment
4. **Validation** - System checks:
   - Student hasn't exceeded 4 course limit
   - Student isn't already enrolled in the same course
   - Session hasn't exceeded maximum capacity
   - Session meets minimum enrollment threshold
5. **Report Generation** - Outputs detailed enrollment reports

## Usage

```bash
# Compile
javac -d bin src/*.java

# Run
java -cp bin App
```

### Menu Options
```
(a) Add existing students to classes in sequential order
(b) Select class and add to it
```

When selecting option (b), you can fill classes to:
- **(a)** Minimum capacity
- **(b)** Maximum capacity  
- **(c)** Median between min and max

## Sample Output

```
Bio1a_T1500 taught by Smith has (25) students
Chem1a_T1505 taught by Johnson has (30) students
Math1a_T1510 taught by Williams has (28) students

Total Students: 150
Total Faculty: 10
Total Courses: 12
Total Sessions: 24
Total Unscheduled Sessions: 3
Total UnEnrolled Students: 5
```

## Technical Details

- **Language**: Java
- **Architecture**: Object-Oriented with inheritance hierarchy
- **Data Storage**: Text file-based I/O
- **Session IDs**: Auto-generated with format `[CourseID]_T[TicketNumber]`

## Background

This project was developed as a final project for an Introduction to Java course, demonstrating concepts including:
- Object-Oriented Programming (inheritance, encapsulation)
- File I/O operations
- Collections (ArrayList, List)
- User input handling
- Data validation and business logic

---

*Built with Java*
