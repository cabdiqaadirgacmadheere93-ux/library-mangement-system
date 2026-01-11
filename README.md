# Library Management System

A comprehensive web-based application designed to manage university library operations. This system handles book inventory, member management, book issuing/returning cycles, fine calculation, and reporting.

## Features

### 📚 Book Management
- **Cataloging**: Add, update, and organize books by category.
- **Inventory**: Track total and available copies of books.
- **Categories**: Organize books into categories (e.g., History, Computer Science, Literature).

### 👥 User Management
- **Role-Based Access**:
  - **Admin**: Full system access, manageable settings, and user oversight.
  - **Librarian**: Manage books, issues, and returns.
  - **Member**: View profile, check book availability (frontend features).
- **Authentication**: Secure login, password reset, and profile management.

### 🔄 Circulation (Issues & Returns)
- **Issue Books**: Assign books to members with due dates.
- **Return Books**: Process returns and automatically calculate status.
- **Tracking**: Monitor active loans, overdue books, and history.

### 💰 Fine System
- **Automatic Calculation**: Fines are generated for late returns.
- **Payment Tracking**: Record fine payments.

### 📊 Reporting
- **Dashboards**: Visual overview of library statistics.
- **Reports**: Generate detailed reports on book status, member activity, and financial summaries.

## Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla).
- **Backend**: PHP 7.4+ (PDO).
- **Database**: MySQL / MariaDB.
- **Server**: Apache (via XAMPP/WAMP/LAMP).

## Installation

1. **Clone the Repository**
   Copy the project files to your web server's root directory (e.g., `C:\xampp\htdocs\library-system`).

2. **Database Setup**
   - Open your MySQL management tool (e.g., phpMyAdmin).
   - Create a new database named `library_system`.
   - Import the `database.sql` file located in the root directory into your new database.
   
   *Tip: This will create the necessary tables (users, books, roles, etc.) and insert initial seed data.*

3. **Configuration**
   - Navigate to `config/config.php`.
   - Update the database credentials if strictly necessary (default checks for `DB_HOST`, `DB_USER`, etc., usually configured for standard XAMPP environments).

4. **Run the Application**
   - Open your browser and visit: `http://localhost/library-system/public`
   - Default Login (if using seed data):
     - **Email**: (Admin/Librarian email from database)
     - **Password**: `123456` (Note: Ensure password hashes in the database match your hash mechanism).

## Project Structure

```
library-system/
├── config/             # Database connection and configuration
├── includes/           # Shared UI components (header, sidebar, footer)
├── public/             # Main application pages
│   ├── books.php       # Book management
│   ├── dashboard.php   # Admin dashboard
│   ├── issues.php      # Circulation management
│   ├── users.php       # Member management
│   └── ...
├── database.sql        # Database schema import file
└── README.md           # Project documentation
```

## License

This project is open-source and available for educational and private use.
## Group Names

* Abdulkadir Omar Hassan — C1220674
* Mohamed Abdow Omar — C1210964
* Yahye Said Abdirahman — C1220673
* Fadumo Ali Warsame — C1221190
