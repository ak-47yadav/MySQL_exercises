CREATE

#### 1. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id.

```sql
Ans: mysql> create table `countries`(
    -> country_id varchar(20),
    -> country_name varchar(20),
    -> region_id varchar(10)
    -> );
```

#### 2. Write a SQL statement to create a simple table countries including columns country_id,country_name and region_id which is already exists.
```sql
mysql> create table if not exists countries(
    -> country_id varchar(2),
    -> country_name varchar(40),
    -> region_id decimal(10,0)
    -> );
```
#### 3. Write a SQL statement to create the structure of a table dup_countries similar to countries.
```sql
mysql> create table if not exists dup_countries
    -> like countries;
```
#### 4. Write a SQL statement to create a duplicate copy of countries table including structure and data by name dup_countries.
```sql
mysql> create table if not exists dup_countries as select*from countries;
```
#### 5. Write a SQL statement to create a table countries set a constraint NULL.
```sql
mysql> CREATE TABLE countries(
    -> COUNTRY_ID VARCHAR(20) NOT NULL,
    -> COUNTRY_NAME VARCHAR(20) NOT NULL,
    -> REGION_ID INT(5) NOT NULL
    -> );
```
#### 6. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary, max_salary and check whether the max_salary amount exceeding the upper limit 25000.
```sql
mysql> CREATE TABLE IF NOT EXISTS jobs(
    -> JOB_ID INT(5),
    -> JOB_TITLE VARCHAR(10),
    -> MIN_SALARY VARCHAR(10),
    -> MAX_SALARY VARCHAR(10) CHECK(MAX_SALARY<=25000)
    -> );
  ```  
#### 7. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that no countries except Italy, India and China will be entered in the table.
```sql
mysql> CREATE TABLE IF NOT EXISTS countries1(
    -> COUNTRY_ID VARCHAR(5),
    -> COUNTRY_NAME ENUM('INDIA', 'ITALY', 'CHINA'));
```
#### 8. Write a SQL statement to create a table named job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that the value against column end_date will be entered at the time of insertion to the format like '--/--/----'.
```sql
mysql> CREATE TABLE IF NOT EXISTS job_history(
    -> EMPLOYEE_ID DECIMAL(5,0) NOT NULL,
    -> START_DATE date NOT NULL,
    -> END_DATE date NOT NULL,
    -> CHECK (END_DATE LIKE '--/--/----'),
    -> JOB_ID varchar(5) NOT NULL,
    -> DEPARTMENT_ID DECIMAL(4,0) NOT NULL
    -> );
    ```
#### 9. Write a SQL statement to create a table named countries including columns country_id,country_name and region_id and make sure that no duplicate data against column country_id will be allowed at the time of insertion.
```sql
mysql> CREATE TABLE IF NOT EXISTS COUNTRIES2(
    -> COUNTRY_ID VARCHAR(10) NOT NULL,
    -> COUNTRY_NAME VARCHAR(10) NOT NULL,
    -> REGION_ID INT NOT NULL,
    -> UNIQUE(COUNTRY_ID)
    -> );
```
#### 10. Write a SQL statement to create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.
```sql
mysql> CREATE TABLE IF NOT EXISTS jobS11(
    -> job_id int NOT NULL,
    -> job_title varchar(20) NOT NULL DEFAULT ' ',
    -> min_salary bigint(10) DEFAULT 8000,
    -> max_salary int(11) DEFAULT NULL
    -> );
```
#### 11. Write a SQL statement to create a table named countries including columns country_id, country_name and region_id and make sure that the country_id column will be a key field which will not contain any duplicate data at the time of insertion.
```sql
mysql> create table countries(
    -> country_id varchar(10),
    -> country_name varchar(20),
    -> region_id int(5),
    -> PRIMARY KEY(country_id)
    -> );
```
#### 12. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the column country_id will be unique and store an auto incremented value.
```sql
mysql> create table if not exists countries(
    -> country_id int(10) NOT NULL AUTO_INCREMENT,
    -> country_name varchar(20),
    -> region_id int(5),
    -> PRIMARY KEY(country_id)
    -> );
    ```
