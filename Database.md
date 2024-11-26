# Database, Storage, and Backup Basics

---

### 1. **Database Basics**

#### What is a Database?

A database is an organized collection of data stored electronically, which allows efficient retrieval, management, and storage of information.

#### Types of Databases

1. **Relational Databases (RDBMS):**
    - Data is organized into tables (rows and columns).
    - Examples: MySQL, PostgreSQL, Oracle, Microsoft SQL Server.
2. **Non-Relational Databases (NoSQL):**
    - Data is stored in formats like key-value pairs, documents, or graphs.
    - Examples: MongoDB, Cassandra, Redis, DynamoDB.

#### Components of a Database

1. **Tables:** Store data in rows and columns.
2. **Schema:** Defines the structure of the database, such as tables, columns, and data types.
3. **Indexes:** Speed up data retrieval operations.
4. **Queries:** Commands to interact with the database, often written in SQL.

#### Database Operations

-   **Create:** Adding tables or databases.
-   **Read:** Fetching data from the database.
-   **Update:** Modifying existing data.
-   **Delete:** Removing data or structures.

---

### 2. **Storage Basics**

#### What is Storage?

Storage refers to where data is saved for future access. It includes physical and cloud-based systems used to store data persistently.

#### Types of Storage

1. **Primary Storage:**
    - Fast and temporary, e.g., RAM.
    - Used by running processes for immediate access.
2. **Secondary Storage:**
    - Persistent and slower than primary.
    - Examples: Hard Drives (HDD), Solid State Drives (SSD).
3. **Tertiary Storage:**
    - External storage for archiving data.
    - Examples: Tape drives, optical disks (CD/DVD).

#### Storage Systems

1. **File Storage:**
    - Data is stored as files in directories.
    - Example: NTFS, FAT32.
2. **Block Storage:**
    - Data is divided into fixed-size blocks.
    - Example: SAN (Storage Area Network).
3. **Object Storage:**
    - Data is stored as objects with metadata.
    - Example: Amazon S3, Google Cloud Storage.

---

### 3. **Backup Basics**

#### What is Backup?

Backup is the process of copying and archiving data to ensure its recovery in case of data loss.

#### Types of Backups

1. **Full Backup:**
    - Copies all data.
    - Pros: Complete data copy.
    - Cons: Time-consuming and storage-heavy.
2. **Incremental Backup:**
    - Copies only data that changed since the last backup.
    - Pros: Faster, requires less space.
    - Cons: Slower recovery process.
3. **Differential Backup:**
    - Copies all changes since the last full backup.
    - Pros: Easier recovery than incremental.
    - Cons: Requires more space than incremental.
4. **Mirror Backup:**
    - Creates an exact copy of the source data.
    - Pros: Real-time updates.
    - Cons: Vulnerable to accidental deletion or corruption.

#### Backup Strategies

1. **3-2-1 Rule:**
    - Keep 3 copies of your data.
    - Store it on 2 different types of media.
    - Keep 1 copy offsite (e.g., cloud storage).
2. **On-Premises Backup:**
    - Backups stored locally.
    - Example: External HDD, NAS (Network-Attached Storage).
3. **Cloud Backup:**
    - Backups stored remotely in cloud services.
    - Example: Google Drive, AWS Backup.

#### Importance of Backup

-   Protects against data loss from accidental deletion, hardware failures, or cyberattacks.
-   Ensures business continuity.

---

### Key Differences Between Storage and Backup

| **Aspect**    | **Storage**                         | **Backup**                           |
| ------------- | ----------------------------------- | ------------------------------------ |
| **Purpose**   | Stores active data for everyday use | Creates copies for recovery purposes |
| **Frequency** | Real-time or continuous             | Periodic (e.g., daily, weekly)       |
| **Location**  | On-premises or cloud                | Typically offsite/cloud for safety   |
| **Access**    | Regularly accessed                  | Accessed only during recovery        |

---

### Best Practices

1. **Database:**

    - Use indexes for faster queries.
    - Regularly optimize and maintain your database.
    - Implement role-based access control for security.

2. **Storage:**

    - Use SSDs for faster performance.
    - Leverage object storage for large unstructured data.
    - Regularly monitor storage health to avoid failures.

