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

## **SQL Data Types and Commands**

### **SQL Data Types**

Data types in SQL define the kind of data that can be stored in a table column.

#### 1. **Numeric Data Types**

Used for storing numbers.

| **Data Type**        | **Description**                                 |
| -------------------- | ----------------------------------------------- |
| **INT/INTEGER**      | Whole numbers.                                  |
| **SMALLINT**         | Smaller range of whole numbers.                 |
| **BIGINT**           | Large range of whole numbers.                   |
| **DECIMAL(p,s)**     | Fixed-point numbers with precision and scale.   |
| **NUMERIC(p,s)**     | Same as `DECIMAL`.                              |
| **FLOAT**            | Approximate numbers with floating-point values. |
| **REAL**             | Single-precision floating-point numbers.        |
| **DOUBLE PRECISION** | Double-precision floating-point numbers.        |

---

#### 2. **Character/String Data Types**

Used for storing text.

| **Data Type**  | **Description**                               |
| -------------- | --------------------------------------------- |
| **CHAR(n)**    | Fixed-length string.                          |
| **VARCHAR(n)** | Variable-length string with a max length `n`. |
| **TEXT**       | Large variable-length string.                 |

---

#### 3. **Date and Time Data Types**

Used for storing date and time values.

| **Data Type** | **Description**                              |
| ------------- | -------------------------------------------- |
| **DATE**      | Stores date (YYYY-MM-DD).                    |
| **TIME**      | Stores time (HH:MM:SS).                      |
| **DATETIME**  | Stores date and time (YYYY-MM-DD HH:MM:SS).  |
| **TIMESTAMP** | Stores date and time with timezone support.  |
| **YEAR**      | Stores year as a 4-digit value (e.g., 2024). |

---

#### 4. **Binary Data Types**

Used for storing binary data like files or images.

| **Data Type**    | **Description**                            |
| ---------------- | ------------------------------------------ |
| **BINARY(n)**    | Fixed-length binary data.                  |
| **VARBINARY(n)** | Variable-length binary data.               |
| **BLOB**         | Binary Large Object for large binary data. |

---

#### 5. **Boolean Data Types**

Stores logical values.
| **Data Type** | **Description** |
|---------------------|------------------------------|
| **BOOLEAN** | Stores `TRUE` or `FALSE`. |

---

#### 6. **Other Data Types**

Used for specialized data.

| **Data Type** | **Description**                    |
| ------------- | ---------------------------------- |
| **ENUM**      | Stores predefined values.          |
| **SET**       | Stores multiple predefined values. |
| **JSON**      | Stores JSON-formatted data.        |
| **XML**       | Stores XML-formatted data.         |

---

### **SQL Commands**

SQL commands are categorized into five groups:

---

#### 1. **Data Query Language (DQL)**

Used for querying data from the database.

| **Command** | **Description**                         |
| ----------- | --------------------------------------- |
| `SELECT`    | Retrieves data from one or more tables. |

**Example:**

```sql
SELECT column1, column2 FROM table_name WHERE condition;
```

---

#### 2. **Data Definition Language (DDL)**

Used to define or modify database structures.

| **Command** | **Description**                                      |
| ----------- | ---------------------------------------------------- |
| `CREATE`    | Creates new database objects like tables.            |
| `ALTER`     | Modifies existing database objects.                  |
| `DROP`      | Deletes database objects.                            |
| `TRUNCATE`  | Removes all data from a table but retains structure. |

**Examples:**

-   Create:
    ```sql
    CREATE TABLE table_name (
        column1 datatype,
        column2 datatype
    );
    ```
-   Alter:
    ```sql
    ALTER TABLE table_name ADD column_name datatype;
    ```
-   Drop:
    ```sql
    DROP TABLE table_name;
    ```

---

#### 3. **Data Manipulation Language (DML)**

Used for managing data within tables.

| **Command** | **Description**                    |
| ----------- | ---------------------------------- |
| `INSERT`    | Adds new records to a table.       |
| `UPDATE`    | Modifies existing data in a table. |
| `DELETE`    | Removes records from a table.      |

