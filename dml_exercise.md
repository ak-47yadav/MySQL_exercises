#  DML EXERCISE

#### 1. Write a SQL statement to insert a record with your own value into the table countries against each columns.

````
Here in the following is the structure of the table countries.

+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(2)    | YES  |     | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
````
````SQL
Answer:

   mysql> insert into country values('1', 'India', 5);
````

#### 2. Write a SQL statement to insert one row into the table countries against the column country_id and country_name.
````
Here in the following is the structure of the table countries.

+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(2)    | YES  |     | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
````
````sql
Answer:
 mysql> insert into country (COUNTRY_ID, COUNTRY_NAME) values('3', 'UK');
````

#### 3. Write a SQL statement to create duplicate of countries table named country_new with all structure and data.
````
Here in the following is the structure of the table countries.

+--------------+---------------+------+-----+---------+-------+
| Field        | Type          | Null | Key | Default | Extra |
+--------------+---------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(2)    | YES  |     | NULL    |       |
| COUNTRY_NAME | varchar(40)   | YES  |     | NULL    |       |
| REGION_ID    | decimal(10,0) | YES  |     | NULL    |       |
+--------------+---------------+------+-----+---------+-------+
````
````sql
mysql> create table if not exists country_new
    -> AS SELECT * FROM country;
````

#### 4. Write a SQL statement to insert NULL values against region_id column for a row of countries table.

````sql
mysql> insert into country (COUNTRY_ID, COUNTRY_NAME) values('4', 'USA');
````
#### 5. Write a SQL statement to insert 3 rows by a single insert statement.
````sql
mysql> insert into country values('5', 'Korea', 45), ('6', 'Russia', 56), ('7', 'Italy', 23);
````
#### 6. Write a SQL statement insert rows from country_new table to countries table.
````
Here is the rows for country_new table. Assume that, the countries table is empty.

+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
| C0001      | India        |      1001 |
| C0002      | USA          |      1007 |
| C0003      | UK           |      1003 |
+------------+--------------+-----------+
````
````sql
mysql> insert into country
   -> select * from country_new;
````
#### 7. Write a SQL statement to insert one row in jobs table to ensure that no duplicate value will be entered in the job_id column.
````sql
mysql> create table if not exists jobs(
    -> JOB_ID varchar(10),
    -> Salary int(10),
    -> MIN_SALARY decimal(6,0),
    -> PRIMARY KEY(JOB_ID)
    -> );
    mysql> INSERT INTO jobs VALUES('1', 20000, 15000);

    mysql> DESC JOBS;
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI | NULL    |       |
| Salary     | int(10)      | YES  |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
````
#### 8. Write a SQL statement to insert one row in jobs table to ensure that no duplicate value will be entered in the job_id column.
````sql
mysql> create table if not exists jobs(
    -> JOB_ID varchar(10),
    -> Salary int(10),
    -> MIN_SALARY decimal(6,0),
    -> PRIMARY KEY(JOB_ID)
    -> );
    mysql> INSERT INTO jobs VALUES('1', 20000, 15000);

    mysql> DESC JOBS;
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI | NULL    |       |
| Salary     | int(10)      | YES  |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
````
#### 9. Write a SQL statement to insert a record into the table countries to ensure that, a country_id and region_id combination will be entered once in the table.
````sql
mysql> create table if not exists countries(
    -> COUNTRY_ID VARCHAR(10),
    -> COUNTRY_NAME VARCHAR(10),
    -> REGION_ID DECIMAL (6,0),
    -> PRIMARY KEY(COUNTRY_ID, REGION_ID)
    -> );
    mysql> DESC COUNTRIES;
+--------------+--------------+------+-----+---------+-------+
| Field        | Type         | Null | Key | Default | Extra |
+--------------+--------------+------+-----+---------+-------+
| COUNTRY_ID   | varchar(10)  | NO   | PRI | NULL    |       |
| COUNTRY_NAME | varchar(10)  | YES  |     | NULL    |       |
| REGION_ID    | decimal(6,0) | NO   | PRI | NULL    |       |
+--------------+--------------+------+-----+---------+-------
````

