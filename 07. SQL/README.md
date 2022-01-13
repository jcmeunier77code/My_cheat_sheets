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

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/sql_var.png" width = '650' height = 'auto'></p>
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

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/student.png" width = '400' height = 'auto'></p>
<p align="center" font-size="20px">Figure 5. Simple table</p>

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

<p align="center"><img src="https://github.com/jcmeunier77code/My_cheat_sheets/blob/master/07.%20SQL/Complex.png" width = '700' height = 'auto'></p>
<p align="center" font-size="20px">Figure 6. Complex schema</p>

### Creating complex multitable schema

```sql
CREATE TABLE employee (
    emp_id INT PRIMARY KEY,
    first_name VARCHAR(40),
    last_name VARCHAR(40), 
    birth_day DATE,
    sex VARCHAR(1),
    salary INT,
    super_id INT,
    branch_id INT
);

CREATE TABLE branch(
    branch_id INT PRIMARY KEY,
    branch_name VARCHAR(40),
    mgr_id INT,
    mgr_start_date DATE,
    FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL
);

ALTER TABLE employee
ADD FOREIGN KEY(branch_id)
REFERENCES branch(branch_id)
ON DELETE SET NULL;

ALTER TABLE employee
ADD FOREIGN KEY(super_id)
REFERENCES employee(emp_id)
ON DELETE SET NULL;

CREATE TABLE client (
    client_id INT PRIMARY KEY,
    client_id VARCHAR(40),
    branch_id INT,
    FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE SET NULL
);

CREATE TABLE works_with (
    emp_id INT?
    client_id INT,
    total_sales INT,
    PRIMARY KEY(emp_id, client_id),
    FOREIGN KEY(emp_id) REFERENCES employee(emp_id) ON DELETE CASCADE, 
    FOREIGN KEY(client_id) REFERENCES client(client_id) ON DELETE CASCADE
);

CREATE TABLE branch_supplier (
    branch_id INT,
    supplier_name VARCHAR(40),
    supply_type VARCHAR(40),
    PRIMARY KEY(branch_id, supplier_name),
    FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE CASCADE,
);
```

### Inserting values within connected tables

```sql
--Corporate
INSERT INTO employee VALUES(100, 'David', 'Wallace', '1967-11-17', 'M', 250000, NULL, NULL);

INSERT INTO branch VALUES(1, 'Corporate', 100, '2006-02-09');

UPDATE employee
SET branch_id = 1
WHERE emp_id = 100;

INSERT INTO employee VALUES(101, 'Jan', 'Levinson', '1961-05-11', 'F', 11000, 100, 1);
```

```sql
--Scranton
INSERT INTO employee VALUES(102, 'Michael', 'Scott', '1967-11-17', 'M', 250000, NULL, NULL);

INSERT INTO branch VALUES(2, 'Scranton', 102, '1992-02-09');

UPDATE employee
SET branch_id = 2
WHERE emp_id = 102;

INSERT INTO employee VALUES(103, 'Angela', 'Martin', '1971-05-11', 'F', 11000, 106, 2);
```

```sql
--Stamford
INSERT INTO employee VALUES(106, 'Josh', 'Porter', '1969-11-17', 'M', 250000, NULL, NULL);

INSERT INTO branch VALUES(3, 'Stamford', 106, '1992-02-09');

UPDATE employee
SET branch_id = 2
WHERE emp_id = 106;

INSERT INTO employee VALUES(107, 'Andy', 'Bernard', '1973-05-11', 'F', 11000, 102, 2);
```

```sql
--branch supplier 
INSERT INTO branch_supplier VALUES(2, 'Hammer Mill', 'Paper');
```

```sql
--client
INSERT INTO client VALUES(400, 'Sunmore Highschool', 2);
```

```sql
INSERT INTO works_with VALUES(105, 400, 55000);
```

### Select 

```sql
--select all employees
SELECT *
FROM employee;
```

```sql
-- find all employees ordered by salary
SELECT *
FROM employee
ORDER BY salary, sex DESC;
```

```sql
--find the first 5 employees
SELECT *
FROM employee
LIMIT 5;
```

```sql
--find the first and last names of all employees
SELECT first_name, last_name
FROM employee;
```

```sql
--find the forename and surname of all employees
SELECT first_name AS forename, last_name AS surname
FROM employee;
```

```sql
--find out all the different genders
SELECT DISTINCT sex
FROM employee;
```


### Functions

#### Count
```sql
--find the number of employees
SELECT COUNT(emp_id)
FROM employee;
```

```sql
--find the number employees female born after 1978
SELECT COUNT(emp_id)
FROM employee
WHERE sex = 'F' AND birth_date > '1970-01-01';
```

```sql
--find out how many males and females there are
SELECT COUNT(sex), sex
FROM employee
GROUP BY sex;
```

#### Average
```sql
SELECT AVG(salary)
FROM employee
WHERE sex = 'M';
```

### Sum
```sql
SELECT SUM(salary)
FROM employee
```

```sql
--find the total sales of each salesman
SELECT SUM(total_sales), emp_id
FROM work_with
GROUP BY emp_id;
```

```sql
--find how much each client spend
SELECT SUM(total_sales), client_id
FROM work_with
GROUP BY client_id;
```

