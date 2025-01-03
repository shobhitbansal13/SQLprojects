# scenario_6.txt - String Operations

CONTEXT:
Clean and format library records.

TASKS:

1. Format member names (First Last)
   SAMPLE OUTPUT:
   | member_id | formatted_name |
   |-----------|------------------|
   | 1 | John Doe |

2. Extract first word from book titles
   SAMPLE OUTPUT:
   | original_title | first_word |
   |------------------------------|------------|
   | The Hobbit | The |

3. Create email list of all members with full name
   SAMPLE OUTPUT:
   | formatted_name | email |
   |------------------|--------------------|
   | John Doe | johndoe@email.com |

4. Clean and standardize phone numbers
   SAMPLE OUTPUT:
   | member_name | formatted_phone |
   |-------------------|-----------------|
   | Alice Johnson | +91-9876543210 |

5. Generate loan receipt text
   SAMPLE OUTPUT:
   | formatted_loan_receipt |
   |-----------------------------------------------|
   | Loan Receipt: The Hobbit borrowed on 2024-12-01|

SKILLS TESTED:

- CONCAT
- SUBSTRING
- UPPER/LOWER
- TRIM
- String formatting

TABLES NEEDED:

- **books**: Tasks 2, 5.
- **members**: Tasks 1, 3, 4, 5.
- **loans**: Tasks 5.
