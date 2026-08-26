# ORM Tasks: JSON to Relational Model in Supabase

In these activities, you will analyse JSON data, identify entities and relationships, create ERDs, and build relational database tables in Supabase.

By the end of these tasks, you should be able to:

- Identify entities from JSON structures
- Identify attributes and keys
- Determine relationship types
- Create relational models
- Design ERDs
- Implement tables in Supabase
- Import JSON data into a relational database

---

## Book Database 

**Scenario**

A local library maintains a list of books. The data is currently stored as JSON and needs to be converted into a relational database table in Supabase.

**JSON Data**

```json
[
  {
    "bookId": 1,
    "title": "Database Fundamentals",
    "author": "Sarah Wilson",
    "yearPublished": 2023,
    "genre": "Education"
  },
  {
    "bookId": 2,
    "title": "Introduction to Python",
    "author": "David Brown",
    "yearPublished": 2022,
    "genre": "Programming"
  },
  {
    "bookId": 3,
    "title": "Cloud Essentials",
    "author": "Emma Taylor",
    "yearPublished": 2024,
    "genre": "Technology"
  }
]
```

**Tasks**

1. Identify the entity.
2. Identify the attributes.
3. Create an ERD.
4. Create the table in Supabase.
5. Load the data into the table.
6. Verify that all records have been inserted.

---

## Veterinary Clinic Database

**Scenario**

A veterinary clinic manages pet owners and their pets.

Each owner can register multiple pets, but each pet belongs to only one owner.

The JSON data must be converted into a relational database model and implemented in Supabase.

**JSON Data**

```json
[
  {
    "ownerId": 1,
    "ownerName": "Sarah Wilson",
    "phone": "0412345678",
    "pets": [
      {
        "petId": 101,
        "petName": "Max",
        "species": "Dog"
      },
      {
        "petId": 102,
        "petName": "Whiskers",
        "species": "Cat"
      }
    ]
  },
  {
    "ownerId": 2,
    "ownerName": "David Brown",
    "phone": "0498765432",
    "pets": [
      {
        "petId": 103,
        "petName": "Charlie",
        "species": "Dog"
      }
    ]
  }
]
```

**Tasks**

1. Identify the entities.
2. Identify the attributes for each entity.
3. Determine the relationship between the entities.
4. Create an ERD.
5. Create the tables in Supabase.
6. Define primary keys.
7. Define foreign keys.
8. Import the data.

---

## Music Festival Database

**Scenario**

A music festival allows performers to appear on multiple stages. Each stage can also host multiple performers.

The JSON data must be converted into a relational database model and implemented in Supabase.

**JSON Data**

```json
[
  {
    "performerId": 1,
    "performerName": "Electric Pulse",
    "genre": "EDM",
    "stages": [
      {
        "stageId": 10,
        "stageName": "Main Stage",
        "performanceDate": "2026-11-14"
      },
      {
        "stageId": 20,
        "stageName": "Dance Arena",
        "performanceDate": "2026-11-15"
      }
    ]
  },
  {
    "performerId": 2,
    "performerName": "The Acoustic Set",
    "genre": "Folk",
    "stages": [
      {
        "stageId": 30,
        "stageName": "Garden Stage",
        "performanceDate": "2026-11-14"
      },
      {
        "stageId": 10,
        "stageName": "Main Stage",
        "performanceDate": "2026-11-15"
      }
    ]
  },
  {
    "performerId": 3,
    "performerName": "Rock Nation",
    "genre": "Rock",
    "stages": [
      {
        "stageId": 10,
        "stageName": "Main Stage",
        "performanceDate": "2026-11-16"
      }
    ]
  }
]
```

**Tasks**

1. Identify the entities.
2. Identify the attributes for each entity.
3. Determine the relationship between Performer and Stage.
4. Create an ERD.
5. Create the relational model.
6. Create the tables in Supabase.
7. Create all primary keys.
8. Create all foreign keys.
9. Import the data from the JSON.

??? Hint
    > Can a performer appear on multiple stages?
    > Can a stage host multiple performers?

---

## IoT Readings Database

**Scenario**

A database needs to store temperature and humidity readings every hour for a house.  There are sensors placed in different rooms of the house.  Each sensor is assigned to a specific room.

**JSON Data**

```json
[
    {
        "roomId": 1,
        "roomName": "Living Room",
        "readings": [
            {
                "temperature": 21.5,
                "humidity": 45,
                "time"": "2026-11-14T08:00:00Z"
            },
            {
                "temperature": 22.0,
                "humidity": 50,
                "time": "2026-11-14T09:00:00Z"
            },
            {
                "temperature": 22.5,
                "humidity": 55,
                "time": "2026-11-14T10:00:00Z"
            },
            {
                "temperature": 23.0,
                "humidity": 60,
                "time": "2026-11-14T11:00:00Z"
            }
        ]
    },
    {
        "roomId": 2,
        "roomName": "Bedroom",
        "readings": [
            {
                "temperature": 20.0,
                "humidity": 40,
                "time": "2026-11-14T08:00:00Z"
            },
            {
                "temperature": 20.5,
                "humidity": 45,
                "time": "2026-11-14T09:00:00Z"
            },
            {
                "temperature": 21.0,
                "humidity": 50,
                "time": "2026-11-14T10:00:00Z"
            },
            {
                "temperature": 21.5,
                "humidity": 55,
                "time": "2026-11-14T11:00:00Z"
            }
        ]

    }
]
```


**Tasks**

1. Identify the entities.
2. Identify the attributes for each entity.
3. Determine the relationship between Performer and Stage.
4. Create an ERD.
5. Create the relational model.
6. Create the tables in Supabase.
7. Create all primary keys.
8. Create all foreign keys.
9. Import the data from the JSON.

---

## Recipe Database

Using the data found at [https://dummyjson.com/docs/recipes](https://dummyjson.com/docs/recipes)

1. Identify the entities.
2. Identify the attributes for each entity.
3. Determine the relationship between Performer and Stage.
4. Create an ERD.
5. Create the relational model.
6. Create the tables in Supabase.
7. Create all primary keys.
8. Create all foreign keys.
9. Import the some of data from the JSON.  First 5.

---

## Extension Challenge

After building each database in Supabase:

1. Create a query that retrieves all records from the main table.
2. Create a query that retrieves related records using joins.
3. Compare the original JSON structure with the relational model.
4. Explain how an ORM would convert relational data back into JSON.
5. Explain the advantages and disadvantages of storing data as JSON versus storing data in relational tables.

