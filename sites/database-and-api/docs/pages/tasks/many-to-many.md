# Many-to-Many Relationship Scenarios

For the below scenarios create:

    - ERD with many-to-many relationships
    - Expand with junction tables
    - Identify composite keys where they can be used

## Scenario 1: Students and Courses

A training organisation offers multiple courses to students.

Students can enrol in several courses throughout the year. Each course may have many students enrolled.

The organisation wants to keep track of:

- Student details
- Course information
- Which students are enrolled in which courses

**Entities**

- Students
- Courses
- Enrolments

**Questions**

1. Can a student enrol in multiple courses?
2. Can a course have multiple students?
3. What information should be stored in the Enrolments table?

---

## Scenario 2: Customers and Products

An online store sells a variety of products.

Customers can purchase multiple products in a single order, and the same product can be purchased by many different customers.

The store wants to record:

- Customer details
- Product details
- Purchase history

**Entities**

- Customers
- Products
- Purchases

**Questions**

1. Can a customer buy multiple products?
2. Can a product be purchased by multiple customers?
3. What information should be stored about each purchase?

---

## Scenario 3: Employees and Projects

A software development company assigns employees to projects.

An employee may work on several projects at the same time. Each project may have multiple employees assigned.

Management wants to track:

- Employee information
- Project information
- Employee project assignments

**Entities**

- Employees
- Projects
- Assignments

**Questions**

1. Can an employee work on multiple projects?
2. Can a project have multiple employees?
3. What information could be stored in the Assignments table?

---

## Scenario 4: Authors and Books

A publishing company manages books written by authors.

An author can write multiple books. Some books may be written by multiple authors.

The company wants to store:

- Author information
- Book information
- Which authors wrote which books

**Entities**

- Authors
- Books
- BookAuthors

**Questions**

1. Can an author write multiple books?
2. Can a book have multiple authors?
3. What attributes might be useful in the linking table?

---

## Scenario 5: Players and Teams

A sporting association manages players and teams across multiple seasons.

A player may play for different teams over several years. A team will have many players throughout its history.

The association wants to record:

- Player information
- Team information
- Team memberships

**Questions**

1. Can a player belong to multiple teams over time?
2. Can a team have multiple players?
3. How could the database record which season a player participated in?

---

## Scenario 6: Doctors and Patients

A medical clinic manages appointments between doctors and patients.

A doctor can see many patients. A patient may visit multiple doctors depending on their healthcare needs.

The clinic wants to record:

- Doctor information
- Patient information
- Appointment history

**Entities**

- Doctors
- Patients
- Appointments

**Questions**

1. Can a doctor see multiple patients?
2. Can a patient see multiple doctors?
3. What information should be stored in the Appointments table?
4. Could appointment date and time be useful attributes?

---

## Scenario 7: Movies and Actors

A movie production company maintains information about films and actors.

An actor may appear in many movies throughout their career. A movie may contain many actors.

The company wants to store:

- Actor information
- Movie information
- Acting roles

**Entities**

- Actors
- Movies
- CastMembers

**Questions**

1. Can an actor appear in multiple movies?
2. Can a movie contain multiple actors?
3. What information could be stored in the CastMembers table?
4. Should the character name be recorded?

---

## Scenario 8: Members and Events

A community centre runs workshops, classes, and special events throughout the year.

Members can attend many events. Each event can have many members attending.

The centre wants to keep track of:

- Member details
- Event details
- Event registrations

**Entities**

- Members
- Events
- Registrations

**Questions**

1. Can a member attend multiple events?
2. Can an event have multiple members attending?
3. What information should be stored in the Registrations table?
4. Would registration date or attendance status be useful?

