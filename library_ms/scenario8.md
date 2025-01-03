# scenario_8.txt - Library Performance Metrics

CONTEXT:
Analyze overall library performance.

TASKS:

1. Calculate daily loan statistics from 1st feb to 1st May 2024

   - Books checked out
   - Books returned
   - New members
   - Active loans
     SAMPLE OUTPUT:
     | date | books_checked_out | books_returned | new_members | active_loans |
     |-------------|-------------------|----------------|-------------|--------------|
     | 2024-12-30 | 5 | 3 | 2 | 7 |



2. Create book efficiency report:
   - Times borrowed
   - Average days between borrow and return
   - Currently available
   - Demand rating
     SAMPLE OUTPUT:
     | book_title | efficiency_metrics |
     |---------------------------|--------------------|
     | Harry Potter | High Demand |

SKILLS TESTED:

- Complex aggregations
- Multiple table operations
- Date grouping
- Statistical calculations
- Performance metrics

TABLES NEEDED:

- **books**: 
- **members**: 
- **loans**: 
