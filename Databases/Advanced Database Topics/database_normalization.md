# Database Normalization

## What is Database Normalization?

**Normalization** is a database design technique that reduces data redundancy and eliminates undesirable characteristics like Insertion, Update and Deletion Anomalies. Normalization rules divides larger tables into smaller tables and links them using relationships. The purpose of Normalization in SQL is to eliminate redundant (repetitive) data and ensure data is stored logically.

## Types of Normal Forms in DBMS

Here is a list of Normal Forms in SQL:

- **1NF (First Normal Form):** Ensures that the database table is organized such that each column contains atomic (indivisible) values, and each record is unique. This eliminates repeating groups, thereby structuring data into tables and columns.
- **2NF (Second Normal Form):** Builds on 1NF by We need to remove redundant data from a table that is being applied to multiple rows. and placing them in separate tables. It requires all non-key attributes to be fully functional on the primary key.
- **3NF (Third Normal Form):** Extends 2NF by ensuring that all non-key attributes are not only fully functional on the primary key but also independent of each other. This eliminates transitive dependency.
- **BCNF (Boyce-Codd Normal Form):** A refinement of 3NF that addresses anomalies not handled by 3NF. It requires every determinant to be a candidate key, ensuring even stricter adherence to normalization rules.
- **4NF (Fourth Normal Form):** Addresses multi-valued dependencies. It ensures that there are no multiple independent multi-valued facts about an entity in a record.
- **5NF (Fifth Normal Form):** Also known as “Projection-Join Normal Form” (PJNF), It pertains to the reconstruction of information from smaller, differently arranged data pieces.
- **6NF (Sixth Normal Form):** Theoretical and not widely implemented. It deals with temporal data (handling changes over time) by further decomposing tables to eliminate all non-temporal redundancy.