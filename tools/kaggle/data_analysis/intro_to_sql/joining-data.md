# (6) Joining Data
https://www.kaggle.com/code/dansbecker/joining-data

## 1. Introduction
Sometimes the data you need is spread across multiple tables. **JOIN** allows you to combine these tables so you can work with all relevant information in one query. JOINs are essential in real-world SQL work.

## 2. Example
You have two tables:
- **pets**: `ID`, `Name`, `Animal`
- **owners**: `ID`, `Name`, `Pet_ID`

To figure out which owner belongs to which pet, you match `pets.ID` with `owners.Pet_ID`. For example, if both tables list a pet with ID 1, you know which owner corresponds to that pet.

## 3. Join
- **INNER JOIN** combines rows from two tables where the matched columns appear in *both* tables.
- The `ON` clause specifies which columns should be matched.
- It’s good practice to prefix columns with their table names (`p.ID`, `o.Pet_ID`) to avoid confusion.
- INNER JOIN is the most common JOIN type, returning only rows with matches on both sides.

## 4. How many files are covered by each type of software license?
- Using two GitHub dataset tables:
- **licenses**: Maps each repo to a license.
- **sample_files**: Lists files and the repos they belong to.

Query steps:
1. **JOIN** the two tables on `repo_name`.
2. **GROUP BY** license.
3. **COUNT(1)** to count how many files belong to each license.
4. **ORDER BY** the count in descending order.

Result: A table showing file counts per license (e.g., MIT, GPL-2.0, Apache-2.0), with MIT appearing most frequently.