#### 10. Write a SQL statement to insert rows into the table countries in which the value of country_id column will be unique and auto incremented.
````sql
mysql> CREATE TABLE IF NOT EXISTS COUNTRIES(
    -> COUNTRY_ID int(10) AUTO_INCREMENT,
    -> COUNTRY_NAME VARCHAR(10),
    -> REGION_ID DECIMAL(6,0),
    -> PRIMARY KEY(COUNTRY_ID)
    -> );
````
#### 11. Write a SQL statement to insert records into the table countries to ensure that the country_id column will not contain any duplicate data and this will be automatically incremented and the column country_name will be filled up by 'N/A' if no value assigned for that column.
````sql
mysql> CREATE TABLE IF NOT EXISTS countries (
    -> COUNTRY_ID integer NOT NULL AUTO_INCREMENT PRIMARY KEY,
    -> COUNTRY_NAME varchar(40) NOT NULL DEFAULT 'N/A',
    -> REGION_ID integer NOT NULL
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> INSERT INTO countries VALUES(23,'Japan',1);
Query OK, 1 row affected (0.01 sec)

mysql> insert into countries(region_id) values(34);
Query OK, 1 row affected (0.01 sec)

mysql> select * from countries;
+------------+--------------+-----------+
| COUNTRY_ID | COUNTRY_NAME | REGION_ID |
+------------+--------------+-----------+
|         23 | Japan        |         1 |
|         24 | N/A          |        34 |
+------------+--------------+-----------+
````
#### 12. Write a SQL statement to insert rows in the job_history table in which one column job_id is containing those values which are exists in job_id column of jobs table.
````sql
mysql> create table if not exists jobs(
    -> JOB_ID INT(10) NOT NULL PRIMARY KEY,
    -> SALARY VARCHAR(10)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> CREATE TABLE IF NOT EXISTS JOB_HISTORY(
    -> JOB_ID INT(10) NOT NULL,
    -> AGE INT(5),
    -> FOREIGN KEY(JOB_ID) REFERENCES jobs(JOB_ID)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> insert into jobs values( 450, '20000'), (550, '17000'), (650, '18500');
mysql> select * from jobs;
+--------+--------+
| JOB_ID | SALARY |
+--------+--------+
|    450 | 20000  |
|    550 | 17000  |
|    650 | 18500  |
+--------+--------+
mysql> insert into job_history values( 450, 20) (550,25) (650,45);
Query OK, 1 row affected (0.00 sec)

mysql> select * from job_history;
+--------+------+
| JOB_ID | AGE  |
+--------+------+
|    450 |   20 |
|    550 |   25 |
|    650 |   45 |
+--------+------+
````
#### 13. Write a SQL statement to insert rows into the table employees in which a set of columns department_id and manager_id contains a unique value and that combined values must have exists into the table departments.
````sql
mysql> create table if not exists departments(
    -> department_id int(10) NOT NULL PRIMARY KEY,
    -> manager_id int(5) UNIQUE,
    -> types_id varchar(10)
    -> );

    mysql> create table if not exists employees(
    -> department_id int(10) NOT NULL,
    -> manager_id int(5),
    -> age int(2),
    -> FOREIGN KEY(department_id) REFERENCES departments(department_id),
    -> FOREIGN KEY(manager_id) REFERENCES departments(manager_id)
    -> );

mysql> desc employees;
+---------------+---------+------+-----+---------+-------+
| Field         | Type    | Null | Key | Default | Extra |
+---------------+---------+------+-----+---------+-------+
| department_id | int(10) | NO   | MUL | NULL    |       |
| manager_id    | int(5)  | YES  | MUL | NULL    |       |
| age           | int(2)  | YES  |     | NULL    |       |
+---------------+---------+------+-----+---------+-------+
````

#### 14. Write a SQL statement to insert rows into the table employees in which a set of columns department_id and job_id contains the values which must have exists into the table departments and jobs.
````sql
mysql> CREATE TABLE IF NOT EXISTS departments1 (
    -> DEPARTMENT_ID integer NOT NULL UNIQUE,
    -> DEPARTMENT_NAME varchar(10) NOT NULL,
    -> MANAGER_ID integer DEFAULT NULL,
    -> LOCATION_ID integer DEFAULT NULL,
    -> PRIMARY KEY (DEPARTMENT_ID)
    -> );

    mysql> CREATE TABLE IF NOT EXISTS jobs1 (
    -> JOB_ID integer UNIQUE PRIMARY KEY,
    -> JOB_TITLE varchar(10) NOT NULL DEFAULT ' ',
    -> MIN_SALARY decimal(4,0) DEFAULT 8000,
    -> MAX_SALARY decimal(8,0) DEFAULT 20000
    -> );

    mysql> CREATE TABLE IF NOT EXISTS employees1 (
    -> EMPLOYEE_ID integer NOT NULL PRIMARY KEY,
    -> FIRST_NAME varchar(20) DEFAULT NULL,
    -> LAST_NAME varchar(25) NOT NULL,
    -> DEPARTMENT_ID integer DEFAULT NULL,
    -> FOREIGN KEY(DEPARTMENT_ID)
    -> REFERENCES  departments(DEPARTMENT_ID),
    -> JOB_ID integer NOT NULL,
    -> FOREIGN KEY(JOB_ID)
    -> REFERENCES  jobs(JOB_ID),
    -> SALARY decimal(8,2) DEFAULT NULL
    -> );

    mysql> desc departments1;
+-----------------+-------------+------+-----+---------+-------+
| Field           | Type        | Null | Key | Default | Extra |
+-----------------+-------------+------+-----+---------+-------+
| DEPARTMENT_ID   | int(11)     | NO   | PRI | NULL    |       |
| DEPARTMENT_NAME | varchar(30) | NO   |     | NULL    |       |
| MANAGER_ID      | int(11)     | YES  |     | NULL    |       |
| LOCATION_ID     | int(11)     | YES  |     | NULL    |       |
+-----------------+-------------+------+-----+---------+-------+

mysql> desc jobs1;
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | int(11)      | NO   | PRI | NULL    |       |
| JOB_TITLE  | varchar(35)  | NO   |     |         |       |
| MIN_SALARY | decimal(6,0) | YES  |     | 8000    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | 20000   |       |
+------------+--------------+------+-----+---------+-------+

mysql> desc employees1;
+---------------+--------------+------+-----+---------+-------+
| Field         | Type         | Null | Key | Default | Extra |
+---------------+--------------+------+-----+---------+-------+
| EMPLOYEE_ID   | int(11)      | NO   | PRI | NULL    |       |
| FIRST_NAME    | varchar(20)  | YES  |     | NULL    |       |
| LAST_NAME     | varchar(25)  | NO   |     | NULL    |       |
| DEPARTMENT_ID | int(11)      | YES  | MUL | NULL    |       |
| JOB_ID        | int(11)      | NO   | MUL | NULL    |       |
| SALARY        | decimal(8,2) | YES  |     | NULL    |       |
+---------------+--------------+------+-----+---------+-------+

mysql> insert into departments1 values(10, 'IT', 5, 4), (12, 'CS', 6, 3);

mysql> insert into jobs1 values(10, 'prog', 5000, 15000);

mysql> insert into employees1 values( 25, 'Aksh', 'yadaa', 12, 10, 15000);

mysql> select * from departments1;
+---------------+-----------------+------------+-------------+
| DEPARTMENT_ID | DEPARTMENT_NAME | MANAGER_ID | LOCATION_ID |
+---------------+-----------------+------------+-------------+
|            10 | IT              |          5 |           4 |
|            12 | CS              |          6 |           3 |
+---------------+-----------------+------------+-------------+

mysql> select * from jobs1;
+--------+-----------+------------+------------+
| JOB_ID | JOB_TITLE | MIN_SALARY | MAX_SALARY |
+--------+-----------+------------+------------+
|     10 | prog      |       5000 |      15000 |
+--------+-----------+------------+------------+

mysql> SELECT * FROM employees;
+-------------+------------+-----------+---------------+--------+----------+
| EMPLOYEE_ID | FIRST_NAME | LAST_NAME | DEPARTMENT_ID | JOB_ID | SALARY   |
+-------------+------------+-----------+---------------+--------+----------+
|         25  | Aksh       | yadaa     |            12 |   10   | 15000.00 |
+-------------+------------+-----------+---------------+--------+----------+
````