### Wild card
```sql
% -- pattern with any number of character
- -- pattern with one character
LIKE -- statement for finding a specific pattern
```

```sql
--find any client that have 'LLC' in their name
SELECT *
FROM client
WHERE client_name LIKE '%LLC';
```

```sql
--find any branch name that have 'label' somewhere in their name
SELECT *
FROM branch_supplier
WHERE supplier_name LIKE '%Label%';
```

```sql
--find any employee born in october
--date format: '1967-10-12'
SELECT *
FROM employee
WHERE birth_date LIKE '____-10%';
```

```sql
--find any client who are schools
SELECT *
FROM client
WHERE client_name LIKE '%school%';
```

### Union
```sql
--find a list of employee and branch name
SELECT first_name
FROM employee
UNION
SELECT branch_name --add the name of the branch in the same column (statement must have the same number of columns)
FROM branch;
```

```sql
--find a list of all client names + id with all supplier names + id
--rename the lists as 'all names' and 'id'
SELECT client_name AS all_names, branch_id AS id
FROM client 
UNION
SELECT supplier_name, branch_id
FROM branch_supplier;
```

```sql
--find a list of all money spent or earned by the company
SELECT salary
FROM employee
UNION
SELECT total_sales
FROM work_with;
```

### Join
Statement for selecting a number of rows from different table based on a common column (eg. id)

```sql
LEFT JOIN --select all the rows of the left table even if the right part has no entry
RIGHT JOIN --select all the rows of the right table even if the left part has no entry
(INNER) JOIN --by default, join rows only for entries that exist in both tables
OUTER JOIN --doesn't exist in sql but it is a combination of RIGHT and LEFT JOIN
```


```sql
--find all branches and the names of their managers
SELECT employee.emp_id, employee.first_name, branch.branch_name
FROM employee
JOIN branch
ON employee.emp_id= branch.mgr_id;
```

### Nested queries
```sql
-- find names of all employees who have sold over 30.000 to a single client
SELECT employee.first_name, employee.last_name
FROM employee
WHERE employee.emp_id IN (
    SELECT work_with.emp_id
    FROM work_with
    WHERE work_with.total_sales > 30000
    );
```


```sql
-- find all clients who are handled by the branch that Michael Scott manages
SELECT client.client_name
FROM client
WHERE client.branch_id = ( -- = works only if the nested query return only one result
    SELECT branch.branch_id 
    FROM branch
    WHERE branch.mgr_id = 102
    LIMIT = 1 -- to make sure that the nested query returns only one entry
    );
```

### On delete
```sql
ON DELETE SET NULL -- set the foreign key in the connected table to null (only if the id in the connected table is NOT a primary key)
ON DELETE SET CASCADE -- delete the corresponding row in the connected table 
```

```sql
CREATE TABLE branch (
branch_id INT PRIMARY KEY,
branch_name VARCHAR(40),
mgr_id INT, 
mgr_start_date DATE,
FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL
);
```

```sql
DELETE FROM employee
WHERE emp_id = 102;
```

### Trigger
Trigger/program an action when a command is launch
When: BEFORE, AFTER
On which action: INSERT, DELETE, UPDATE

```sql
--create a table
CREATE TABLE trigger_test(
message VARCHAR(100)
);
```

```sql
-- set up a trigger when a new entry is added
DELIMITER $$--set the delimiter to $$ instead of ; so that no conflict with the sql command that is nested (i.e. INSERT INTO)
-- !!! delimiter cannot be changed in popsql, thus this command has to be run into the mysql console
CREATE 
    TRIGGER my_trigger BEFORE INSERT 
    ON employee 
    FOR EACH ROW BEGIN
        INSERT INTO trigger_test VALUES('add a new employee');
        --INSERT INTO trigger_test VALUES(NEW.first_name); alternative for adding the name of the employee instead of 'add a new employee'
    END$$
DELIMITER ; -- re-initialize the delimiter to ;
```

Activating the trigger in the mysql console
```console
mysql> DELIMITER $$
mysql> CREATE 
    TRIGGER my_trigger BEFORE INSERT 
    ON employee 
    FOR EACH ROW BEGIN
        INSERT INTO trigger_test VALUES('add a new employee');
        --INSERT INTO trigger_test VALUES(NEW.first_name); alternative for adding the name of the employee instead of 'add a new employee'
    END$$
 mysql> DELIMITER ;
 ```

```sql
-- set up a trigger with IF statement when a new entry is added
DELIMITER $$ 
CREATE 
    TRIGGER my_trigger BEFORE INSERT 
    ON employee 
    FOR EACH ROW BEGIN
        IF NEW.sex = 'M' THEN
            INSERT INTO trigger_test VALUES('added male employee')
        ELIF NEW.sex = 'F' THEN
            INSERT INTO trigger_test VALUES('added female')
        ELSE
            INSERT INTO trigger_test VALUES('added other type of employee')
        END IF;
    END$$
DELIMITER ; 
        
SELECT * FROM trigger_test; 
```

```sql
-- add an entry and tigger the trigger
INSERT INTO employee
VALUES(109, 'Oscar', 'Martinez', '1968-02-19', 'M', 69000, 106, 3);

SELECT * FROM trigger_test;
```

For dropping a trigger (in command, console)
```console
mysql> DROP TRIGGER my_trigger;
```

```sql

```


```sql

```


