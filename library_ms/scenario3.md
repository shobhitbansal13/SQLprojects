# scenario_3.txt - Data Modification

CONTEXT:
Handle daily book and member record updates.

TASKS:

1. Add new book to library
   SAMPLE OUTPUT:
   A new book is added to the library database. Example:
   | book_id | title | author | genre | publication_year | total_copies | available_copies |
   |---------|-----------------------|----------------|--------|------------------|--------------|------------------|
   | 9 | The Catcher in the Rye| J.D. Salinger | Classic| 1951 | 4 | 4 |

2. Update member's contact information for james wilson
   SAMPLE OUTPUT:
   The updated member record with new contact information is saved. Example:
   | member_id | name | contact |
   |-----------|-----------------|--------------|
   | 1 | John Doe | 9876543210 |

3. Mark a book as lost (remove copies)
   SAMPLE OUTPUT:
   The total and available copies of the lost book are decreased. Example:
   | book_id | title | total_copies | available_copies |
   |---------|---------------------------|--------------|------------------|
   | 1 | The Hobbit | 2 | 1 |

4. Register new library member
   SAMPLE OUTPUT:
   A new member is added to the database. Example:
   | member_id | name | join_date |
   |-----------|-----------------|------------|
   | 5 | Alice Johnson | 2024-12-30 |

5. Modify book genre categorization for '1984' to thriller
   SAMPLE OUTPUT:
   The book's genre is updated in the database. Example:
   | book_id | title | old_genre | new_genre |
   |---------|----------------------|-----------|-----------|
   | 6 | A Game of Thrones | Fantasy | Epic |

SKILLS TESTED:

- INSERT INTO
- UPDATE
- DELETE
- Transaction handling
- Data modification constraints

TABLES NEEDED:

- **books**: Tasks 1, 3, 5.
- **members**: Tasks 2, 4.
