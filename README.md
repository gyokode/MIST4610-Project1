# Team 6 MIST4610-Group-Project-1

# Team Name
61608 Group 6

**Team Members:**
1. Gio Kim @gyokode
2. Matheo Brooks @matheobrooks-cpu
3. Luka Gangemi @lukagangemi
4. Luke Piazza @lukepiazza479

# Scenario Description
Our project is a database for managing data at a boutique fitness studio. Our core entity is the Members table, that keeps data like their ID number, their name, and their contact information. The member entity has relationships with payment and membership information, feedback, attendance, and the types of classes that the members attend. We also included entities related to equipment, vendors, and purchases to more accurately capture the scope of the boutique.

# Data Model
<img width="1705" height="1331" alt="image" src="https://github.com/user-attachments/assets/d111cb4d-c106-4ab6-84e6-b078ea7661ca" />

### Data Model Explanation
Our data model represents the operations of a boutique fitness studio and the relationships between its core functional areas. Members belong to specific membership plans, which is shown through the one‑to‑many relationship between Memberships and Members, and each member can make multiple payments recorded in the Member_Payments table. Members attend scheduled fitness classes, so we created an associative entity, Attendance_Logs, to capture the many‑to‑many relationship between Members and Class_Session, including check‑in times and attendance status. Class_Session itself branches from both Classes and Trainers, since each scheduled session is tied to a class type, a trainer, a room, and a specific time window. Trainers can lead many sessions and also receive feedback from members, which is represented by the Feedback table linking Members, Trainers, and Class_Session. Finally, we included a one-to-many recursive relationship on Trainers, indicating the possibility of a trainer superviser managing more than one other trainer.

The physical layout of the studio is represented through Rooms and Equipment. Rooms_has_Equipment serves as an associative entity that shows which equipment is located in which room, along with quantities and inspection dates. Equipment is purchased from external vendors, so Equipment_Purchase captures the many‑to‑many relationship between Vendors and Equipment, including purchase dates, unit costs, and quantities. Altogether, the model provides a complete view of how members interact with classes, trainers, rooms, and equipment, while also supporting operational needs such as payments, scheduling, feedback, and vendor management.


## Data Dictionary
<img width="1289" height="806" alt="image" src="https://github.com/user-attachments/assets/9ae82b22-5b47-4531-9b01-8b5218ea2a59" />
<img width="1323" height="1122" alt="image" src="https://github.com/user-attachments/assets/13593aac-5572-41e4-a0e1-d8feb78b1905" />
<img width="1288" height="1161" alt="image" src="https://github.com/user-attachments/assets/aad130db-ff04-4ab6-ad8f-f954d0caf275" />
<img width="1310" height="1301" alt="image" src="https://github.com/user-attachments/assets/9bf6889b-d80f-4c47-9626-c869092723f9" />
<img width="1293" height="1392" alt="image" src="https://github.com/user-attachments/assets/01fa583e-ab04-43f1-a11a-20ee0d0bfc77" />
<img width="1358" height="1164" alt="image" src="https://github.com/user-attachments/assets/e0441814-c490-4599-8efa-3c969a90c6a0" />
<img width="1319" height="1174" alt="image" src="https://github.com/user-attachments/assets/2577728b-ba16-4ec7-a9b3-dcb130b292f5" />
<img width="1333" height="626" alt="image" src="https://github.com/user-attachments/assets/32885db1-b852-442d-9cbc-b05373c2eebc" />
<img width="1322" height="696" alt="image" src="https://github.com/user-attachments/assets/b2a671dc-c75f-4ea4-814d-80e4567624be" />
<img width="1329" height="555" alt="image" src="https://github.com/user-attachments/assets/a3feb206-48ef-47ed-a713-8834b3283b4d" />
<img width="1298" height="943" alt="image" src="https://github.com/user-attachments/assets/10e31701-106b-422c-b7c5-55b33f8fcee2" />
<img width="1314" height="829" alt="image" src="https://github.com/user-attachments/assets/644f71ef-af2a-4a0b-8444-cf092b38a2a9" />
<img width="1301" height="862" alt="image" src="https://github.com/user-attachments/assets/8682a4a9-5ba1-4e16-970c-2a488c3fc4f8" />







## Ten Queries
We have developed 10 unique queries (6 complex, 4 simple) to provide actionable business intelligence.

