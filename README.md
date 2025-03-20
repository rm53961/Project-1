 **Team 1 Mist 4610 Group Project 1** |
Team Name:
MIST 4610 3:55-5:10 Group 9

**Team Members:**
[Gabriela Rivera](https://github.com/Gcr79540)
[Daniel Yi](https://github.com/dmy17582)
[Maggie Craig](https://github.com/Maggiecraig108)
[Rashi Modey](https://github.com/rm53961)
[John Carr](https://github.com/jac08171)

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

**Queries
 
Simple Queries**


This query retrieves all students who are in grade 11 from the student table.
SELECT * FROM student WHERE student_grade = '11';


This query helps managers track the number of 11th-grade students and their information. It can be used for class planning, resource allocation, and monitoring academic goals and interests. From having all the contact information it also makes it easy to see the emails just in case the managers need to send a mass email to students in this grade to give any updates.




This query retrieves all assignments that are pending. 
SELECT * FROM assignment WHERE assignment_status = 'Pending';


 This query helps managers monitor outstanding assignments. It allows them to identify students who may need additional support or follow-up. If a large number of assignments are pending, it could indicate issues such as poor time management, lack of student engagement, or unclear instructions. This insight can help managers adjust deadlines, provide extra assistance, or intervene early to improve overall student performance. Student success is what drives business for BrightPath tutoring.








Count the total number of tutors
SELECT COUNT(*) AS total_tutors FROM tutor;

Query 1 counts the total number of tutors who work at Brightpath.


It allows the managers to see how many tutors they have working at their company. Knowing this information is helpful to the company because they are able to have an accurate view of the labor resources that are available to them. Managers are then able to decide whether they need to hire more tutors to meet an increased demand in the education market. They are also able to forecast whether they will need to hire/fire tutors depending on whether more kids are signing up. This query allows managers to identify where they should allocate resources. 












Get the names and contact details of all tutors who charge more than $30 per session:
SELECT tutor_name, tutor_phone, tutor_email 
FROM tutor 
WHERE tutor_rate > 30;


Query 2 lists the name and contact information for all the tutors who charge more than $30 per session a student.


This information is useful because it allows managers to compile a list of their tutors who fall on the more expensive end of the spectrum. Managers can recommend specific tutors within their company to certain families who are looking to invest a little extra money in their children’s education, Another benefit of compiling this information is that this can be shared with families who cannot afford expensive tutoring. If a family does not want to spend over $30 per session, then the managers know which tutors to avoid recommending. This will lead to clients feeling like they get personalized options for tutors who meet their specific needs, leading to client satisfaction.





Complex Queries 


This query retrieves a list of students who have completed at least one assignment by joining the student and assignment tables. It ensures that only distinct student records appear in the results.




Find students who have at least one completed assignment
SELECT DISTINCT s.student_id, s.student_name
FROM student s
JOIN assignment a ON s.student_id = a.student_id
WHERE a.assignment_status = 'Completed';



This query helps managers track student engagement by identifying those who have completed assignments. It aids in monitoring performance, assessing coursework effectiveness, identifying students needing support, and improving resource allocation.




This query calculates the average tutor rate for each subject by grouping tutors based on the subject they teach.


Get the average tutor rate for each subject
SELECT sub.subject_name, AVG(t.tutor_rate) AS average_rate
FROM tutor t
JOIN subject sub ON t.subject_id = sub.subject_id
GROUP BY sub.subject_name;





This helps managers analyze tutor costs across subjects, set competitive pricing, budget for tutoring services, and ensure fair compensation.






This query retrieves tutors who have received at least one low feedback rating (below 3). It ensures that each tutor appears only once in the results.


List tutors who have received at least one feedback rating below 3
SELECT DISTINCT t.tutor_id, t.tutor_name
FROM tutor t JOIN feedback f ON t.tutor_id = f.tutor_id
WHERE f.feedback_rating 

This helps managers identify tutors with poor ratings, assess performance issues, provide training or support, and maintain service quality.






































































Find the most popular subject based on the number of tutoring sessions
SELECT session_subject, COUNT(*) AS session_count
FROM session GROUP BY session_subject
HAVING COUNT(*) > (SELECT AVG(session_count)
FROM (
SELECT session_subject, COUNT(*) AS session_count
FROM session
GROUP BY session_subject) AS avg_session_count
);


Query 8 identifies the most popular subject that students choose to be tutored in at Brightpath based on which subject has the most people sign up for tutoring.
This information would help managers determine which subject students want the most tutoring in, which also helps them see what is bringing the company the most revenue. Knowing their company’s strengths as well as what services customers and students are most looking forward to will allow Brightpath to make smarter business decisions. For example, if math is a popular subject to be tutored in, then Brightpath will push more marketing efforts towards their math tutors. Also, managers could look at hiring more math tutors to meet the increased demand from students.









Find assignments whose titles contain the word "Paper"
SELECT * 
FROM assignment
WHERE assignment_title REGEXP '[Pp]aper';


This query helps identify which assignments require paper in order to be completed.
This information could be useful to managers for a number of reasons. If managers anticipate the rise of many paper assignments, they could prepare by buying more paper or ink for their printing equipment. They could also avoid buying more computers or other online resources, which would save them money. This information can also be relayed to parents and students who want to sign up, as some customers would prefer paper assignments over online ones because it helps them learn better and retain information.







Get a list of students who have not completed any assignment
SELECT * FROM student
WHERE NOT EXISTS (
SELECT 1
FROM assignment
WHERE assignment.student_id = student.student_id AND assignment.assignment_status = 'Completed'
);


Query 10 depicts a list of students who have not completed any assignments in their time at Brightpath so far. 
This information is very beneficial to managers because it can either show which students are new to Brightpath or show students who are slacking in their work. For new students, managers can see who has not made any progress yet. For current students, the staff will be able to analyze who is not completing their work and then take further future action accordingly, whether that be to request for additional sessions or direct special, one on one attention to the student in order to determine the cause for incompletion. This way, we can see whether a student is just not completing work, doesn’t understand material, or has another obstacle hindering their ability to work.