#### 13. Write a SQL statement to create a table countries including columns country_id, country_name and region_id and make sure that the combination of columns country_id and region_id will be unique.
```sql
mysql> create table if not exists countries(
    -> country_id int(10) NOT NULL,
    -> country_name varchar(20) NOT NULL,
    -> region_id int(5) NOT NULL,
    -> PRIMARY KEY(country_id, region_id)
    -> );
```
#### 14. Write a SQL statement to create a table job_history including columns employee_id, start_date, end_date, job_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key column job_id contain only those values which are exists in the jobs table.
```
Here is the structure of the table jobs;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```
```sql
mysql> CREATE TABLE IF NOT EXISTS jobs_history(
    -> employee_id int(5) NOT NULL,
    -> start_date date NOT NULL,
    -> end_date date NOT NULL,
    -> job_id varchar(10) NOT NULL,
    -> department_id varchar(10) NOT NULL,
    -> FOREIGN KEY (job_ID) REFERENCES jobs(JOBS_ID)
    -> );
```
#### 15. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion and the foreign key columns combined by department_id and manager_id columns contain only those unique combination values, which combinations are exists in the departments table.
```
Assume the structure of departments table below.

+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | NO   | PRI | 0       |       |
| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+
```
```sql
mysql> create table if not exists employees(
    ->     employee_id int(5) NOT NULL,
    ->     first_name varchar(10) NOT NULL,
    ->      last_name varchar(10) NOT NULL,
    ->     email varchar(20) NOT NULL,
    ->      phone_number VARCHAR(10) NOT NULL,
    ->      hire_date date NOT NULL,
    ->      job_id int(5) NOT NULL,
    ->      salary int(10) NOT NULL,
    ->     commission decimal(4,0) NOT NULL,
    ->     manager_id decimal(6,0) NOT NULL,
    ->      department_id decimal(4,0) NOT NULL,
    ->     FOREIGN KEY(department_id) REFERENCES departments(department_id),
    ->     FOREIGN KEY(manager_id) REFERENCES departments(manager_id)
    ->      );
```

#### 16. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, email, phone_number hire_date, job_id, salary, commission, manager_id and department_id and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column department_id, reference by the column department_id of departments table, can contain only those values which are exists in the departments table and another foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables.

*"A foreign key constraint is not required merely to join two tables. For storage engines other than InnoDB, it is possible when defining a column to use a REFERENCES tbl_name(col_name) clause, which has no actual effect, and serves only as a memo or comment to you that the column which you are currently defining is intended to refer to a column in another table." - Reference dev.mysql.com*
```
Assume that the structure of two tables departments and jobs.

+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | YES  |     | NULL    |       |

| LOCATION_ID     | decimal(4,0) | YES  |     | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```
```sql
mysql> create table if not exists employees(
    ->      employee_id int(10) NOT NULL PRIMARY KEY,
    ->      first_name varchar(10),
    ->      last_name varchar(10),
    ->      email varchar(10) NOT NULL,
    ->      phone_number varchar(10) NOT NULL,
    ->      hire_date date NOT NULL,
    ->      job_id varchar(10) NOT NULL,
    ->      salary int(10),
    ->      commission decimal(3,0),
    ->      manager_id decimal(6,0),
    ->      department_id decimal(4,0) NOT NULL,
    ->      FOREIGN KEY(department_id) REFERENCES departments(department_id),
    ->      FOREIGN KEY(job_id) REFERENCES jobs(JOBS_ID)
    ->      );
```
#### 17. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON UPDATE CASCADE action allows you to perform cross-table update and ON DELETE RESTRICT action reject the deletion. The default action is ON DELETE RESTRICT.
```
Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs (
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY,
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ',
MIN_SALARY decimal(6,0) DEFAULT 8000,
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```
```sql
mysql> create table if not exists employees(
    -> employee_id int(5) NOT NULL PRIMARY KEY,
    -> first_name varchar(10) NOT NULL,
    -> last_name varchar(10) NOT NULL,
    -> job_id int(11) NOT NULL,
    -> salary int(10) NOT NULL,
    -> FOREIGN KEY(job_id) REFERENCES jobs(job_id)
    -> );
```
#### 18. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE CASCADE that lets you allow to delete records in the employees(child) table that refer to a record in the jobs(parent) table when the record in the parent table is deleted and the ON UPDATE RESTRICT actions reject any updates.
```
Assume that the structure of the table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs (
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY,
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ',
MIN_SALARY decimal(6,0) DEFAULT 8000,
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```
```sql
mysql> create table if not exists employees1(
    -> employee_id int(5) NOT NULL PRIMARY KEY,
    -> first_name varchar(10) NOT NULL,
    -> last_name varchar(10) NOT NULL,
    -> job_id int(11) NOT NULL,
    -> salary int(10) NOT NULL,
    -> FOREIGN KEY(job_id) REFERENCES jobs1(job_id) ON DELETE CASCADE ON UPDATE RESTRICT
    -> );
```
#### 19. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE SET NULL action will set the foreign key column values in the child table(employees) to NULL when the record in the parent table(jobs) is deleted, with a condition that the foreign key column in the child table must accept NULL values and the ON UPDATE SET NULL action resets the values in the rows in the child table(employees) to NULL values when the rows in the parent table(jobs) are updated.
```
Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs (
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY,
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ',
MIN_SALARY decimal(6,0) DEFAULT 8000,
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```
```sql
mysql>  create table if not exists employees2(
    -> employee_id int(5) NOT NULL,
    -> first_name varchar(10) NOT NULL,
    -> last_name varchar(10) NOT NULL,
    -> job_id int(11) NOT NULL,
    -> salary int(10) NOT NULL,
    -> PRIMARY KEY(employee_id),
    -> FOREIGN KEY(job_id) REFERENCES job2(job_id) ON DELETE SET NULL ON UPDATE SET NULL
    -> );
```
#### 20. Write a SQL statement to create a table employees including columns employee_id, first_name, last_name, job_id, salary and make sure that, the employee_id column does not contain any duplicate value at the time of insertion, and the foreign key column job_id, referenced by the column job_id of jobs table, can contain only those values which are exists in the jobs table. The InnoDB Engine have been used to create the tables. The specialty of the statement is that, The ON DELETE NO ACTION and the ON UPDATE NO ACTION actions will reject the deletion and any updates.
```
Assume that the structure of two table jobs and InnoDB Engine have been used to create the table jobs.

CREATE TABLE IF NOT EXISTS jobs (
JOB_ID integer NOT NULL UNIQUE PRIMARY KEY,
JOB_TITLE varchar(35) NOT NULL DEFAULT ' ',
MIN_SALARY decimal(6,0) DEFAULT 8000,
MAX_SALARY decimal(6,0) DEFAULT NULL
)ENGINE=InnoDB;

+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
```
```sql
mysql> CREATE TABLE employees3
    -> (
    -> employee_id INT(11) NOT NULL,
    -> first_name VARCHAR(10) NOT NULL,
    -> last_name VARCHAR(10) NOT NULL,
    -> job_id INT(11) NOT NULL,
    -> salary DECIMAL(6,0),
    -> PRIMARY KEY(employee_id),
    -> FOREIGN KEY(job_id) REFERENCES jobs3(job_id) ON DELETE NO ACTION ON UPDATE NO ACTION
    -> );
```

