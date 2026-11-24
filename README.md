# Student Management System - Class Diagram

```text
+-----------------------------------------+
|                 Person                  |
+-----------------------------------------+
| - id: String                            |
| - name: String                          |
| - email: String                         |
+-----------------------------------------+
| + getDetails(): String                  |
+-----------------------------------------+
         ^                       ^
         |                       |
+--------------------+   +----------------------+
|      Student       |   |      Instructor      |
+--------------------+   +----------------------+
| - studentNo: String|   | - title: String      |
| - gpa: double      |   | - department: String |
+--------------------+   +----------------------+
| + enroll(c)        |   | + assignCourse(c)    |
+--------------------+   +----------------------+
         |   *                   *   |
         |                           |
         +-------------+---------------+
                       | 0..*
                       v
+-----------------------------------------+
|                 Course                  |
+-----------------------------------------+
| - courseCode: String                    |
| - title: String                         |
| - credits: int                          |
+-----------------------------------------+
| + getSyllabus(): String                 |
+-----------------------------------------+
                       |
                       | 1..*
                       v
+-----------------------------------------+
|               Department                |
+-----------------------------------------+
| - deptCode: String                      |
| - deptName: String                      |
+-----------------------------------------+
| + listCourses(): List                   |
+-----------------------------------------+
```
## Class Responsibilities
- **Person:** Stores shared identity fields (`id`, `name`, `email`) and common details output.
- **Student:** Extends `Person`, tracks student number and GPA, and handles course enrollment.
- **Instructor:** Extends `Person`, tracks academic title and department, and handles course assignment.
- **Course:** Holds course code, title, credits, and syllabus information.
- **Department:** Holds department code and name, and lists offered courses.

## Relationship Notes
- **Inheritance (`^`):** `Student` and `Instructor` inherit common attributes and methods from `Person`.
- **Association & Multiplicity (`0..*`, `*`):** Students enroll in courses and instructors teach courses across many-to-many relations.
- **Department Ownership (`1..*`):** Each course belongs to a department, and a department provides one or more courses.