3. **Backup:**
    - Automate backups to avoid human errors.
    - Test backup restoration regularly.
    - Encrypt backups to protect sensitive data.

---

## **Database Management Basics**

### What is SQL?

SQL (Structured Query Language) is a programming language specifically designed for managing and manipulating relational databases. It is widely used for querying, updating, and organizing data stored in relational database systems.

---

### Key Features of SQL

1. **Data Retrieval:** Use `SELECT` statements to retrieve data from tables.
2. **Data Manipulation:** Insert, update, and delete data using `INSERT`, `UPDATE`, and `DELETE`.
3. **Data Definition:** Create, modify, and delete database structures like tables using `CREATE`, `ALTER`, and `DROP`.
4. **Data Control:** Manage user access and permissions using `GRANT` and `REVOKE`.
5. **Transaction Control:** Commit or roll back transactions using `COMMIT` and `ROLLBACK`.

---

### Common SQL Commands

#### 1. **Data Querying (DQL - Data Query Language)**

-   **`SELECT`**: Used to fetch data from a table.
    ```sql
    SELECT column1, column2 FROM table_name WHERE condition;
    ```

#### 2. **Data Manipulation (DML - Data Manipulation Language)**

-   **`INSERT`**: Adds new rows to a table.
    ```sql
    INSERT INTO table_name (column1, column2) VALUES (value1, value2);
    ```
-   **`UPDATE`**: Modifies existing data in a table.
    ```sql
    UPDATE table_name SET column1 = value1 WHERE condition;
    ```
-   **`DELETE`**: Removes rows from a table.
    ```sql
    DELETE FROM table_name WHERE condition;
    ```

#### 3. **Data Definition (DDL - Data Definition Language)**

-   **`CREATE`**: Creates database objects like tables or schemas.
    ```sql
    CREATE TABLE table_name (
        column1 datatype,
        column2 datatype
    );
    ```
-   **`ALTER`**: Modifies an existing database object.
    ```sql
    ALTER TABLE table_name ADD column_name datatype;
    ```
-   **`DROP`**: Deletes database objects.
    ```sql
    DROP TABLE table_name;
    ```

#### 4. **Transaction Control (TCL - Transaction Control Language)**

-   **`COMMIT`**: Saves changes permanently.
    ```sql
    COMMIT;
    ```
-   **`ROLLBACK`**: Reverts changes.
    ```sql
    ROLLBACK;
    ```

#### 5. **Data Control (DCL - Data Control Language)**

-   **`GRANT`**: Provides access to users.
    ```sql
    GRANT SELECT, INSERT ON table_name TO user_name;
    ```
-   **`REVOKE`**: Removes user access.
    ```sql
    REVOKE SELECT, INSERT ON table_name FROM user_name;
    ```

---

### Key Concepts in SQL

#### 1. **Database**

A collection of tables, schemas, and other objects.

#### 2. **Table**

A structured format to store data in rows and columns.

#### 3. **Primary Key**

A column (or set of columns) that uniquely identifies each row in a table.

#### 4. **Foreign Key**

A column that creates a relationship between two tables.

#### 5. **Indexes**

Used to speed up data retrieval operations.

---

### Example of a Simple SQL Workflow

#### 1. Create a Table:

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Salary DECIMAL(10, 2)
);
```

#### 2. Insert Data:

```sql
INSERT INTO Employees (EmployeeID, FirstName, LastName, Salary)
VALUES (1, 'John', 'Doe', 50000.00);
```

#### 3. Query Data:

```sql
SELECT * FROM Employees WHERE Salary > 40000;
```

#### 4. Update Data:

```sql
UPDATE Employees
SET Salary = 55000.00
WHERE EmployeeID = 1;
```

#### 5. Delete Data:

```sql
DELETE FROM Employees WHERE EmployeeID = 1;
```

---

### Advantages of SQL

1. **Standardized Language:** SQL is a standardized language supported by most relational database systems.
2. **Powerful and Flexible:** Supports a wide range of operations on data.
3. **High Performance:** Optimized for managing large datasets.
4. **Compatibility:** Works with many database management systems like MySQL, PostgreSQL, Oracle, and SQL Server.

---

### Popular SQL Database Management Systems

1. **MySQL**
2. **PostgreSQL**
3. **Microsoft SQL Server**
4. **Oracle Database**
5. **SQLite**

---