## ALTER

#### 1. Write a SQL statement to rename the table countries to country_new.
```sql
mysql> Rename table countries to country_new;
```
#### 2. Write a SQL statement to add a column region_id to the table locations.
```sql
mysql> alter table locations
    -> add column region_id int(5);
```
#### 3. Write a SQL statement to add a columns ID as the first column of the table locations.
```sql
mysql> alter table locations
    -> add column id int(5) first;
```
#### 4. Write a SQL statement to add a column region_id after state_province to the table locations.
```sql
mysql> alter table locations
    -> add column region_id int after state_province;
```
#### 5. Write a SQL statement change the data type of the column country_id to integer in the table locations.
```sql
mysql> alter table locations
    -> modify country_id int;
```
#### 6. Write a SQL statement to drop the column city from the table locations.
```sql
mysql> alter table locations
    -> drop column city;
```
#### 7. Write a SQL statement to change the name of the column state_province to state, keeping the data type and size same.
```sql
mysql> alter table locations
    -> change state_province state varchar(10);
```
#### 8. Write a SQL statement to add a primary key for the columns location_id in the locations table.
```sql
mysql> alter table locations
    -> add primary key(country_id);
```
#### 9. Write a SQL statement to add a primary key for a combination of columns location_id and country_id.
```sql
mysql> alter table locations
    -> add primary key(location_id,country_id);
```
#### 10. Write a SQL statement to drop the existing primary from the table locations on a combination of columns location_id and country_id.
```sql
mysql> alter table locations
    -> drop primary key;
```
#### 11. Write a SQL statement to add a foreign key on job_id column of job_history table referencing to the primary key job_id of jobs table.
```sql
	mysql> alter table job_history
    -> add FOREIGN KEY(job_id) REFERENCES jobs(job_id);
```
#### 12. Write a SQL statement to add a foreign key constraint named fk_job_id on job_id column of job_history table referencing to the primary key job_id of jobs table.
```sql
mysql> alter table job_history
    -> ADD CONSTRAINT fk_job_id FOREIGN KEY(job_id) REFERENCES jobs(job_id);
```
#### 13. Write a SQL statement to drop the existing foreign key fk_job_id from job_history table on job_id column which is referencing to the job_id of jobs table.
```sql
mysql> alter table job_history
    -> drop FOREIGN KEY fk_job_id;
```
#### 14. Write a SQL statement to add an index named indx_job_id on job_id column in the table job_history.
```sql
mysql> alter table job_history
    -> add INDEX indx_job(job_id);
```
### 15. Write a SQL statement to drop the index indx_job_id from job_history table.
```sql
mysql> alter table job_history
    -> drop INDEX indx_job;
```
