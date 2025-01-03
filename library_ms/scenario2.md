# scenario_2.txt - Aggregate Functions

CONTEXT:
The library manager needs statistical information about the book collection.

TASKS:

1. Count total books per genre
   SAMPLE OUTPUT:
   | genre | book_count | total_copies |
   |-----------|------------|--------------|
   | Fantasy | 6 | 35 |
   | Dystopian | 1 | 3 |
   | Classic | 1 | 2 |

2. Find average publication year for each genre
   SAMPLE OUTPUT:
   | genre | avg_year | 
   |-----------|----------|-------------|-------------|
   | Fantasy | 1959 | 
   | Dystopian | 1949 | 
   | Classic | 1925 | 

3. Calculate total and available copies per author
   SAMPLE OUTPUT:
   | author | total_books | total_copies | available_copies |
   |--------------------|-------------|--------------|------------------|
   | J.R.R. Tolkien | 4 | 18 | 10 |
   | J.K. Rowling | 1 | 10 | 8 |
   | George R.R. Martin | 1 | 7 | 5 |
   | George Orwell | 1 | 3 | 3 |
   | F. Scott Fitzgerald| 1 | 2 | 1 |

4. Show genres with more than 3 books
   SAMPLE OUTPUT:
   | genre | book_count |
   |---------|------------|
   | Fantasy | 6 |

5. Find authors with most books in the library
   SAMPLE OUTPUT:
   | author | book_count | total_copies |
   |--------------------|------------|--------------|
   | J.R.R. Tolkien | 4 | 18 |

SKILLS TESTED:

- COUNT, SUM, AVG
- GROUP BY
- HAVING
- MIN, MAX
- Arithmetic operations

TABLES NEEDED:

- **books**: Required for all tasks in this scenario.
