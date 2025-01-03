# scenario_7.txt - Complex Member Analysis

CONTEXT:
Create detailed member activity profiles.

TASKS:

1. Calculate for each member:

   - Total books borrowed
   - genre of book borrowed
   - Average days to return
   - Number of current loans
     SAMPLE OUTPUT:
     | member_name | total_books_borrowed | favorite_genre | avg_days_to_return | current_loans |
     |-------------------|----------------------|----------------|--------------------|---------------|
     | John Doe | 5 | Fantasy | 10 | 1 |

2. Find members eligible for rewards:

   - Borrowed at least 5 books
   - No overdue books
   - Returns books on average within 14 days
     SAMPLE OUTPUT:
     | member_name | qualification_metrics |
     |-------------------|-----------------------|
     | John Doe | Eligible |

3. Generate member status report:
   - Active/Inactive status
   - last books borrowed
     SAMPLE OUTPUT:
     | member_name | detailed_status |
     |-------------------|----------------------------------|
     | John Doe | Active: Last book borrowed: Hobbit, Thrones |

SKILLS TESTED:

- Multiple joins
- Subqueries
- Complex filtering
- Multiple aggregations
- Conditional logic

TABLES NEEDED:

- **books**: Tasks 1, 2, 3.
- **members**: All tasks.
- **loans**: All tasks.