**Examples:**

-   Insert:
    ```sql
    INSERT INTO table_name (column1, column2) VALUES (value1, value2);
    ```
-   Update:
    ```sql
    UPDATE table_name SET column1 = value1 WHERE condition;
    ```
-   Delete:
    ```sql
    DELETE FROM table_name WHERE condition;
    ```

---

#### 4. **Transaction Control Language (TCL)**

Used to manage database transactions.

| **Command** | **Description**                                   |
| ----------- | ------------------------------------------------- |
| `COMMIT`    | Saves the changes permanently.                    |
| `ROLLBACK`  | Reverts changes since the last commit.            |
| `SAVEPOINT` | Sets a point within a transaction to rollback to. |

**Examples:**

-   Commit:
    ```sql
    COMMIT;
    ```
-   Rollback:
    ```sql
    ROLLBACK;
    ```

---

#### 5. **Data Control Language (DCL)**

Used to control access to data.

| **Command** | **Description**                 |
| ----------- | ------------------------------- |
| `GRANT`     | Provides permissions to users.  |
| `REVOKE`    | Removes permissions from users. |

**Examples:**

-   Grant:
    ```sql
    GRANT SELECT, INSERT ON table_name TO user_name;
    ```
-   Revoke:
    ```sql
    REVOKE SELECT, INSERT ON table_name FROM user_name;
    ```

---

### **Specialized SQL Clauses**

-   **`WHERE`**: Filters rows based on conditions.
-   **`GROUP BY`**: Groups rows with similar values.
-   **`HAVING`**: Filters groups after grouping.
-   **`ORDER BY`**: Sorts query results.
-   **`LIMIT`**: Limits the number of rows returned.
-   **`JOIN`**: Combines rows from multiple tables.

**Example of a JOIN:**

```sql
SELECT employees.name, departments.name
FROM employees
JOIN departments ON employees.department_id = departments.id;
```

---

## **Storage in Detail**

Storage systems are essential for saving, retrieving, and managing data in modern computing. Let’s explore the key concepts, types, and technologies involved.

---

### **1. Types of Storage**

#### A. **Primary Storage**

-   **Definition:** Volatile memory used for immediate processing.
-   **Examples:** RAM (Random Access Memory), Cache memory.
-   **Features:**
    -   High-speed access.
    -   Temporary storage (data is lost when power is off).

#### B. **Secondary Storage**

-   **Definition:** Persistent storage for long-term use.
-   **Examples:** Hard Disk Drives (HDDs), Solid-State Drives (SSDs).
-   **Features:**
    -   Non-volatile (data retained even when power is off).
    -   Used for operating systems, applications, and data files.

#### C. **Tertiary Storage**

-   **Definition:** Used for backup, archiving, or infrequent access.
-   **Examples:** Tape drives, Optical disks (CD/DVD/Blu-ray).
-   **Features:**
    -   Slower access time.
    -   Typically used for disaster recovery.

#### D. **Cloud Storage**

-   **Definition:** Data stored on remote servers accessed via the internet.
-   **Examples:** Google Drive, Amazon S3, Microsoft Azure.
-   **Features:**
    -   Highly scalable.
    -   Requires network connectivity.

---

### **2. Disk Storage**

#### A. **Hard Disk Drive (HDD)**

-   **Components:**
    -   **Platter:** Magnetic disks that store data.
    -   **Read/Write Head:** Accesses and modifies data.
    -   **Spindle:** Rotates the platters.
-   **Features:**
    -   Large capacity.
    -   Mechanical parts make it slower than SSDs.

#### B. **Solid-State Drive (SSD)**

-   **Components:**
    -   Flash memory chips (NAND).
    -   Controller for managing data storage.
-   **Features:**
    -   Faster than HDDs.
    -   No moving parts, more durable.

#### C. **Hybrid Drives (SSHD)**

-   Combines an HDD and an SSD.
-   Frequently accessed data is stored in the SSD portion for speed.

---

### **3. RAID (Redundant Array of Independent/Inexpensive Disks)**