### 1. Simple Queries
**Q1: List all trainers hired after January 1, 2024.**
* **Managerial Justification:** Helps management identify which staff members are still in their introductory or training phases.
* **SQL:** `SELECT first_name, last_name, hire_date FROM Trainers WHERE hire_date > '2024-01-01';`

**Q2: Find all classes with "Hard" difficulty level.**
* **Managerial Justification:** Ensures that the studio is offering enough high-intensity options for advanced members.
* **SQL:** `SELECT class_name FROM Classes WHERE difficulty = 'Hard';`

**Q3: Count total active members.**
* **Managerial Justification:** Provides an immediate snapshot of the studio's current market reach and growth.
* **SQL:** `SELECT COUNT(member_id) AS Total_Members FROM Members;`

**Q4: Identify equipment with a purchase cost over $500.**
* **Managerial Justification:** Highlights high-value assets that require strict maintenance schedules to protect the investment.
* **SQL:** `SELECT equipment_id, unit_cost FROM Equipment_Purchase WHERE unit_cost > 500;`

### 2. Complex Queries

**Q5: Which classes had the highest attendance?**
* **Managerial Justification:** This query returns the name of the class, the ID of the session, the start time, and the attendance count for the different classes offered in descending order. This allows managers to see which classes are drawing in the biggest crowds, which could impact class pricing and scheduling. For example, in this scenario, the studio may want to increase class sessions for Yoga Flow, Boxing Fundamentals, and Meditation & Breathwork to maximize attendance and revenue since they were most popular.

*  <img width="1923" height="1130" alt="image" src="https://github.com/user-attachments/assets/1b60f392-3258-4fa4-9d7c-eb655a51fa7d" />

**Q6: Total revenue generated by each membership tier.**
* **Managerial Justification:** Identifies which membership types are driving the most profit, aiding in pricing strategy.
* <img width="1935" height="787" alt="image" src="https://github.com/user-attachments/assets/50a86852-1c3d-4852-875a-7fa610803303" />


**Q7: Classes with average feedback rating above 4. Results are ordered by rating descending.**
* **Managerial Justification:** Managers can identify which classes consistently receive high ratings. These are the gym's strongest offerings and may warrant more session slots, promotion, or increased capacity.
* <img width="958" height="456" alt="Screenshot 2026-04-02 at 4 00 58 PM" src="https://github.com/user-attachments/assets/6ce62427-fef4-40fb-9922-fcd8fbad0fe7" />


**Q8: Members who have never attended a class.**
* **Managerial Justification:** Identifies "ghost members" for targeted re-engagement campaigns to reduce churn.
* **SQL:** `SELECT first_name, last_name FROM Members WHERE member_id NOT IN (SELECT member_id FROM Attendance_Logs);`

**Q9: Top 3 most popular classes by attendance.**
* **Managerial Justification:** Directs management to add more sessions for the most popular class types.
* **SQL:** `SELECT c.class_name, COUNT(a.member_id) AS Attendance FROM Classes c JOIN Class_Session s ON c.class_id = s.class_id JOIN Attendance_Logs a ON s.session_id = a.session_id GROUP BY c.class_name ORDER BY Attendance DESC LIMIT 3;`

**Q10: Inventory count of equipment per room.**
* **Managerial Justification:** Facilitates room setup audits and ensures equipment is distributed correctly for scheduled classes.
* **SQL:** `SELECT r.room_name, e.equipment_name, re.quantity_in_room FROM Rooms r JOIN Rooms_has_Equipment re ON r.room_id = re.room_id JOIN Equipment e ON re.equipment_id = e.equipment_id;`

**Q11: Employee-to-Manager reporting list.**
* **Managerial Justification:** Clarifies the internal organizational chart for better communication and accountability.
* **SQL:** `SELECT t1.first_name AS Staff, t2.first_name AS Manager FROM Trainers t1 LEFT JOIN Trainers t2 ON t1.supervisor_id = t2.trainer_id;`

## Query Feature Matrix
| Query | Joins | Subqueries | Group By | Aggregate Functions | Sorting |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Q1-4 | | | | X | X |
| Q5 | X | | X | X | |
| Q6 | X | | X | X | |
| Q7 | | X | | | |
| Q8 | X | | X | X | X |
| Q9 | X | | | | |
| Q10 | X | | | | |

## Database Information
* **Database Name:** ns_Sp26_61608_Group6
* **Stored Procedures:** All queries are implemented as stored procedures following the `TP_Qx` format (e.g., `CALL TP_Q1();`).
