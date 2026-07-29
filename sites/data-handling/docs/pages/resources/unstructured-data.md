# Introduction to Unstructured Data

## Introduction

Not all useful information is stored in rows and columns.

Many organisations collect information in the form of:

- Comments
- Emails
- Support tickets
- Feedback forms
- Survey responses

This type of information is known as unstructured data.

By the end of this module, you will be able to:

- Identify unstructured data
- Understand common challenges
- Extract useful information from text
- Categorise comments
- Prepare text data for analysis

---

## What is Unstructured Data?

Unstructured data is information that does not follow a predefined structure.

Unlike spreadsheets, unstructured data does not naturally fit into rows and columns.

---

## Examples of Unstructured Data

- Survey comments
- Social media posts
- Emails
- Chat transcripts
- Support tickets
- Meeting notes

---

## Structured vs Unstructured Data

**Structured**

| ResponseID | Rating |
|------------|---------|
| R001 | 4 |

**Unstructured**

```text
The youth centre is great but public transport is limited after 6pm.
```

---

## Why Unstructured Data is Valuable

Although difficult to analyse, comments often contain:

- Opinions
- Suggestions
- Concerns
- Opportunities
- Context

This information is often unavailable in numerical data.

---

## Common Challenges

Unstructured data can contain:

- Different wording
- Spelling mistakes
- Abbreviations
- Incomplete sentences
- Mixed topics

---

## Example

Three people may describe the same issue:

```text
Need more buses.
```

```text
Transport is difficult.
```

```text
Hard to get home after activities.
```

Humans recognise a common theme.

Computers require additional processing.

---

## Cleaning Text Data

Before analysis we often clean text.

Common tasks include:

- Removing extra spaces
- Standardising capitalisation
- Fixing formatting
- Removing unwanted characters

---

## Categorising Comments

One of the most common approaches is categorisation.

### Example

Comment:

```text
Need more basketball programs.
```

Category:

```text
Sport
```

---

## Another Example

Comment:

```text
More buses are needed after evening activities.
```

Category:

```text
Transport
```

---

## Keyword Identification

Keywords can help summarise comments.

### Comment

```text
Need more buses after youth activities.
```

### Keywords

```text
buses
transport
```

---

## Creating Categories

Categories help convert free text into structured information.

### Example Categories

- Sport
- Wellbeing
- Education
- Employment
- Transport
- Safety
- Social Activities

---

## Pattern Extraction

Sometimes we need to identify specific information.

**Examples**

- Email addresses
- Reference numbers
- Postcodes
- Dates
- Program names

---

## Example

Text:

```text
Please contact me at student@example.com
```

Extract:

```text
student@example.com
```

---

## Working with Survey Feedback

Survey comments are often highly valuable.

### Example

```text
I would like more study spaces and access to free WiFi.
```

Possible Category:

```text
Education
```

---

## Multiple Categories

Some comments belong to more than one category.

### Example

```text
I would like more buses and safer places to meet friends.
```

Potential Categories:

```text
Transport
Safety
```

---

## Human Review

Not every comment can be categorised automatically.

Some responses require:

- Human judgement
- Context
- Local knowledge

---

## Power Query Text Functions

Useful text functions include:

- Trim
- Clean
- Replace Values
- Split Column
- Extract Text
- Format Text

These functions help convert messy text into structured information.

---

## Preparing Text for Analysis

A common workflow is:

```text
Import Comments
```

↓

```text
Clean Text
```

↓

```text
Extract Keywords
```

↓

```text
Categorise Responses
```

↓

```text
Create Structured Dataset
```

---

## Activity: Categorising Survey Responses

Using the supplied survey comments:

1. Read each response.
2. Identify key themes.
3. Assign a category.
4. Record the category in a new column.

---

## Activity: Extracting Information from Text

Using the supplied comments:

1. Identify keywords.
2. Extract relevant information.
3. Create structured fields.
4. Produce a table suitable for analysis.

---

## Key Takeaways

Unstructured data contains valuable information that often cannot be found in numerical datasets.

Common approaches include:

- Cleaning text
- Extracting keywords
- Categorising responses
- Creating structured datasets

Remember:

> The goal of transforming unstructured data is to convert human language into information that can be consistently analysed.
