# Geospatial Data

Created: Jan 14, 2021 8:10 PM
Last Edited: Mar 8, 2021 3:05 PM
Tags: 181A
UID: 202101142010

# Representation

How do we represent the world?

### The Geographical Matrix

![[Field Knowledge/GIS/GIS Data/Geospatial Data/Untitled.png]]

Vertical axis: Domains of Synthesis. Ask questions regarding different dynamics between the environment and human society

Horizontal axis: Geography's ways of looking at the world. Look at integrations in place, or across scales

Z Axis: Spatial representation. 5 different ways in which we can describe these two axes of information

### The Geospatial Data Cube

![[Field Knowledge/GIS/GIS Data/Geospatial Data/Untitled 1.png]]

Axes: Locations, Occasions, and Attributes

occations = time, locations = place, attributes = quality

geospatial data varies across space and time, so it's difficult to represent!

## Representing the Spatial Dimension

### Object based Models

- object populate space
- defined with discrete, identifiable boundaries
- clear spatial extent
- described by traits, attributes

Vector model! of points/lines/polygons

### Field based models

- phenomena **fill** space - they almost *are* the space
- no definite boundary, continuous area

Raster model!

Spatial relations: how phenomena and objects are connected, associated, or linked together in space

Temporal relations: how phenomena and objects are connected, associated, or linked together in time

Language for spatial relationships:

- near
- neighboring
- from
- to
- intersects
- joins
- within
- nested
- outside
- contains
- overlaps
- many, many more

## Temporal attributes

language for temporal attributes

- start, origination
- duration
- end
- signifigance
- temporal scale:
    - expressed in terms of *map time : real time*

Space-time: the continuum of SPACE and TIME interconnected!!

# Utilizing geospatial data

**encoding** - the process by which data becomes usable by computers

**organization** - a principle which permits the efficient use of data

- logical organization: establishes methods for the classification and feature coding of data in order to establish relationships between items
- physical organization: how data are stored in memory

Classification schemes are important as well! Logical organization provides *a priori* standards for us

- **Descriptive Names** of classes/subclasses, based on form and function
- **Definitions** of each class and subclass

The empire state building is a 'high-rise structure' in form, but 'commercial' in function.

Guidelines for classification:

- mutually exclusive
- re-usable to other items
- easily understood
- returns replicable and applicable results
- heirarchical!
- sensitive to scale
- stable over time
- flexible, modifiable
- quantitative

# Geospatial data feature codes and coding

**Entity**: a spatial object with specific objects, distinct from other entities

**Entity Class, Entity Type, Feature Class:** Entities that share common properties

- ex, "interstate highways", "states", "lakes", etc

![[Field Knowledge/GIS/GIS Data/Geospatial Data/Untitled 2.png]]

Each type of entity is assigned a unique NUMBER! This is used to encode land use instructions

Subclasses have their own numbers as well. To specify a specific type, start at the most general and work your way down the tree, appending to the string

- residential code: 120
- crop code: 100
- etc.

# Data Models

Three levels of abstraction, resulting in an actually implemented data model:

1. **Conceptual Model**
- general definitions of the model
- traits of entities to include

2. **Logical Model**

- Framework
- definitions and measures
- database type (relational DB, hierarchical DB, etc.)

3. **Physical Model**

- Hardware dependent
- the actual implementation of the database!

## Database Management Systems (DBMS)

These systems have benefits:

- reduces redundancy (data sharing)
- Single Data Collection and Input Process minimizes inconsistencies
- Data sharing, concurrent access
- establish standards
- increased accessibility to everyone
- data security, application security
- data integrity

Speficic benefits to **Geospatial DBMS**

- Transaction management
- Spatial Data Indexing
- Spatial Data integration
- Spatial relations encode topology
- Spatial operations allow for intersection, join, overlay, etc.