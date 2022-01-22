# Tabular Data Relations

Created: Jan 22, 2021 9:38 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 181A
UID: 202101222138

# GIS Data is most useful when you keep this stuff in mind:

- KISS - keep it simple, stupid!
    - Simple architecture is more resilient than complicated, convoluted stuff and works for more general purpose use. Worth investing time to make it simple!
- DRY - don't repeat yourself
    - ensuring the same data aren't stored in several locations will keep your work organized, and save time. More robust system as well!
- Do it right the first time!
    - It takes more time to do it right initially - simple in structure, non-repetitive and non-redundant. It's worth it! Clear documentation helps too

# Organizing Large Amounts of Tabular Data

## Relational Database Management Systems (RDBMS)

Software-driven database platforms

- Store data in two-dimensional tables that are linked to one another using KEY FIELDS
- **Primary Key:** The attribute which UNIQUELY identifies a record in an attribute table
- **Foreign Key:** The attribute corresponding to a primary key in an associated table

Two primary advantages over other database models:

1. Each table can be separately prepared, maintained, edited. Easier to maintain etc.
2. Tables may be maintains separately until the need of a particular query / analysis requires the tables be related! Saves LOTS of memory and speed!

## Choosing good key fields

Key fields must share:

- Identical data types
- Identical data values
- Identical encodings

A good key field is the simplest, least ambiguous standardized value used to refer to a given feature / record. Ideally, not subject to issued with encoding

![[GIS/GIS Data/Tabular Data Relations/Untitled.png]]

## Table Joins

**Joins -** operations that append the information of one table into a second through the use of an attribute or field common to both tables (a **key field**)

- A pair of key fields establishes a **RELATION** between two tables
- relations and sets of key fields can be **DOCUMENTED** in database documentation, which keeps users informed on how to use them properly

It's worth it! I feel like it should go without saying lol

- great potential for redundancy in this model. Each table must contain an attribute corresponding to an attribute in every other related table. Having to update a column of values stored inconsistently across multiple data tables is a PAIN! Cut out duplicates to save time

# Normal Forms of Organizing Data

1. **First Normal Form**: first stage in normalization of relational databases
    - repeating groups and attributes are eliminated by placing them into SEPARATE TABLES, connected via primary keys and foreign keys

        First normal form (1NF) is a property of a relation in a relational database. A relation is in first normal form if and only if the domain of each attribute contains only atomic (indivisible) values, and the value of each attribute contains only a single value from that domain.

        ![[GIS/GIS Data/Tabular Data Relations/Untitled 1.png]]

2. **Second Normal Form**
    - all non-key attributes are made DEPENDENT on the primary key

        ![[GIS/GIS Data/Tabular Data Relations/Untitled 2.png]]

    - better explanation: dept_num and dept_name are pretty much semantic duplicates of each other. They encode the same information, and dept_name is dependent on dept_num
3. **Third Normal Form**
    - all non-primary keys are made MUTUALLY EXCLUSIVE

        ![[GIS/GIS Data/Tabular Data Relations/Untitled 3.png]]

        A database relation (e.g. a database table) is said to meet third normal form standards if all the attributes (e.g. database columns) are functionally dependent on solely the primary key. Codd defined this as a relation in second normal form where all non-prime attributes depend only on the candidate keys and do not have a transitive dependency on another key.[1]

In some cases, there are software performance and time considerations which make the first and second levels of normal forms acceptable for what we're doing. Look at the scope and performance and decide how much normalization is necessary. Generally, more is better, but it's a compromise between organized data and time/memory usage.