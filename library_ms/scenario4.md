# scenario_4.txt - Member and Book Relations

CONTEXT:
Track relationships between members,books and loans

TASKS:

1. Show all loans for Robert thomas
   SAMPLE OUTPUT:
   | book_title | loan_date | due_date | status |
   |-----------------------------|------------|-----------|----------|
   | The Hobbit | 2024-12-01 | 2024-12-15| Returned |
   | Harry Potter and the Sorcerer's Stone | 2024-12-05 | 2024-12-19| Overdue |

2. List members with no loans
   SAMPLE OUTPUT:
   | member_name | loan_status |
   |-------------------|------------|
   | Alice Johnson | 2024-12-30 |

3. Find members who borrowed specific genre i.e Fantasy
   SAMPLE OUTPUT:
   | member_name |   genre |
   |-------------------|------------|------------------|
   | John Doe | fantasy

4. Show books never borrowed
   SAMPLE OUTPUT:
   | title | author | status |
   |---------------------------|--------------------|------------------|
   | The Catcher in the Rye | J.D. Salinger | NULL |

5. List all overdue books with borrower details
   SAMPLE OUTPUT:
   | book_title | member_name | days_overdue |
   |---------------------------|-------------------|--------------|
   | Harry Potter and the Sorcerer's Stone | John Doe | 10 |

SKILLS TESTED:

- INNER JOIN
- LEFT/RIGHT JOIN
- Multiple table joins
- NULL handling
- Relationship mapping

TABLES NEEDED:

- **books**: Tasks 1, 4, 5.
- **members**: Tasks 2, 3, 5.
- **loans**: Tasks 1, 3, 5.
