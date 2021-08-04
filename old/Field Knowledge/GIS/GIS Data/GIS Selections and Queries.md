# GIS Selections and Queries

Created: Sep 2, 2020 3:01 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 7
Topic: [[Data Structures in GIS]]
UID: 202009021501

Date: Aug 23, 2020

### Topic: Selections and Queries

### Recall

### Notes

Maps are the end products of research. Let's sharpen our spatial awareness and critical thinking

2 Types of Analytical Approaches:

- Topological Functions
    - Uses geographic relations
    - "Which state does Los Angeles County reside in"
    - "Which states does California border?"
- Non-topological Functions
    - Queries and statistics displayed on a map
    - Spatial Database Query
    - Statistical Computations
    - "Average income of french citizens"
    - "Population of China"
- These functions are NOT MUTUALLY EXCLUSIVE. They got lots of synergy

**Attribute Database Queries**

- Most common form of query
- Interrogate the attribute table of a certain dataset
- Performed using **SQL**

**SQL** - Structured/Standard Query Language

- Pronounced as "Sequel"
- 3 general operations:
- Select
    - Select specific rows of a table
- Project
    - Pull items from specified Columns
- Join
    - Relate two tables based off of a common variable (found in both tables)

```sql
SELECT <attribute name or variable>
	FROM <table>
	WHERE <condition statement>

% - the wildcard character in sql
"" - double quotes are for variables
'' - single quotes are for strings
```

- Standard Operators
    - Relational (> ≥ < ≤ =)
    - Mathematical (+ - * /)
    - Boolean (AND, OR, NOT)

![[old/Field Knowledge/GIS/GIS Data/GIS Selections and Queries/Untitled.png]]

![[old/Field Knowledge/GIS/GIS Data/GIS Selections and Queries/Untitled 1.png]]

**SUMMARY:**