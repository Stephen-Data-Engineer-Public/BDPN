
### **Creating a Table in SQL Server**

**1️ Basic Syntax**

```sql
CREATE TABLE table_name (
    column1 datatype [constraints],
    column2 datatype [constraints],
    ...
);
```

**2️ Common Data Types**

| Data Type      | Description                                       |
| -------------- | ------------------------------------------------- |
| `INT`          | Integer numbers (whole numbers)                   |
| `BIGINT`       | Larger integers                                   |
| `DECIMAL(p,s)` | Fixed-point numbers, `p` = precision, `s` = scale |
| `FLOAT`        | Approximate decimal numbers                       |
| `CHAR(n)`      | Fixed-length string of length `n`                 |
| `VARCHAR(n)`   | Variable-length string (max length `n`)           |
| `TEXT`         | Large text                                        |
| `DATE`         | Stores date (`YYYY-MM-DD`)                        |
| `DATETIME`     | Stores date and time (`YYYY-MM-DD HH:MM:SS`)      |
| `BOOLEAN`      | True/False value                                  |




**53 Example**

```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(50) NOT NULL
);

CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    EmpName VARCHAR(100) NOT NULL,
    DeptID INT,
    FOREIGN KEY (DeptID) REFERENCES Departments(DeptID)
);
```
