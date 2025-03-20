 **Team 1 Mist 4610 Group Project 1** |
Team Name:
MIST 4610 3:55-5:10 Group 9

**Team Members:**
Gabriela Rivera @gcr79540@uga.edu
Daniel Yi @dmy17582@uga.edu
Maggie Craig @src80607@uga.edu
Rashi Modey @rm53961@uga.edu
John Carr @jac08171@uga.edu

**Problem Description**
The task at hand is to design and build a relational database for our tutoring company, Brightpath. Brightpath offers one-on-one tutoring services across multiple subjects, with tutors working in different locations to assist students in scheduled sessions. The session entity serves as the central entity of our data model, capturing essential details about which tutor is teaching, which student is receiving tutoring, the subject being covered, the session location, and its duration. Supporting entities include tutors, students, subjects, assignments, attendance, feedback, locations, and payments—all interconnected to ensure seamless tracking of tutoring activities. Our goal is to build an accurate and functional database that allows us to generate sample data, populate entities with meaningful attributes, and run queries that provide valuable insights. These insights may include student progress tracking, session scheduling, and payment records to help optimize our tutoring services.

**DATA MODEL**

<img width="642" alt="Screenshot 2025-03-20 at 5 05 42 PM" src="https://github.com/user-attachments/assets/990a47cf-1801-4939-978f-524506a8b0a2" />
Our data model is structured around a hypothetical tutoring company, Brightpath. The Session entity serves as the central focus of our model, representing one-on-one tutoring sessions between students and tutors. Each session captures essential details, including the tutor, student, subject, location, session duration, and feedback.
A Tutor works in a specific Location and teaches students in multiple Subjects, which is why we established a one-to-many relationship between Tutors and Subjects. Additionally, tutors conduct multiple Sessions, forming a one-to-many relationship between Tutors and Sessions.
Each Student participates in multiple Sessions, with their academic progress and engagement tracked through Assignments, Attendance, and Feedback. A one-to-many relationship exists between Students and Assignments, allowing tutors to assign and review work. Similarly, Attendance tracks student participation in sessions, helping monitor engagement.
Brightpath operates in various locations, so we created a Location entity containing address, city, and contact details. Since each Tutor and Session takes place at a specific location, we established relationships between the Location, Tutors, and Sessions.
To evaluate performance and gather insights, we included a Feedback entity. Tutors provide feedback on student progress, and students can also review their learning experiences. The Feedback entity links to both Tutors and Sessions, ensuring a structured approach to tracking educational outcomes.
Brightpath also processes Payments for tutoring services. Each Session has an associated Payment record, capturing payment amount, date, and method. This enables tracking of revenue and ensures that payments are linked to completed sessions.
Finally, the Assignment entity allows tutors to assign tasks related to a specific Session and Subject. Each Assignment includes a due date, description, and completion status, ensuring structured learning for students.
This relational model enables Brightpath to effectively manage tutoring services, track student progress, monitor tutor performance, and optimize session scheduling and revenue generation.

