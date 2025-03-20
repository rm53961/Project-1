# MIST 4610 21484 Group 9 Project

**Team Members:**

1) Gabriela Rivera [@Gcr79540](https://github.com/Gcr79540)
2) Daniel Yi [@dmy17582](https://github.com/dmy17582)
3) Maggie Craig [@Maggiecraig108](https://github.com/Maggiecraig108)
4) Rashi Modey [@rm53961](https://github.com/rm53961)
5) John Carr [@jac08171](https://github.com/jac08171)

## **Problem Description**
The task at hand is to design and build a relational database for our tutoring company, Brightpath. Brightpath offers one-on-one tutoring services across multiple subjects, with tutors working in different locations to assist students in scheduled sessions. The session entity serves as the central entity of our data model, capturing essential details about which tutor is teaching, which student is receiving tutoring, the subject being covered, the session location, and its duration. Supporting entities include tutors, students, subjects, assignments, attendance, feedback, locations, and payments—all interconnected to ensure seamless tracking of tutoring activities. Our goal is to build an accurate and functional database that allows us to generate sample data, populate entities with meaningful attributes, and run queries that provide valuable insights. These insights may include student progress tracking, session scheduling, and payment records to help optimize our tutoring services.

## **Data Model**

<img width="600" alt="Screenshot 2025-03-20 at 5 05 42 PM" src="https://github.com/user-attachments/assets/990a47cf-1801-4939-978f-524506a8b0a2" />

Our data model is structured around a hypothetical tutoring company, Brightpath. The Session entity serves as the central focus of our model, representing one-on-one tutoring sessions between students and tutors. Each session captures essential details, including the tutor, student, subject, location, session duration, and feedback.

A Tutor works in a specific Location and teaches students in multiple Subjects, which is why we established a one-to-many relationship between Tutors and Subjects. Additionally, tutors conduct multiple Sessions, forming a one-to-many relationship between Tutors and Sessions.
Each Student participates in multiple Sessions, with their academic progress and engagement tracked through Assignments, Attendance, and Feedback. A one-to-many relationship exists between Students and Assignments, allowing tutors to assign and review work. Similarly, Attendance tracks student participation in sessions, helping monitor engagement.

Brightpath operates in various locations, so we created a Location entity containing address, city, and contact details. Since each Tutor and Session takes place at a specific location, we established relationships between the Location, Tutors, and Sessions.
To evaluate performance and gather insights, we included a Feedback entity. Tutors provide feedback on student progress, and students can also review their learning experiences. The Feedback entity links to both Tutors and Sessions, ensuring a structured approach to tracking educational outcomes.

Brightpath also processes Payments for tutoring services. Each Session has an associated Payment record, capturing payment amount, date, and method. This enables tracking of revenue and ensures that payments are linked to completed sessions.

Finally, the Assignment entity allows tutors to assign tasks related to a specific Session and Subject. Each Assignment includes a due date, description, and completion status, ensuring structured learning for students.
This relational model enables Brightpath to effectively manage tutoring services, track student progress, monitor tutor performance, and optimize session scheduling and revenue generation.

## **Queries**
 
## **Simple Queries**


### 1) *This query retrieves all students who are in grade 11 from the student table*

SELECT * FROM student WHERE student_grade = '11';


This query helps managers track the number of 11th-grade students and their information. It can be used for class planning, resource allocation, and monitoring academic goals and interests. From having all the contact information it also makes it easy to see the emails just in case the managers need to send a mass email to students in this grade to give any updates.

<img width="382" alt="Screenshot 2025-03-20 at 5 31 14 PM" src="https://github.com/user-attachments/assets/3b850a6b-d900-4fce-a9d1-b9dcf44a41d1" />








### 2) *This query retrieves all assignments that are pending* 

SELECT * FROM assignment WHERE assignment_status = 'Pending';



 This query helps managers monitor pending assignments. It allows them to identify students who may need additional support when falling behind. If a large number of assignments are pending, it could indicate issues such as poor time management, lack of student engagement, or unclear instructions. This insight can help managers adjust deadlines, provide extra assistance, or intervene early to improve overall student performance. Student success is what drives business for BrightPath tutoring and its important to check for poor performance.

<img width="382" alt="Screenshot 2025-03-20 at 5 31 14 PM" src="https://github.com/user-attachments/assets/e3a06302-7c77-44f4-8373-4c84371cac35" />



### 3) *This query ounts the total number of tutors who work at Brightpath*

Count the total number of tutors
SELECT COUNT(*) AS total_tutors FROM tutor;


It allows the managers to see how many tutors they have working at their company. Knowing this information is helpful to the company because they are able to have an accurate view of the labor resources that are available to them. Managers are then able to decide whether they need to hire more tutors to meet an increased demand in the education market. They are also able to forecast whether they will need to hire/fire tutors depending on whether more kids are signing up. This query allows managers to identify where they should allocate resources. 


<img width="438" alt="Screenshot 2025-03-20 at 5 32 25 PM" src="https://github.com/user-attachments/assets/ab089036-827c-471d-8e4c-516d0ab8920d" />




### 4) *This query gets the names and contact details of all tutors who charge more than $30 per session*

SELECT tutor_name, tutor_phone, tutor_email 
FROM tutor 
WHERE tutor_rate > 30;


This information is useful because it allows managers to compile a list of their tutors who fall on the more expensive end of the spectrum. Managers can recommend specific tutors within their company to certain families who are looking to invest a little extra money in their children’s education, Another benefit of compiling this information is that this can be shared with families who cannot afford expensive tutoring. If a family does not want to spend over $30 per session, then the managers know which tutors to avoid recommending. This will lead to clients feeling like they get personalized options for tutors who meet their specific needs, leading to client satisfaction.

<img width="446" alt="Screenshot 2025-03-20 at 5 35 39 PM" src="https://github.com/user-attachments/assets/3804260f-2b57-4d5c-86cb-93bc415dfee6" />




## **Complex Queries** 


### 5) *Find students who have at least one completed assignment* 


SELECT DISTINCT s.student_id, s.student_name
FROM student s
JOIN assignment a ON s.student_id = a.student_id
WHERE a.assignment_status = 'Completed';


This query helps managers track student engagement by identifying those who have completed assignments and being able to grab feedback right away. It helps BrightPath look at ways to improve and get everyone's opinions. This helps Bright Path account for everyone since it shows students that completed at least one assignment.


<img width="309" alt="Screenshot 2025-03-20 at 5 37 06 PM" src="https://github.com/user-attachments/assets/61188934-9686-4e84-bfb2-17884f87abc1" />





### 6) *This query calculates the average tutor rate for each subject* 

SELECT sub.subject_name, AVG(t.tutor_rate) AS average_rate
FROM tutor t
JOIN subject sub ON t.subject_id = sub.subject_id
GROUP BY sub.subject_name;

This helps managers analyze tutor costs across subjects, set competitive pricing, budget for tutoring services, and ensure fair compensation. This data can also be used when obtaining more tutors by giving them a recommended price to charge for service.

<img width="325" alt="Screenshot 2025-03-20 at 5 37 45 PM" src="https://github.com/user-attachments/assets/dcc309b2-11fe-4558-b981-37ebb3f4d3b4" />





### 7) *This query retrieves tutors who have received at least one low feedback rating (below 3)*


List tutors who have received at least one feedback rating below 3
SELECT DISTINCT t.tutor_id, t.tutor_name
FROM tutor t JOIN feedback f ON t.tutor_id = f.tutor_id
WHERE f.feedback_rating 


This helps managers identify tutors with poor ratings, assess performance issues, provide training or support, and maintain service quality. Poor service means less students coming back and its important to catch on to be able to implement change.

<img width="400" alt="Screenshot 2025-03-20 at 5 38 17 PM" src="https://github.com/user-attachments/assets/c5dd0ac6-dce5-4bc3-8431-e64dbb29c1b6" />


                   

### 8) *This query finds the most popular subject based on the number of tutoring sessions* 

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


<img width="405" alt="Screenshot 2025-03-20 at 5 39 36 PM" src="https://github.com/user-attachments/assets/7ec82ba7-c5d7-4737-8bfe-cf153a0d5cfa" />






### 9) *This query helps identify which assignments require paper in order to be completed*

Find assignments whose titles contain the word "Paper"
SELECT * 
FROM assignment
WHERE assignment_title REGEXP '[Pp]aper';


This information could be useful to managers for a number of reasons. If managers anticipate the rise of many paper assignments, they could prepare by buying more paper or ink for their printing equipment. They could also avoid buying more computers or other online resources, which would save them money. This information can also be relayed to parents and students who want to sign up, as some customers would prefer paper assignments over online ones because it helps them learn better and retain information.

<img width="452" alt="Screenshot 2025-03-20 at 5 40 18 PM" src="https://github.com/user-attachments/assets/6734e1f3-0603-4c60-9f1e-18852c5d89ba" />






### 10) *This query gives a list of students who have not completed any assignment* 

SELECT * FROM student
WHERE NOT EXISTS (
SELECT 1
FROM assignment
WHERE assignment.student_id = student.student_id AND assignment.assignment_status = 'Completed'
);


Query 10 depicts a list of students who have not completed any assignments in their time at Brightpath so far. 
This information is very beneficial to managers because it can either show which students are new to Brightpath or show students who are slacking in their work. For new students, managers can see who has not made any progress yet. For current students, the staff will be able to analyze who is not completing their work and then take further future action accordingly, whether that be to request for additional sessions or direct special, one on one attention to the student in order to determine the cause for incompletion. This way, we can see whether a student is just not completing work, doesn’t understand material, or has another obstacle hindering their ability to work.

<img width="408" alt="Screenshot 2025-03-20 at 5 40 52 PM" src="https://github.com/user-attachments/assets/f85b35da-0b40-40f5-b5bd-a75accb393c5" />


## *Data Dictionary:*
<img width="747" alt="Screenshot 2025-03-20 at 17 25 50" src="https://github.com/user-attachments/assets/c1603126-492b-45cc-938b-03b07063cea5" />

<img width="745" alt="Screenshot 2025-03-20 at 17 26 01" src="https://github.com/user-attachments/assets/5a8d1dc3-61cb-4a5a-a0d6-5fb18b5e534a" />
<img width="726" alt="Screenshot 2025-03-20 at 17 26 15" src="https://github.com/user-attachments/assets/f14f5b16-6229-458d-aa6d-0014b429f07f" />

<img width="740" alt="Screenshot 2025-03-20 at 17 26 42" src="https://github.com/user-attachments/assets/67f9ed9e-4741-4359-9875-8c05463ff10a" />

<img width="737" alt="Screenshot 2025-03-20 at 17 27 01" src="https://github.com/user-attachments/assets/95cef90f-ff47-4781-b1b1-41ab99a3377a" />

<img width="730" alt="Screenshot 2025-03-20 at 17 27 12" src="https://github.com/user-attachments/assets/d0da2fd6-bd75-4b41-b4bf-ee4f8a18b735" />

<img width="739" alt="Screenshot 2025-03-20 at 17 27 20" src="https://github.com/user-attachments/assets/af6e8690-5e90-46af-9144-2cbab5e0fc41" />

<img width="730" alt="Screenshot 2025-03-20 at 17 27 30" src="https://github.com/user-attachments/assets/de54f530-6f06-40e5-9dbb-d66ee07e8e53" />

<img width="730" alt="Screenshot 2025-03-20 at 17 27 37" src="https://github.com/user-attachments/assets/f28e407b-5c4a-4f2f-af61-6259bb80e40d" />

<img width="738" alt="Screenshot 2025-03-20 at 17 27 43" src="https://github.com/user-attachments/assets/81526614-a9cd-48fc-b7d7-1055fff52cb7" />

<img width="721" alt="Screenshot 2025-03-20 at 17 27 50" src="https://github.com/user-attachments/assets/a9df1060-0c74-4435-9147-2b278072dcc7" />


## Database Information:

Name of the database: al_group_21484_g9

##
Thanks for reading!

































































