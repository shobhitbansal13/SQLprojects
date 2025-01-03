# scenario_5.txt - Date Operations

CONTEXT:
Analyze time-based patterns in library operations.

TASKS:

1. Calculate loan duration for all returned books
   SAMPLE OUTPUT:
   | book_title | borrow_date | return_date | days_borrowed |
   |-----------------------------|-------------|-------------|---------------|
   | The Hobbit | 2024-12-01 | 2024-12-10 | 9 |
   | A Game of Thrones | 2024-12-02 | 2024-12-15 | 13 |

2. Find all loans made in february
   SAMPLE OUTPUT:
   | book_title | member_name | loan_date |
   |-----------------------------|-------------------|------------|
   | The Hobbit | John Doe | 2024-11-20 |

3. Show members who joined in february and days since joined
   SAMPLE OUTPUT:
   | member_name | join_date | days_since_joined |
   |-------------------|------------|-------------------|
   | Alice Johnson | 2024-12-30 | 0 |

4. List overdue books and days overdue
   SAMPLE OUTPUT:
   | book_title | member_name | due_date | days_overdue |
   |-----------------------------|-------------------|------------|--------------|
   | Harry Potter and the Sorcerer's Stone | John Doe | 2024-12-19| 10 |

5. Calculate average loan duration by genre
   SAMPLE OUTPUT:
   | genre | avg_days_borrowed |
   |-------------|-------------------|
   | Fantasy | 11 |
   | Dystopian | 8 |

SKILLS TESTED:

- DATE functions
- DATEDIFF
- DATE_FORMAT
- Date comparisons
- Date arithmetic

TABLES NEEDED:

- **books**: Tasks 1, 4, 5.
- **members**: Tasks 2, 3, 4.
- **loans**: All tasks.
