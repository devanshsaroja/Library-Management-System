# Library Management System using SQL Project --P2

## Project Overview

**Project Title**: Library Management System  
**Database**: `library_db`

This project demonstrates the implementation of a Library Management System using SQL. It includes creating and managing tables, performing CRUD operations, and executing advanced SQL queries. The goal is to showcase skills in database design, manipulation, and querying.


![Library Management System](https://www.skoolbeep.com/blog/wp-content/uploads/2020/12/WHAT-IS-THE-PURPOSE-OF-A-LIBRARY-MANAGEMENT-SYSTEM-min.png)

## Objectives

1. **Set up the Library Management System Database**: Create and populate the database with tables for branches, employees, members, books, issued status, and return status.
2. **CRUD Operations**: Perform Create, Read, Update, and Delete operations on the data.
3. **CTAS (Create Table As Select)**: Utilize CTAS to create new tables based on query results.
4. **Advanced SQL Queries**: Develop complex queries to analyze and retrieve specific data.

## Project Structure

### 1. Database Setup
![ERD](https://github.com/najirh/Library-System-Management---P2/blob/main/library_erd.png)

- **Database Creation**: Created a database named `library_db`.
- **Table Creation**: Created tables for branches, employees, members, books, issued status, and return status. Each table includes relevant columns and relationships.

### 2. CRUD Operations

- **Create**: Inserted sample records into the `books` table.
- **Read**: Retrieved and displayed data from various tables.
- **Update**: Updated records in the `employees` table.
- **Delete**: Removed records from the `members` table as needed.


## 3. Key Functionalities & Business Logic

### 📊 Data Analysis Reports
- Most and least issued books.
- Employees with highest issue/return counts.
- Branch-wise issue statistics.

### 🧠 Advanced SQL
- **Joins**: Multiple INNER and LEFT joins to correlate data across tables.
- **Aggregations**: COUNT, AVG, MAX, MIN, and GROUP BY for analytics.
- **CTAS (Create Table As Select)**: For generating dynamic reporting tables.
- **Stored Procedure**: Handles return logic and calculates late fines automatically.
  ```sql
   CREATE OR REPLACE PROCEDURE add_return_records (
        p_issued_id INT,
        p_return_date DATE,
        p_fine NUMERIC
    ) AS $$
    BEGIN
        IF EXISTS (SELECT 1 FROM return_status WHERE issued_id = p_issued_id) THEN
            RAISE NOTICE 'Return already logged for issued_id: %', p_issued_id;
            RETURN;
        END IF;
    
        INSERT INTO return_status (issued_id, return_date, fine)
        VALUES (p_issued_id, p_return_date, p_fine);
    END;
    $$ LANGUAGE plpgsql;
    '''

## 🧠 Skills Demonstrated

| Category             | Tools/Concepts Used                                      |
|----------------------|----------------------------------------------------------|
| Database Design      | Normalization, Primary/Foreign Keys, ERD                |
| Query Language       | SQL (PostgreSQL syntax), Joins, Group By, CTAS         |
| Procedural Logic     | Stored Procedures with Parameters                       |
| Reporting & Insights | Aggregation, Sorting, Grouped Reports                   |
| Optimization         | Efficient joins and subqueries                          |

## Reports

- **Database Schema**: Detailed table structures and relationships.
- **Data Analysis**: Insights into book categories, employee salaries, member registration trends, and issued books.
- **Summary Reports**: Aggregated data on high-demand books and employee performance.

## Conclusion

This project demonstrates the application of SQL skills in creating and managing a library management system. It includes database setup, data manipulation, and advanced querying, providing a solid foundation for data management and analysis.

## How to Use

1. **Clone the Repository**: Clone this repository to your local machine.
   ```sh
     git clone https://github.com/your-username/library-management-system.git
      cd library-management-system

   ```

2. **Set Up the Database**: Execute the SQL scripts in the `database_setup.sql` file to create and populate the database.
3. **Run the Queries**: Use the SQL queries in the `advanced_queries.sql` and  `medium_queries.sql` file to perform the analysis.
4. **Explore and Modify**: Customize the queries as needed to explore different aspects of the data or answer additional questions.

## License

This project is licensed under the [MIT License](LICENSE).

