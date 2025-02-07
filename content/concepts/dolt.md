---
title: Why Dolt?
---

# Why Dolt?

Dolt brings the features of Git-style distributed version control to the SQL database.

Git-style Distributed Version Control allowed the world to collaborate on open source software in a beautiful way. Dolt aspires to bring that distributed collaboration model to data.

SQL is the worldwide standard for data description and querying. SQL has been popular for 50 years. By combining schema and data, SQL gives data a powerful language for data practitioners to communicate with. 

Before Dolt, to share a SQL database with a fellow data practitioner, you both needed to share the same view of the data. Only one write could happen at a time. Making a copy implied creating a point in time backup and restoring on a separate running server. Once that copy was made, the two databases could change independently. There was no tractable way to compare the two copies of the database to see what changed. Moreover, there was no easy way to merge the two copies back together. In source code parlance, the copy was a hard fork of the database.

The inability to copy and merge forced databases into a specific model of usage. Data was hard to move and share. As an industry, we built complicated pipelines to move and transform data between databases. We built APIs to allow programmatic, controlled access to data. 

Here at DoltHub, we looked at all these systems and thought there must be a better way. What if you could copy a database, make changes, compare the database to any other copy, and merge the changes whenever you wanted? What if thousands of people could do this at the same time? What if you could use Git workflows on databases? 

A database with these properties would allow thousands of users to read and write at the same time. If someone made a mistake, no big deal, just roll back the change. Need a copy of the data to run a metrics job on? No problem, just make a clone. Bug in production? Create a copy of the database on your laptop, start your services, change the production data to speed debugging. Want to open your data up to the world? Push it up to a remote that's accessible via the internet.

## Concepts

In order to achieve the above mission, Dolt needed to implement Git concepts in a SQL database. As best we could, we tried to keep things as similar as possible.

We built Dolt using the following axioms:

1. Git versions files. Dolt versions table schema and table data.
2. Dolt will copy the Git command line exactly.
3. Dolt will be MySQL compatible.
4. Git features in SQL will extend MySQL SQL. Write operations will be procedures. Read operations will be system tables.

In order to achieve the above at scale, we needed to start at the bottom; the storage engine of the database. Dolt is built from the storage engine up to offer you the Git experience in a SQL database.  

In this section of the documentation, we will explain [Git](./dolt/git/README.md), [SQL](./dolt/sql/README.md), and [Relational Database Management System (RDBMS)](./dolt/rdbms/README.md) concepts and how we applied them in Dolt using the above axioms.
