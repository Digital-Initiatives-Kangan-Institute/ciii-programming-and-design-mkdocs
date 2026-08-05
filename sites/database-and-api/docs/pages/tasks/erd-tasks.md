# ERD Practice Business Cases

## Library Book Loans

**Required Entities and Attributes**

**Member**

- MemberID
- FirstName
- LastName
- Email

**Loan**

- LoanID
- LoanDate
- DueDate

**Book**

- BookID
- Title
- Author
- Genre

**Scenario**

A local library wants to keep track of its members, books, and borrowing activity. Members can borrow many books over time, and the library needs to record when each book is borrowed and when it is due back. The system should allow staff to see which member borrowed a book, the details of the book, and the history of loans made by each member.

---

## School Students and Classes

**Required Entities and Attributes**

**Class**

- ClassID
- ClassName
- Room

**Student**

- StudentID
- FirstName
- LastName
- DateOfBirth

**Scenario**

A school organises students into classes. Each class has a name and is assigned to a room. A class can have many students, but each student belongs to one class. The school wants to store student details and be able to identify which class each student is currently assigned to.

---

## Customer Orders

**Required Entities and Attributes**

**Customer**

- CustomerID
- Name
- Email

**Order**

- OrderID
- OrderDate
- TotalAmount

**OrderNote**

- NoteID
- NoteText
- CreatedDate

**Scenario**

An online store keeps records of its customers and the orders they place. A customer can place many orders over time. Each order includes information such as the order date and total amount. Staff may also add notes to an order, such as delivery instructions, customer requests, or follow-up comments. The store wants to track customers, their orders, and any notes linked to those orders.

---

## Veterinary Clinic

**Required Entities**

- Owner
- Pet

**Scenario**

A veterinary clinic stores information about pet owners and their pets. Each owner can have one or more pets registered at the clinic. The clinic needs to record owner contact details as well as basic pet information such as the pet name and species. Staff should be able to see which pets belong to each owner.

---

## Company Departments

**Required Entities**

- Department
- Employee
- TrainingRecord

**Scenario**

A company is organised into departments. Each department can have many employees, but each employee belongs to one department. Employees may also complete training courses during their employment. The company wants to keep employee details, identify which department they work in, and maintain a record of training completed by each employee.

---

## Real Estate Agency

**Required Entities**

- Owner
- Property

**Scenario**

A real estate agency manages property owners and their properties. Each owner can have one or more properties listed with the agency. The agency needs to store owner contact details and property information such as address and suburb. Staff should be able to view all properties connected to a particular owner.

---

## Hospital Patients

A hospital stores details about its patients. Each patient can attend the hospital many times over the years for consultations, check-ups, and treatments. Whenever a patient visits, an appointment record is created that includes the appointment date and the doctor they will see. The hospital would like to keep a history of all appointments associated with each patient.

---

## Event Management

A community organisation runs a variety of events throughout the year, such as workshops, seminars and networking sessions. People can register to attend these events. Each registration is recorded with the date it was made, and attendee details are captured for each registration. The organisation wants to track which attendees have registered for which events and maintain a history of all registrations.

---

## University Courses

A university offers a range of courses to students. Each student is enrolled in one course and may complete multiple assessments during their studies. Assessment results are recorded along with the assessment name and score achieved. The university wants to monitor student progress and maintain a record of all assessment outcomes linked to each student and their course.

---

## Cafe Loyalty Program

A cafe operates a loyalty program for its regular customers. When customers join, their membership details are recorded. Each time a member makes a purchase, the transaction is stored in the system. Some purchases may result in the member receiving a reward or benefit through the loyalty program. The cafe wants to keep track of member purchases and any rewards earned over time.