RAID combines multiple physical disks into a single logical unit for better performance, redundancy, or both.

#### A. **Types of RAID**

| **RAID Level** | **Description**                                       | **Pros**                                | **Cons**                                       |
| -------------- | ----------------------------------------------------- | --------------------------------------- | ---------------------------------------------- |
| **RAID 0**     | Stripes data across disks without redundancy.         | High performance, full capacity usage.  | No fault tolerance. Data loss if a disk fails. |
| **RAID 1**     | Mirrors data across two disks.                        | High fault tolerance. Easy recovery.    | Storage capacity halved.                       |
| **RAID 5**     | Stripes data with parity across 3+ disks.             | Fault tolerance. Efficient storage use. | Slower write speeds. Needs 3+ disks.           |
| **RAID 6**     | Like RAID 5 but with dual parity for more redundancy. | Can survive 2 disk failures.            | More parity overhead.                          |
| **RAID 10**    | Combines RAID 1 (mirroring) and RAID 0 (striping).    | High performance and fault tolerance.   | Expensive, requires at least 4 disks.          |

#### B. **RAID Use Cases**

-   **RAID 0:** High-speed applications (e.g., gaming, video editing).
-   **RAID 1:** Critical systems needing data redundancy.
-   **RAID 5/6:** Enterprise environments needing a balance of performance and redundancy.
-   **RAID 10:** Databases and applications requiring speed and fault tolerance.

---

### **4. File Systems**

The file system manages how data is stored and retrieved on a disk.

#### Common File Systems:

-   **NTFS (New Technology File System):** Default for Windows. Supports large files and advanced permissions.
-   **FAT32 (File Allocation Table):** Older, compatible with many devices but limited to 4GB file size.
-   **EXT (Extended File System):** Used in Linux. Versions include EXT2, EXT3, and EXT4.
-   **APFS (Apple File System):** Optimized for macOS and iOS devices.

---

### **5. Storage Networking**

#### A. **Direct-Attached Storage (DAS)**

-   Physically connected to a computer.
-   Examples: Internal HDD/SSD, external USB drives.

#### B. **Network-Attached Storage (NAS)**

-   Connected to a network for shared storage.
-   Provides file-level access.
-   Example: A home media server.

#### C. **Storage Area Network (SAN)**

-   High-speed network of storage devices.
-   Provides block-level access.
-   Common in enterprise environments.

---

### **6. Backup Storage**

#### A. **Local Backup**

-   Data stored on external HDDs, NAS devices, or tape drives.

#### B. **Cloud Backup**

-   Data stored on remote servers for disaster recovery.
-   Examples: AWS Backup, Google Backup.

#### C. **Backup Methods**

-   **Full Backup:** Copies all data. Time and storage-intensive.
-   **Incremental Backup:** Copies only data changed since the last backup.
-   **Differential Backup:** Copies all changes since the last full backup.

---

### **7. Key Metrics for Storage Performance**

| **Metric**                                    | **Description**                                     |
| --------------------------------------------- | --------------------------------------------------- |
| **Capacity**                                  | Total amount of data the system can store.          |
| **Throughput**                                | Amount of data processed in a given time.           |
| **Latency**                                   | Time taken to process a request (e.g., read/write). |
| **IOPS (Input/Output Operations per Second)** | Measure of disk performance.                        |

---

### **8. Storage Best Practices**

1. **Regular Monitoring:**
    - Check disk health, RAID status, and IOPS.
2. **Implement RAID:**
    - Use RAID for redundancy and performance.
3. **Data Backup:**
    - Follow the 3-2-1 rule (3 copies, 2 different media, 1 offsite).
4. **Cloud Integration:**
    - Use cloud storage for scalability and disaster recovery.
5. **Encryption:**
    - Protect sensitive data with encryption.

---

### **Mirroring and Striping in Data Storage**

Mirroring and striping are key techniques used in data storage, often in the context of RAID (Redundant Array of Independent/Inexpensive Disks). Each method serves specific purposes related to performance, redundancy, and fault tolerance.

