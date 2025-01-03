# SCENARIO 1: Basic Data Retrieval

File: scenario_1.txt

CONTEXT:
You're working the front desk at the library and need to help patrons with basic book queries.

SAMPLE DATA (Relevant subset of books table):

```
book_id | title                    | author           | genre     | publication_year | total_copies | available_copies
1       | The Hobbit              | J.R.R. Tolkien   | Fantasy   | 1937            | 3            | 2
2       | The Lord of the Rings   | J.R.R. Tolkien   | Fantasy   | 1954            | 3            | 2
3       | The Great Gatsby        | F. Scott Fitzgerald| Classic  | 1925            | 3            | 2
4       | The Catcher in the Rye  | J.D. Salinger    | Fiction   | 1951            | 2            | 1
5       | Harry Potter            | J.K. Rowling     | Fantasy   | 1997            | 4            | 3
```

TASKS:

1. Find all books by J.R.R. Tolkien
   SAMPLE OUTPUT:

   ```
   title                    | author         | publication_year | available_copies
   The Hobbit              | J.R.R. Tolkien | 1937            | 2
   The Lord of the Rings   | J.R.R. Tolkien | 1954            | 2
   ```

2. List all Fantasy genre books with more than 2 copies available
   SAMPLE OUTPUT:

   ```
   title                    | author         | total_copies | available_copies
   Harry Potter            | J.K. Rowling   | 4            | 3
   ```

3. Show books published between 1950 and 2000
   SAMPLE OUTPUT:

   ```
   title                    | author         | publication_year
   The Lord of the Rings   | J.R.R. Tolkien | 1954
   The Catcher in the Rye  | J.D. Salinger  | 1951
   Harry Potter            | J.K. Rowling   | 1997
   ```

4. Find books containing word 'The' ordered by publication year
   SAMPLE OUTPUT:

   ```
   title                    | author              | publication_year
   The Great Gatsby        | F. Scott Fitzgerald | 1925
   The Hobbit              | J.R.R. Tolkien     | 1937
   The Catcher in the Rye  | J.D. Salinger      | 1951
   The Lord of the Rings   | J.R.R. Tolkien     | 1954
   ```

5. List all books sorted by title (A-Z)
   SAMPLE OUTPUT:
   ```
   title                    | author              | genre
   Harry Potter            | J.K. Rowling       | Fantasy
   The Catcher in the Rye  | J.D. Salinger      | Fiction
   The Great Gatsby        | F. Scott Fitzgerald | Classic
   The Hobbit              | J.R.R. Tolkien     | Fantasy
   The Lord of the Rings   | J.R.R. Tolkien     | Fantasy
   ```

SKILLS TESTED:

- SELECT, WHERE, AND/OR
- ORDER BY (ASC/DESC)
- Comparison operators (<, >, =)
- LIKE operator
- Basic filtering
- String matching
- Sorting

TABLES NEEDED:

- books
