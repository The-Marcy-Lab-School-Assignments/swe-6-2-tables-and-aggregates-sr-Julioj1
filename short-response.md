# Short Response: Creating Tables and Aggregates

Answer each question below. Write in complete sentences (3–5 per answer).

## Question 1

What is a data type? Why does it matter what type you assign to a column? Give an example of what could go wrong if you used the wrong type.

**Your answer:**

A data type is an attribute assigned to a database column that tells the system how to interpret, store, and manipulate the information it holds. It acts as a set of rules that defines what specific kind of values are allowed and what operations can be performed on them.

Assigning the correct data type is critical because it directly impacts:

- **Data Integrity**: It acts as a primary constraint, preventing invalid information from entering the system.
- **Performance**: Databases process queries faster when data is "right-sized"; for example, small numeric types use less memory and disk than generic text types.
- **Storage Efficiency**: Choosing the smallest appropriate type can save massive amounts of disk space as a dataset scales.

## Question 2

What is a constraint? Name two constraints and explain what each one enforces.

**Your answer:**

A **constraint** is a rule applied to data in a database table or a system that restricts the type of data that can be inserted, updated, or deleted.

1. `NOT NULL` Constraint
   **What it enforces**: It prevents a column from having a `NULL` (empty) value.
   **Purpose**: Ensures that a column always contains data, which is **essential** for fields requiring identification (like a username) or for calculations where an empty value would cause errors.
   **Example**: Defining `Email VARCHAR(255) NOT NULL` ensures every row has an email address.

2. `UNIQUE` Constraint
   **What it enforces**: It ensures that all values in a column or a set of columns are distinct from one another across all rows in a table.
   **Purpose**: Prevents duplicate entries in columns that should be **distinct**, such as usernames, email addresses, or tax identification numbers.
   **Example**: Defining `Username VARCHAR(50) UNIQUE` ensures that no two users can have the same username.

## Question 3

What is the difference between `WHERE` and `HAVING`? Can you use both in the same query? If so, what does each one do?

**Your answer:**

Yes, you can use both `WHERE` and `HAVING` in the same SQL query. They are used for different stages of data filtering:

`WHERE` filters individual rows before they are grouped or aggregated.
`HAVING` filters summarized groups after the aggregation has been performed.

## Question 4

What is a seed file? Why is seeding important when working on a team?

**Your answer:**

A **seed file** is a script or data file used to pre-populate a database with initial, structured, or sample data. It provides a foundational dataset such as lookup tables, default roles, or sample user profiles, needed for an application to function properly during development or testing.

**Seeding** is important when working on a team because it ensures that all team members work with the same data environment, reduces onboarding time, and facilitates consistent testing.

Seed files allow all developers to **populate** their local databases with identical data, ensuring that code works locally, in staging, and in production. New team members can run a single command to set up a usable development database instantly, rather than manually entering data.

Developers can use seed data to validate logic for new features without waiting for a full production data refresh.

## Question 5

You have a table called `orders` with a `customer_name` column and a `total` column. Write a SQL query that shows each customer's total spending, but only includes customers who have spent more than $100 in total.

```sql
SELECT customer_name, SUM(total) AS total_spending
FROM orders
GROUP BY customer_name
HAVING SUM(total) > 100;
```