---

### **1. Mirroring (RAID 1)**

**Definition:**  
Mirroring involves duplicating the same data on two or more disks. This ensures that if one disk fails, the other(s) still have an identical copy of the data.

#### **How It Works:**

-   Data written to one disk is simultaneously written to another.
-   Read operations can occur from either disk, often improving read speed.
-   No data striping or splitting—each disk holds a full copy of all data.

#### **Advantages:**

1. **High Fault Tolerance:** Complete data redundancy ensures no data loss if one disk fails.
2. **Fast Read Performance:** Multiple disks can be used for reading in parallel.
3. **Easy Recovery:** In the event of a failure, the mirrored disk can be used directly.

#### **Disadvantages:**

1. **Storage Efficiency:** Only 50% of the total disk capacity is usable (e.g., two 1TB disks provide 1TB usable storage).
2. **Write Performance:** Writing to two disks simultaneously may introduce a slight delay.

#### **Use Cases:**

-   Critical systems where data loss is unacceptable, such as:
    -   Financial databases.
    -   Server environments requiring high availability.

---

### **2. Striping (RAID 0)**

**Definition:**  
Striping involves splitting data into smaller chunks and spreading (or "striping") them across multiple disks. This improves performance but provides no redundancy.

#### **How It Works:**

-   Data is divided into "stripes" and written sequentially across all disks in the array.
-   Parallel read/write operations improve speed significantly.
-   No data duplication or parity information is stored.

#### **Advantages:**

1. **High Performance:**
    - Faster read and write speeds due to parallel access.
    - Ideal for large file operations like video editing.
2. **Full Disk Utilization:** All available storage capacity is used (e.g., two 1TB disks provide 2TB usable storage).

#### **Disadvantages:**

1. **No Fault Tolerance:**
    - If one disk fails, all data is lost.
2. **Higher Risk:** Increased chance of failure since more disks are involved.

#### **Use Cases:**

-   High-performance applications where speed is critical, and data loss is acceptable, such as:
    -   Gaming systems.
    -   Temporary data storage.

---

### **Key Comparison: Mirroring vs. Striping**

| **Aspect**             | **Mirroring (RAID 1)**              | **Striping (RAID 0)**                    |
| ---------------------- | ----------------------------------- | ---------------------------------------- |
| **Purpose**            | Redundancy and fault tolerance.     | Performance improvement.                 |
| **Data Storage**       | Duplicates data on multiple disks.  | Splits data across multiple disks.       |
| **Fault Tolerance**    | High (data survives disk failure).  | None (data lost if a single disk fails). |
| **Storage Efficiency** | 50% (due to duplication).           | 100% (no redundancy).                    |
| **Read Performance**   | Improved (parallel reading).        | Very high (parallel reading).            |
| **Write Performance**  | Slightly slower than a single disk. | Very high (parallel writing).            |
| **Ideal Use Case**     | Mission-critical systems.           | Performance-critical tasks.              |

---

### **Combining Mirroring and Striping: RAID 10**

**RAID 10 (1+0):** Combines the benefits of both techniques.

-   **How It Works:** Data is first mirrored (RAID 1) for redundancy, then striped (RAID 0) for performance.
-   **Advantages:**
    -   High fault tolerance.
    -   High read/write performance.
-   **Disadvantages:**
    -   Requires at least 4 disks.
    -   Expensive due to the number of disks needed.

---

### **Visual Representation**

#### Mirroring:

```
Disk 1: | DATA A | DATA B | DATA C |
Disk 2: | DATA A | DATA B | DATA C |
```

#### Striping:

```
Disk 1: | DATA A1 | DATA B1 | DATA C1 |
Disk 2: | DATA A2 | DATA B2 | DATA C2 |
```

#### RAID 10 (Mirroring + Striping):

```
Disk 1: | DATA A1 | DATA B1 |
Disk 2: | DATA A1 | DATA B1 |
Disk 3: | DATA A2 | DATA B2 |
Disk 4: | DATA A2 | DATA B2 |
```

---
