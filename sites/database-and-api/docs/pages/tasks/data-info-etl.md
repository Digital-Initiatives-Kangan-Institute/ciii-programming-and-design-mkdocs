# Tasks: Data vs Information, Business Rules, ETL and Power Query

## Task: Data vs Information

**Scenario**

A local council has collected information about youth participation in community programs.

Review each item and determine whether it represents **data** or **information**.

| Item | Data or Information? |
|--------|--------|
| Participant ID = 10452 | |
| Age = 16 | |
| 65% of participants are aged under 18 | |
| Program Name = Basketball Skills | |
| Average satisfaction score = 4.2 out of 5 | |
| Suburb = Broadmeadows | |
| Basketball is the most popular program | |
| Attendance = 42 participants | |
| Total attendance increased by 18% compared to last year | |
| Survey Response = "Very Satisfied" | |


**Questions**

1. Which examples are raw facts?
2. Which examples provide meaning or insight?
3. How can data be transformed into information?
4. Why is information more useful for decision-making?

**Extension**

Create three examples of your own:

- One piece of data
- One piece of information
- One example where data has been transformed into information

---

## Task: Turning Information into Data

**Scenario**

A manager wants a report showing the performance of several community programs.

You have been given the following information.

- Basketball is the most popular program.
- Average participant age is 17 years.
- 80% of participants are satisfied with their experience.
- Broadmeadows has the highest number of participants.
- Total attendance increased by 15% compared to last year.

**Task**

For each statement:

1. Identify what information is being presented.
2. Determine what raw data would need to be collected to produce that information.

Complete the table below.

| Information | What Data Would Be Required? |
|------------|------------|
| Basketball is the most popular program | |
| Average participant age is 17 | |
| 80% of participants are satisfied | |
| Broadmeadows has the highest participation rate | |
| Attendance increased by 15% | |


**Discussion Questions**

- Why is information usually easier for managers to understand than raw data?
- What challenges might arise when collecting the required data?
- What data quality issues could affect the accuracy of the information?

---

## Business Case 1: Community Sports Centre

**Scenario**

A community sports centre runs a variety of programs including basketball, futsal and volleyball.

Participants must register before attending a program.

Each participant receives a unique participant ID.

Participants can register for multiple programs.

Each program can have many participants.

Every program is supervised by one coach.

A coach may supervise multiple programs.

Programs cannot operate without an assigned coach.

Attendance must be recorded for every session.

**Task**

Identify at least eight business rules from the scenario.

**Extension Challenge**

Create a list of data fields that would be required to support these business rules.

---

## Business Case 2: Solar Rebate Program

**Scenario**

A local council manages a solar rebate program for residential properties.

Every property must have a property ID.

A property can have multiple owners.

An owner may own multiple properties.

Each rebate application is linked to exactly one property.

A property may submit multiple rebate applications over time.

Solar panel counts must be greater than zero.

Resident counts must be between 1 and 16.

Applications cannot be approved unless all required documents have been submitted.

**Task**

Identify the business rules contained within the scenario.

Write each rule as a clear business rule statement.

Example:

- Every property must have a unique property ID.

**Extension Challenge**

Separate the business rules into:

- Data quality rules
- Validation rules
- Relationship rules

---

## Power Query Practice

For the files below, identify the transformations required and execute them in Power Query.

[solar_data_2.csv](../../assets/solar_data_2.csv)

[names2.xlsx](../../assets/names2.xlsx)
[names3.xlsx](../../assets/names3.xlsx)

**Extension**

After completing the transformations on `names2.xlsx` and `names3.xlsx`, combine the two datasets into a single dataset using the merge function in Power Query.
