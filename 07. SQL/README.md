# SQL & PopSQL

## 1. General

### Cheat sheets 

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/SQL-Cheet-Sheet-1.png"></p>
<p align="center" font-size="20px">Figure 1. Cheat sheet 1</p>

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/SQL-Cheat-Sheet-2.png"></p>
<p align="center" font-size="20px">Figure 2. Cheat sheet 2</p>

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/SQL-Cheat-Sheet-3.png"></p>
<p align="center" font-size="20px">Figure 3. Cheat sheet 3</p>

### Type of variables 

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/sql_var.png"></p>
<p align="center" font-size="20px">Figure 4. Type of SQL variables</p>

### Comparison operations

```sql
= -- equals
<> -- not equals
> -- greater than
< -- less than
>= -- greater or equal
<= -- less than or equal
AND
OR

```

## 2. Creating, updating and deleting data/table

With simple/unique table

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/sql_var.png"></p>
<p align="center" font-size="20px">Figure 4. Type of SQL variables</p>

### Creating a table

```sql
CREATE TABLE STUDENT (
    student_id INT PRIMARY KEY,
    name_people VARCHAR(255),
    major VARCHAR (255)
);
```

Alternative primary key statement 
```sql
CREATE TABLE Student (
    student_id INT,
    name_people VARCHAR(255),
    major VARCHAR (255), 
    PRIMARY KEY (student_id)
);
```

Setting columns specificity
```sql
CREATE TABLE Student (
    student_id INT,
    name_people VARCHAR(255) NOT NULL, --cannot have empty values
    major VARCHAR (255) UNIQUE, --each entry must be distinct
    minor VARCHAR (255) DEFAULT '20 ECTS', --set default value
    PRIMARY KEY (student_id)
);
```

Auto increment values for primary key
```sql
CREATE TABLE Student (
    student_id INT AUTO_INCREMENT,
    name_people VARCHAR(255),
    major VARCHAR (255),
    PRIMARY KEY (student_id)
);
```

```sql
INSERT INTO Student(name_people, major) VALUES ('helen, 'computer science');
```

```sql
DESCRIBE Student;
```

```sql
DROP TABLE Student
```

```sql
ALTER TABLE Student ADD gpa DECIMAL(3, 2);
```

```sql
ALTER TABLE Student DROP COLUMN gpa;
```

### Inserting data in a table

Inserting a row
```sql
INSERT INTO Student VALUES(1, 'jack', 'biology');
INSERT INTO Student VALUES(2, 'kate', 'sociology');
```

Inserting values for specific columns
```sql
INSERT INTO Student(student_id, name) VALUES(1, 'jack');
```

### Update data in table

Changing label name
```sql
UPDATE Student
SET major = 'Bio'
WHERE major = 'Biology';
```

```sql
UPDATE Student
SET major = 'Biochemistry'
WHERE major = 'Biology' OR major = 'Chemistry';
```

```sql
UPDATE Student
SET name_people = 'Tom', major = 'Undecided'
WHERE student_id = 5;
```

Changing values based on other column value
```sql
UPDATE Student
SET major = 'Computer science'
WHERE student_id = 5;
```

```sql
SELECT * FROM Student;
```

### Delete data in table

Deleting row(s)
```sql
DELETE FROM Student 
WHERE name_poeple = 'Tom'
```

Deleting all entries
```sql
DELETE FROM Student 
```

## 3. Queries

### Select

Simple select
```sql
SELECT * FROM Student; 
```

```sql
SELECT name_people, major
FROM Student; 
```

```sql
SELECT Student.name_people, Student.major
FROM Student; 
```

Select ordered
```sql
SELECT Student.name_people, Student.major
FROM Student 
ORDER BY major;
```

```sql
SELECT Student.name_people, Student.major
FROM Student 
ORDER BY major DESC;
```

```sql
SELECT Student.name_people, Student.major
FROM Student 
ORDER BY major, student_id;
```

With limit
```sql
SELECT Student.name_people, Student.major
FROM Student 
ORDER BY major
LIMIT 2;
```

With filter
```sql
SELECT Student.name_people, Student.major
FROM Student 
ORDER BY major
WHERE Student_id < 10 AND student_id > 2;
```

```sql
SELECT Student.name_people, Student.major
FROM Student 
ORDER BY major
WHERE Student_id <> 10;
```

```sql
SELECT Student.name_people, Student.major
FROM Student 
ORDER BY major
WHERE name_people IN ('Claire', 'Kate', 'Pierre');
```

```sql
SELECT Student.name_people, Student.major
FROM Student 
ORDER BY major
WHERE name_people IN ('Claire', 'Kate', 'Pierre') AND Student_id <> 10;
```

## 4. Working with more complex schema

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/sql_var.png"></p>
<p align="center" font-size="20px">Figure 4. Type of SQL variables</p>

