# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```
### Submission:
GOWSHIK S 212223220026

**Question 1**
![Q1](https://github.com/user-attachments/assets/e11a7152-453e-427c-ace6-8d9f846540b2)

```sql
CREATE TABLE Employees(
EmployeeID PRIMARY KEY,
FirstName NOT NULL,
LastName NOT NULL,
Email UNIQUE,
Salary DECIMAL CHECK(Salary > 0),
DepartmentID INTEGER,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**
![A1](https://github.com/user-attachments/assets/86235bca-2ddc-4f2d-a158-2b89bad9b01d)

**Question 2**
![Q2](https://github.com/user-attachments/assets/3c1a3134-7b62-4044-98fe-b6d7444c4d0d)

```sql
ALTER TABLE Student_details
ADD Date_of_birth Date;
```

**Output:**
![A2](https://github.com/user-attachments/assets/deaa9450-4ab5-46e8-b07f-b1f423fc10b3)

**Question 3**
![Q3](https://github.com/user-attachments/assets/94141be7-acae-43b7-bf7f-708012bdb1f8)

```sql
INSERT INTO Products(ProductID, Name, Category, Price, Stock)
VALUES (106, "Fitness Tracker", "Wearables", NULL, NULL);

INSERT INTO Products(ProductID, Name, Category, Price, Stock)
VALUES (107, "Laptop", "Electronics", 999.99, 50);

INSERT INTO Products(ProductID, Name, Category, Price, Stock)
VALUES (108, "Wireless Earbuds", "Accessories", NULL, 100);
```

**Output:**
![A3](https://github.com/user-attachments/assets/11c330f1-889b-436e-a09d-c08f0e327371)

**Question 4**
![Q4](https://github.com/user-attachments/assets/3f078f30-ea5b-4021-8733-b6417a2cceee)

```sql
INSERT INTO Employee(EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary FROM Former_employees;
```

**Output:**
![A4](https://github.com/user-attachments/assets/7cd124b6-20c9-42d3-bdb1-48bb41f38dce)

**Question 5**
![Q5](https://github.com/user-attachments/assets/4c3e15c9-f268-477b-91d8-98807f6f3427)

```sql
CREATE TABLE Products(
ProductID PRIMARY KEY,
ProductName NOT NULL,
Price REAL CHECK(Price > 0),
Stock INTEGER CHECK(Stock >= 0)
);
```

**Output:**
![A5](https://github.com/user-attachments/assets/8dc31525-b4ab-46a2-9f76-ed471031a158)

**Question 6**
![Q6](https://github.com/user-attachments/assets/cf0e68b8-14aa-4acd-b001-07721ec8e9d3)

```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT CHECK(Length(icom_id)=4),
FOREIGN KEY (icom_id) REFERENCES company(com_id)
ON UPDATE SET NULL
ON DELETE SET NULL
);
```

**Output:**
![A6](https://github.com/user-attachments/assets/ffe49c70-7513-4e9e-94cb-1f66f0279f94)

**Question 7**
![Q7](https://github.com/user-attachments/assets/af087f93-4625-48bf-8a4d-1ecea52c9357)


```sql
CREATE TABLE contacts(
contact_id INTEGER PRIMARY KEY,
first_name TEXT NOT NULL,
last_name TEXT NOT NULL,
email TEXT,
phone TEXT NOT NULL CHECK(Length(phone) >= 10)
);
```

**Output:**
![A7](https://github.com/user-attachments/assets/ccffa308-254e-49f2-8d40-e3211fcf008d)

**Question 8**
![Q8](https://github.com/user-attachments/assets/2179cbf1-00ab-42c1-964c-719f2d05f9a3)

```sql
ALTER TABLE Student_details
ADD mobilenumber number;
```

**Output:**
![A8](https://github.com/user-attachments/assets/30abeb4d-d97d-4eae-a1c4-723d644052c4)

**Question 9**
![Q9](https://github.com/user-attachments/assets/1ea61151-7cce-458c-b56a-30a8a7eda491)

```sql
CREATE TABLE Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE);
```

**Output:**
![A9](https://github.com/user-attachments/assets/3562eb28-f660-450c-8d3d-ae824bc4b4f8)

**Question 10**
![Q10](https://github.com/user-attachments/assets/3175834d-4228-40f3-8286-112b2c6253e0)

```sql
INSERT INTO Student_details (RollNo, Name, Gender, Subject, MARKS)
VALUES (201, "David Lee", "M", "Physics", 92);
```

**Output:**
![A10](https://github.com/user-attachments/assets/0f9467f8-f6b6-4b35-971a-0407cf369ba5)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
