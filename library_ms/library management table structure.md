-- books_table.txt
CREATE TABLE books (
book_id INT PRIMARY KEY AUTO_INCREMENT,
title VARCHAR(100) NOT NULL,
author VARCHAR(100) NOT NULL,
genre VARCHAR(50),
isbn VARCHAR(13) UNIQUE,
publication_year INT,
total_copies INT DEFAULT 1,
available_copies INT DEFAULT 1,
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- members_table.txt
CREATE TABLE members (
member_id INT PRIMARY KEY AUTO_INCREMENT,
first_name VARCHAR(50) NOT NULL,
last_name VARCHAR(50) NOT NULL,
email VARCHAR(100) UNIQUE NOT NULL,
phone VARCHAR(15),
join_date DATE DEFAULT (CURRENT_DATE),
membership_status ENUM('Active', 'Expired', 'Suspended') DEFAULT 'Active'
);

-- loans_table.txt
CREATE TABLE loans (
loan_id INT PRIMARY KEY AUTO_INCREMENT,
book_id INT,
member_id INT,
loan_date DATE DEFAULT (CURRENT_DATE),
due_date DATE,
return_date DATE,
status ENUM('Borrowed', 'Returned', 'Overdue') DEFAULT 'Borrowed',
FOREIGN KEY (book_id) REFERENCES books(book_id),
FOREIGN KEY (member_id) REFERENCES members(member_id)
);
