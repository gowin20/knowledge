# Database Management

Created: Sep 2, 2020 3:02 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 7
Topic: [[Data Structures in GIS]]
UID: 202009021502

### Date: Aug 16, 2020

### Topic: Database Management

### Recall

### Relational Database Management System (RDBMS)

- a collection of tables which are connected so that all data can be accessed WITHOUT REORGANIZATION
- Each column is a specific attribute (Name, PIN number, Last Name, Blood Type)
- Each row is a unique instance of data for each attribute (George, 2018, Owen, A-)
- Each table is linked to other tables via keys
    - Primary key - the attribute column whose value UNIQUELY IDENTIFIES A SPECIFIC ROW
        - maybe each name is unique, or simply each entry has a unique identifying hash
        - every entry must contain a primary key - no empty values here!
    - Foreign key
        - Each primary key directly corresponds to a foreign key in another table
        - Each table must contain an attribute that corresponds to an attribute in every other related table
        - This relation between primary and foreign keys is why we call it a "Relational" DBMS
- Advantages:
    - Each table is discrete, can be edited and maintained separately
    - Tables can vibe separately until they need to be related together
    - ^ means they're EFFICIENT!
- Disadvantages: Lots of REDUNDANCY! (could be good but is usually bad)
    - Each table must contain an attribute that corresponds to an attribute in every other related table
    - have to actively monitor this to keep it down
    - To keep redundancy down, we have lots of norms
- The Three Normal Forms of RDBMS:

    First Normal Form has five conditions: (Codd's rules for efficient Database design)

    - No Sequence to the ordering of rows
    - No Sequence to the ordering of columns
    - Each row is unique
    - Each cell has one value
    - All values in a column pertain to the same attribute

        ![[Database Management/Untitled.png]]

        first normal form

    Second Normal Form:

    - Any column that is not a primary key must be DEPENDENT on the primary key
    - eliminate table dependencies that are not related to the key fields
    - Prevents the possibility of multiple primary keys

        ![[Database Management/Untitled 1.png]]

        ^ department name depends on department num, which is not the primary key of the table. Employee num is

    Third Normal Form

    - All nonprimary keys must depend on the primary key, while the primary key remains independent of all nonprimary keys
    - "all nonprimary keys must provide a fact about the key, the whole key, and nothing but the key."

        ![[Database Management/Untitled 2.png]]

### Joins and Relates

Join Operation

- Appends the fields of one table into a second table
- Uses an attribute / field that both tables have
- Used to combine attribute data and geospatial data/GIS features
- Suitable for **one-to-one** or **one-to-many**
    - Building to address : one-to-one
    - State to counties : one-to-many

Relate Operation

- Temporarily associated two map layers / tables while keeping them physically separate
- Bidirectional
- Allows association of many tables at once
- Suitable for **one-to-one, one-to-many, many-to-one, and many-to-many** (all of them)
    - cities to states : many-to-one

### Queries

Attribute Query

- Find something according to tabular attribute data

Spatial Query

- Find something according to spatial data or GIS layer data

SQL Query

- Find something, but phrased in SQL (Structured Query Language)

 **SUMMARY:**