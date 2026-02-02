# tvet-student
This documentation integrates your db.js file with the Student Course Registration System architecture shown in your diagram. It provides a clear overview of the data flow and the relational structure for your GitHub repository.

📊 Database Documentation
This project uses a MySQL relational database named tvet_db to power the Student Course Registration System. The database handles student information, course management, and enrollment tracking.

🗺️ System Architecture
The system follows a standard Level 0 DFD (Data Flow Diagram) structure:

Users submit student info, course data, and enrollment requests.

The Registration System (Node.js/Express) processes these requests.

Data is persisted and retrieved from the Student Database.

🏗️ Entity-Relationship Diagram (ERD)
The database consists of three core tables with the following relationships:

1. Students Table
Stores personal information for all registered students.

student_id (INT, PK): Unique identifier for each student.

first_name (VARCHAR): Student's given name.

last_name (VARCHAR): Student's family name.

email (VARCHAR): Contact email address.

created_at (TIMESTAMP): Record creation date.

2. Courses Table
Maintains the catalog of available courses.

course_id (INT, PK): Unique identifier for each course.

course_name (VARCHAR): The title of the course.

created_at (TIMESTAMP): Record creation date.

3. Enrollments Table
A junction table managing the Many-to-Many relationship between Students and Courses.

enrollment_id (INT, PK): Unique identifier for the enrollment record.

student_id (INT, FK): Links to the Students table.

course_id (INT, FK): Links to the Courses table.

💻 Implementation (db.js)
The connection is established using the mysql2 driver. Below is the configuration used to connect the application logic to the ERD defined above:

JavaScript
const mysql = require('mysql2');

const db = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: '', // Ensure this matches your local MySQL setup
  database: 'tvet_db'
});

db.connect(err => {
  if (err) throw err;
  console.log('Database Connected');
});

module.exports = db;
🛠️ Setup Instructions
Initialize Database:

SQL
CREATE DATABASE tvet_db;
Run Migrations: Execute the table creation scripts (based on the ERD above) to set up the students, courses, and enrollments tables.

Environment: Ensure your local MySQL server is running on localhost before starting the Node.js application.

Would you like me to generate the full SQL CREATE TABLE scripts based on the attributes in your ERD?
