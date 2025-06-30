Bank Management System
Project Overview
This project is a robust, Python-based application designed to simulate core banking operations within a secure environment. It serves as a practical demonstration of fundamental software engineering principles, including database management, secure user authentication, role-based access control, and transaction processing. The system currently operates as a Command-Line Interface (CLI) application, making it a foundational backend system capable of managing user accounts and financial transactions.
Key Features
Secure User Authentication: Implements a robust registration and login system with password hashing, supporting both standard user accounts and administrative roles.
User Account Management: Allows users to create multiple bank accounts (e.g., savings, checking) and view their account details, including balances.
Financial Transaction Processing: Supports fundamental banking operations such as:
Deposits: Adding funds to a specified account.
Withdrawals: Removing funds from an account, with balance checks to prevent overdrafts.
Transfers: Facilitating secure money transfers between different bank accounts within the system.
Comprehensive Transaction History: Provides detailed logs for all account activities, including transaction type, amount, description, and timestamp.
Real-time Balance Updates: Ensures account balances are accurately and immediately reflected after each transaction.
Admin-Level Monitoring & Control: A dedicated administrator panel provides privileged functionalities:
Viewing a list of all registered users.
Toggling user account activation status (enabling/disabling user access).
Monitoring all bank accounts and their current balances across the system.
Accessing a complete audit log of all financial transactions within the bank.
Technologies Used
Core Language: Python 3.x
Database: SQLite (for development and local persistence, easily adaptable to PostgreSQL for production)
Object-Relational Mapper (ORM): SQLAlchemy
Chosen for its abstraction layer over raw SQL, allowing interaction with the database using Python objects, enhancing code readability, and providing database independence.
Password Hashing: bcrypt
Used for securely hashing user passwords, including automatic salting, to prevent plaintext storage and protect against common attacks like rainbow table lookups.
System Interaction: os and sys modules for command-line operations (e.g., clearing screen, exiting application).
Data Handling: Standard Python data structures and datetime for timestamps.
Architectural Highlights & Design Choices
Modular Architecture: The application is logically separated into distinct Python modules (database.py, auth.py, bank_operations.py, admin_operations.py, cli_app.py). This promotes code organization, reusability, and makes the system easier to debug and extend.
Layered Design:
Data Layer: SQLAlchemy models define the database schema and handle persistence.
Business Logic Layer: Functions for banking operations and authentication rules reside here.
Presentation Layer: The CLI handles user input and output.
Secure Password Management: A critical design choice was to never store plaintext passwords. bcrypt generates strong, unique hashes for each password, which are then stored in the database. Password verification involves hashing the entered password and comparing it to the stored hash.
Error Handling: Robust try-except blocks are implemented around database operations and user input to gracefully manage exceptions (e.g., SQLAlchemyError, ValueError) and provide informative feedback to the user.
Role-Based Access Control (RBAC): Differentiating between 'user' and 'admin' roles at the application level ensures that only authorized individuals can perform sensitive administrative tasks, enhancing system security.
Challenges and Solutions
Challenge: Managing Database Sessions: Ensuring proper session handling with SQLAlchemy (opening, committing/rolling back, and closing sessions for each operation) was crucial to prevent resource leaks and maintain data integrity, especially given Python's threading model.
Solution: Implemented a session factory (Session = sessionmaker(bind=engine)) and consistently managed sessions within try...finally blocks in each database interaction function, ensuring sessions are closed regardless of success or failure.
Challenge: Password Security: Storing and verifying passwords securely is paramount.
Solution: Integrated bcrypt for one-way password hashing with salting, a cryptographic best practice that protects against brute-force attacks and rainbow table attacks.

Future Enhancements
Graphical User Interface (GUI): Transitioning from CLI to a more user-friendly GUI (e.g., using Tkinter, PyQt, or a web framework like Flask/Django with a frontend) would enhance user experience.
External Database: Migrating from SQLite to a robust external database like PostgreSQL or MySQL for better scalability and concurrent access in a production environment.
Enhanced Security: Implementing features like two-factor authentication (2FA), rate limiting for login attempts, and detailed audit logging of administrative actions.
Advanced Features: Adding more complex banking features such as loan management, interest calculation, account statements, and notifications.
Transaction Limits & Fees: Incorporating business logic for transaction limits and various service fees.
Comprehensive Testing: Developing a suite of unit tests, integration tests, and end-to-end tests to ensure reliability and correctness.

