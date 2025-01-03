-- books_data.txt
INSERT INTO books (title, author, genre, isbn, publication_year, total_copies, available_copies) VALUES
('The Great Gatsby', 'F. Scott Fitzgerald', 'Classic', '9780743273565', 1925, 3, 2),
('To Kill a Mockingbird', 'Harper Lee', 'Fiction', '9780446310789', 1960, 4, 3),
('1984', 'George Orwell', 'Science Fiction', '9780451524935', 1949, 3, 1),
('Pride and Prejudice', 'Jane Austen', 'Romance', '9780141439518', 1813, 2, 2),
('The Hobbit', 'J.R.R. Tolkien', 'Fantasy', '9780547928227', 1937, 3, 2),
-- ... [previous book entries continue]

-- members_data.txt
INSERT INTO members (first_name, last_name, email, phone, join_date) VALUES
('John', 'Smith', 'john.smith@email.com', '555-0101', '2023-01-15'),
('Emma', 'Johnson', 'emma.j@email.com', '555-0102', '2023-02-20'),
('Michael', 'Brown', 'michael.b@email.com', '555-0103', '2023-03-10'),
('Sarah', 'Davis', 'sarah.d@email.com', '555-0104', '2023-04-05'),
('James', 'Wilson', 'james.w@email.com', '555-0105', '2023-05-12'),
-- ... [previous member entries continue]

-- loans_data.txt
INSERT INTO loans (book_id, member_id, loan_date, due_date, return_date, status) VALUES
(1, 1, '2024-03-01', '2024-03-15', '2024-03-14', 'Returned'),
(2, 3, '2024-03-05', '2024-03-19', NULL, 'Borrowed'),
(3, 5, '2024-03-10', '2024-03-24', NULL, 'Borrowed'),
(4, 2, '2024-02-28', '2024-03-13', '2024-03-16', 'Returned'),
(5, 4, '2024-03-15', '2024-03-29', NULL, 'Borrowed'),
-- ... [previous loan entries continue]
