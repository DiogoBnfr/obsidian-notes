# Definition
---
A database is a structured collection of data organized and stored in a systematic manner. It is designed to efficiently manage, retrieve, and manipulate large amounts of information.

# Database Management Systems
---
A Database Management System (DBMS) is software that enables the creation, organization, management, and retrieval of data in a database. It serves as an interface between the database itself and the end users or applications that interact with the data. The DBMS provides a set of tools and functionalities to handle the storage, manipulation, and retrieval of data efficiently and securely.

## Relational Databases
---
Relational databases are based on the relational model, which organizes data into tables consisting of rows and columns. These tables are related to each other through key-based relationships. The relational model provides a structured and organized way to store and manage data, ensuring data integrity and consistency. Relational databases use Structured Query Language (SQL) for data manipulation and retrieval. The relational model allows for complex queries, supports ACID (Atomicity, Consistency, Isolation, Durability) properties, and provides a clear and defined schema.

## Non-Relational Databases
---
Non-relational databases, commonly referred to as NoSQL databases, are designed to handle vast amounts of unstructured, semi-structured, and varying data types. They deviate from the rigid structure and relational nature of traditional databases and provide flexible data models that can adapt to evolving data requirements. NoSQL databases can be categorized into various types, including:

1. **Key-Value Stores:** These databases store data as key-value pairs, where each value is associated with a unique key. 
3. **Document Databases:** Document databases store and retrieve data in flexible, self-descriptive documents, such as JSON or XML. 
4. **Columnar Databases:** These databases organize data into columns rather than rows, making them efficient for analytical workloads. 
5. **Graph Databases:** Graph databases store and represent data as nodes, edges, and properties, making them suitable for complex relationships and network analysis. 

# Database Design
---
Database design refers to the process of creating a well-structured and efficient database schema that meets the requirements of an application or system. It involves identifying the entities, relationships, and attributes of the data that need to be stored and designing a logical and physical structure for organizing and accessing the data effectively.

1. **Conceptual Schema:** Create a high-level conceptual model of the database, often represented using entity-relationship (ER) diagrams. Identify the entities, their attributes, and the relationships between them.
2. **Logical Schema:** Translate the conceptual model into a logical model that represents the database structure in a more detailed and implementable way. This involves determining the tables, columns, primary keys, foreign keys, and constraints based on the conceptual model. Normalization techniques are applied to eliminate data redundancy and improve data integrity.
3. **Physical Schema:** Map the logical model to a physical implementation by selecting a specific database management system (DBMS) and defining the storage structures, file organizations, and indexing mechanisms. Considerations include partitioning, data distribution, and access control mechanisms.

## Data Integrity
---

## Atomic Values
---

## Relationships
---

## Keys & Classifications
---
Keys are columns with unique values (most of the times), that are used to identify one specific entity in databases. They are values (they can be one single value or a group of them) which all other values in a row points to.

### Candidate Key
---
Candidate keys are a set of minimal attributes (columns) within a relational database table that can uniquely identify each tuple (row) in the table. A candidate key has two main characteristics:

1. **Uniqueness:** Each candidate key value combination must uniquely identify a tuple in the table. This means that no two tuples can have the same combination of values for the candidate key attributes.
2. **Minimalism:** A candidate key must be minimal, meaning that no subset of the candidate key can uniquely identify a tuple. If any attribute is removed from the candidate key, it should no longer be able to guarantee unique identification.

### Super Key
---
Superkeys are sets of attributes (columns) within a relational database table that can uniquely identify tuples (rows) in the table. A superkey possesses the following characteristics:

1. **Uniqueness:** Each superkey value combination must uniquely identify a tuple in the table. This means that no two tuples can have the same combination of values for the superkey attributes.
2. **Redundancy:** Unlike candidate keys, superkeys can contain additional attributes that are not strictly necessary for unique identification. These extra attributes may be present within the superkey but do not contribute to the uniqueness property.
3. **Superset:** A superkey can encompass one or more candidate keys within its set of attributes. It may include all the attributes of a candidate key or have additional attributes along with the candidate key attributes.

### Primary Key
---
Primary keys are selected candidate keys within a relational database table that uniquely identify each tuple (row) in the table. A primary key possesses the following characteristics:

1. **Uniqueness:** Each primary key value must uniquely identify a tuple in the table. This means that no two tuples can have the same value for the primary key attribute(s).
2. **Minimalism:** A primary key is a minimal candidate key, meaning that no subset of the primary key attributes can uniquely identify a tuple. If any attribute is removed from the primary key, it should no longer guarantee unique identification.
3. **Selected Identifier:** Among the candidate keys, one is chosen as the primary key. This selection is based on factors such as stability, simplicity, and applicability to the data model. The primary key becomes the main identifier for each tuple in the table.

	*Always unique. Never change. Never be null.* 

In general, if a key contain this three characteristics, it will be a good and stable key that comply with it's function of maintaining the integrity of your database.

### Alternate Key
---
Alternate keys are candidate keys within a relational database table that are not selected as the primary key. An alternate key possesses the following characteristics:

1. **Uniqueness:** Each alternate key value combination must uniquely identify a tuple in the table. This means that no two tuples can have the same combination of values for the alternate key attributes.
2. **Minimalism:** Similar to the primary key, an alternate key is a minimal candidate key. It means that no subset of the alternate key attributes can uniquely identify a tuple. Removing any attribute from the alternate key would result in a loss of unique identification.
3. **Non-Primary Identifier:** While the primary key is chosen as the main identifier for the table, alternate keys provide additional options for unique identification. Although not selected as the primary key, they still have the property of uniquely identifying tuples in the table.

### Natural Key
Is a primary key that is naturally in your database. A value who has real-world meaning and that you want to be stored. The primary function of this value is not to be a key, to create relationships between tables or anything else. Is simply to store specific values but adapted to help in the database integrity and relations.

### Surrogate Key 
Surrogate keys in the other side are values who you don't naturally want to store in your database. They are created with the only purpose of work as an support to your database organization, integrity and etc.

### Simple Key
A single-column key, simple key, is a key that consists of a single column in a table and is used to uniquely identify each record.

### Composite Key
A composite key refers to a combination of two or more columns that uniquely identify a record in a table.

### Compound Key
Is a combination of two keys. Normally used in intermediary tables to create uniqueness in the rows.

# Bibliography
---
- https://youtu.be/ztHopE5Wnpc