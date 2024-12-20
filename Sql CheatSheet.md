# MySQL Cheatsheet

#---------------------------------------------------------------------------------------------#

# SQL Database

Sql or Relational Database is used to store and modify the data objects that are related to one another.

## Create Database

to create a database

```
create database databasename;
```

## List All Databases

to list all databases

```
show databases;
```

## Current Database

to show the current selected database

```
select database();
```

## To Use A Database

to select a database

```
use databasename;
```

## Deleting Database

to delete a database

```
drop database databasename;
```

## Deleting Database If It Exists

to delete a database if it exists

```
drop database if exists databasename;
```

# SQL Table

Tables are database objects used to store the data in rows and columns format.

## Creating Table

to create a table

```
create table tablename(column1 datatype constaints, column2 datatype constaints, column3 datatype constaints ,primary key (column1));
```

## Verifying Table Is Created or Not

to verify if the table is create and to view the structure of the database

```
desc tablename
```

## Creating Tables If The Not Exist

to create a table if it not exists in the database

```
create table if not exists tablename(column1 datatype, column2 datatype, primary key(column1));
```

## List All Tables

to view the list of tables

```
show tables;
```

## Rename Table

to rename the table

```
rename table oldtablename to newtablename;
```

## Empty The Contents Of A Table

to empty the contents of the table

```
truncate table tablename
```

## Clone Tables - Simple Cloning

copy all the data from one table to another along with its structure except extras

```
create table newtablename select * from tablename;
```

## Clone Tables - Shallow Cloning

only copy the structure from one table to another with extra

```
create table newtablename like tablename;
```

## Clone Tables - Deep Cloning

clone all the data and structure along with extra from one table to another

```
create table newtablename like tablename;
insert into newtablename select * from tablename;
```

## Create Temporary Tables

temporary tables are tables that is used to store temporary data and are deleted once the client session is closed

```
create temporary table tablename (column1 datatype constaints, column2 datatype constaints, column3 datatype constaints, primary key(column1));
```

## Drop Temporary Tables

to delete the temporary tables

```
drop temporary table tablename;
```

## Alter Table - Add Column

to alter the table by adding a new column

```
alter table tablename add columnname datatype constaints;
```

## Alter Table - Drop Column

to alter the table by removing a column

```
alter table tablename drop column columnname constaints;
```

## Alter Table - Add Primary Key

alter the table by adding a new primary key

```
alter table tablename add constraint constraintname primary key(column1);
```

## Alter Table - Drop Primary Key

alter the table by dropping a primary key

```
alter table tablename drop primary key;
```

## Alter Table - Add Constraint

alter table by adding a constraint

```
alter table tablename add constraint constraintname unique (column1);
```

## Alter Table - Drop Constraint

alter table by removing a constraint

```
alter table tablename drop constraint constraintname;
```

## Alter Table - Rename Column

alter table by renaming the columnname

```
alter table tablename rename column oldcolumnname to newcolumnname;
```

## Alter Table - Modify Column

alter table by modifying the datatype of column

```
alter table tablename modify column columnname datatype constaints;
```

## Drop Table

to drop a table

```
drop table tablename;
```

## Drop Table If Exists

to drop a table if it exists

```
drop table if exists tablename;
```

## Delete Table

to delete all rows of a table without changing the structure of the table

```
delete from tablename;
```

## Delete Table - Using Where Clause

to delete a row based on where clause

```
delete from tablename where conditon;
```

## Check Constraints

to check the validity of the data that is entered into a table column

```
alter table tablename modify column columnname datatype check(condition);
```

## To Check All Constraints

to check all the constraints of a table

```
show create table tablename;
```

# SQL Queries

## Insert Query

to insert a row into a table column

```
insert into tablename (column1, column2, column3) values (value1, value2, value3);
```

another variation without column. Ensure values are in the same order as the columns in the table

```
insert into tablename values (value1, value2, value3);
```

## Insert Into - Select Query

to insert data from a table to another table using select query

```
insert into newtablename select * from tablename;
```

with using where clause

```
insert into newtablename select column1, column2 from tablename where (condition);
```

## Insert Into - Table Query

to insert data from a table to another table using table query

```
insert into newtablename table tablename;
```

## Select Query

to select query is used to fetch data from a table

```
select * from tablename;
```

```
select column1, column2 from tablename;
```

select query based on where clause

```
select column1, column2 from tablename where (condition);
```

## Select Query - Alias

to fetch data from a table using alias

```
select columnname as aliasname from tablename;
```

## Select Query - Concat()

to fetch data from a table using concat and alias

```
select concat(column1, column2) as aliasname, column3 from tablename;
```

## Update Query

update query is used to modify the existing records in a table

```
update table tablename set column1=value1, column2=value2 where (condition);
```

## Delete Query

to delete a record from a table based on where clause, if there is no where clause all the records will be deleted

```
delete from tablename where (condition);
```

```
delete from tablename ;
```

## Sorting Results

order by clause is used to sort the results in ascending or descending order, by default all records will be sorted ascending

```
select * from tablename where (condition) order by columnname [asc/desc];
```

## Sorting Results - Custom Order

to sort the results in a custom order using case

```
select * from tablename where (condition) order by (case columnname  when columnvalue then ordernumber) [asc/desc];
```

# SQL Views

Sql views are virtual table that is stored in the database with an associated name.

## Create Views

to create a view in a database

```
create view view_name as select * from tablename where (condition);
```

with **check option** - to ensure all the update and insert statements satify the conditions specified by the where clause

```
create view view_name as select * from tablename where (condition) with check option;
```

## List All Views

to list all views in a database

```
select table_schema, table_name from information_schema.views where table_schema like 'database_name';
```

## Update Views

to update a view in a database

```
update viewname set columnN = valueN where (condition);
```

## Drop Views

to drop a view from a database

```
drop view view_name;
```

## Delete Views

to delete a particular record from the view

```
delete from view_name where (condition);
```

# SQL Operators and Clauses

## SQL Where clause

where clause is used to filter the results obtained from the dml query such as select, update,delete.

```
select * from tablename where (condition);
```

```
update tablename set columnN = valueN where (condition);
```

```
delete from tablename where (condition);
```

## SQL Limit & Offset Clause

sql limit clause is used to restrict the number of rows returned from by a select statement.
offset clause is used to get the record that is next to the previous record

```
select * from tablename where (condition) limit value offset value;
```

## SQL Distinct clause

distinct keyword is used to get the unique records from a table

```
select distinct column1, column2, columnN from tablename where (condition) order by columnN [asc/desc];
```

## SQL Distinct clause - count

count is used to get the number of records returned by the select query

```
select count(distinct column1, column2, columnN) from tablename where (condition) order by columnN [asc/desc];
```

## SQL Group by clause

group by clause is used to arrange identical data into groups and should be used along with aggregate functions

## aggregate functions

sum(), min(), max(), count(), avg()

```
select column1, aggregate_function(columnN) from tablename group by columnN;
```

or

```
select column1, columnN from tablename group by column1, columnN;
```

## SQL Group by clause - with having and order by

having is used to filter the grouped data in a table based on a specific criteria

```
select column1 from tablename group by column1 having (condition) order by columnN [asc/desc];
```

## SQL AND & OR & NOT

conjunctive operators are used to combine two or more conditions in an sql statement

```
select * from tablename where not((condition) and (condition1) or (condition2));
```

## SQL Boolean Operators

a boolean is a universal datatype that is used to store true or false value

```
create table tablename column1 datatype constraint,columnN boolean constraint;
```

dynamic insertion of boolean value based on the color while insertion is performed

```
insert into tablename values(column1 value, column2 value, column3 value, case when "column3 value" = "something" then "some value" else 0 end);
```

## SQL Like Operator

like operator is used to get the values from the table based on a specific pattern

```
select * from tablename where columnN like "pattern";
```

## pattern

"b%" -> return any value that has b as the second letter

"%b%" -> return any value that has b anywhere in the text

"%b" -> return any value that ends with b

"b%" - > return any value that starts with b

## SQL In Operator

In operator is used to specify multiple values or sub query in the where clause.

```
select * from tablename where columnN in(value1, value2, value3);
```

also In operator is used with Not operator

```
select * from tablename where columnN not in (value1, value2, value3);
```

## SQL ANY and ALL Operator

ANY and ALL operator are used to perform comparison between a single value and range of values retured by the sub query
the ANY and ALL operators must be preceded by a standard comparison operator i.e. >, >=, <, <=, =, <>, != and followed by a subquery. The main difference between ANY and ALL is that ANY returns true if any of the subquery values meet the condition whereas ALL returns true if all of the subquery values meet the condition.

```
select * from tablename where columnN > Any(subquery);
```

subquery = select columnN from tablename where (condition);

## SQL Exists Operator

The SQL EXISTS operator is used to verify whether a particular record exists in a MySQL table.

```
select * from tablename where exists(condition);
```

subquery = select columnN from newtablename where tablename.columnN = newtablename.columnN [and/or/not] (condition);

## SQL CASE Operator

The SQL Case statement is a conditional statement that help us to make decision based on set of conditions.

```
select column1, column2, (case when conditionN then valueN else valueM end) as aliasname from tablename;
```

## SQL NOT Operator

SQL NOT is a logical operator/connective used to negate a condition or boolean expression in a WHERE clause.

```
select * from tablename where not (condition);
```

## SQL Not Equal Operator

The SQL NOT EQUAL operator is used to compare two values and return true if they are not equal.
<> or != the main difference between the two is that <> follows the ISO standard, but != doesn't.

```
select * from tablename where (condition);
```

condition - columnN <> valueN

## SQL Is Null Operator

The SQL IS NULL operator is used to check whether a value in a column is NULL. It returns true if the column value is NULL; otherwise false.

```
select * from tablename where columnN Is Null;
```

## SQL Is Not Null Operator

The SQL IS NOT NULL operator is used to filter data by verifying whether a particular column has a not-null values. This operator can be used with SQL statements such as SELECT, UPDATE, and DELETE.

```
select * from tablename where columnN IS NOT NULL;
```

```
update tablename set columnN = valueN where columnN IS NOT NULL;
```

```
delete from tablename where columnN IS NOT NULL;
```

## SQL Not Null Constraint

The NOT NULL constraint in SQL is used to ensure that a column in a table doesn't contain NULL (empty) values, and prevent any attempts to insert or update rows with NULL values.

```
Alter table tablename modify column columnN datatype constraints
```

constraint - Not Null

## SQL Between Operator

The BETWEEN operator is a logical operator in SQL, that is used to retrieve the data within a specified range.

```
select * from tablename where columnN between valueN AND valueM;
```

Between with IN Operator

```
select * from tablename where columnN between valueN AND valueM AND columnM in (valueQ, valueW, valueE);
```

## SQL Union Operator

The SQL Union operator is used to combine data from multiple tables by eliminating duplicate rows and return them as a single table.

```
select * from tablename where (condition) union select * from newtablename where (condition);
```

## SQL Union All Operator

The SQL Union All operator is used to combine data from multiple tables by preserving duplicate rows and return them as a single table

```
select * from tablename where (condition) union all select * from newtablename where (condition);
```

the tables that are combined together should have the same number of columns

## SQL Intersect Operator

The SQL Intersect operator is used to combine common data from multiple tables and return them as a single set.

```
select column1, column2 from tablename intersect select column1, column2 from newtablename;
```

note : column1, column2 should be present in both the tables;

# SQL Joins

## SQL Using Joins

The SQL Joins operator is used to combine data from two or more tables in a database.

```
select column1, column2, columnN from tablename join newtablename;
```

### Types Of Joins

**Inner Join** - is the default implementation which retrieves all the records of the intersection of two tables.  
**Outer Join** - unlike inner join outer join retrieve all the records in the two tables.  
Outer Join - Left Join, Right Join, Full Join

**Left Join** - returns all the rows in the left table even if there is no match in the right table.  
**Right Join** - return all the rows in the right table even if there is no match in the left table.  
**Full Join** - return a row if there a match in any one of the two tables.

**Self Join** - is used to join the table to itself.  
**Cross Join** - return the cartesian product of the two tables.

## SQL Inner Join

The SQL Inner Join is used to retrieve all the records of intersection of two tables.

```
select tablename.column1, tablename.column2, newtablename.column3 from tablename inner join newtablename on tablename.columnN = newtablename.columnN;
```

## SQL Left Join

The SQL Left Join is used to retrieve all the records from the left table even if there is no match found in the right table.

```
select tablename.column1, tablename.column2, newtablename.column3 from tablename left join newtablename on tablename.columnN = newtablename.columnN;
```

## SQL Right Join

The SQL Right Join is used to retrieve all the records from the right table even if there is no match found in the left table.

```
select tablename.column1, tablename.column2, newtablename.column3 from tablename right join newtablename on tablename.columnN = newtablename.columnN;
```

## SQL Full Join

The SQL Full Join is used to retrieve the records that is present in either one table.

MySQL doesn't support full join but the same results can be achieved using left join union right join or vice versa.

```
select tablename.column1, tablename.column2, newtablename.column3 from tablename right join newtablename on tablename.columnN = newtablename.columnN
union
select tablename.column1, tablename.column2, newtablename.column3 from tablename left join newtablename on tablename.columnN = newtablename.columnN;
```

## SQL Cross Join

The SQL Cross Join is used to return the cartesian product of two tables.

```
select tablename.column1, newtablename.column2 from tablename cross join newtablename;
```

## SQL Self Join

The SQL Self Join is used to join the table to itself as if there were two tables.

```
select M.column1, M.column2, N.column3 from tablename M, tablename N where (condition);
```

# SQL Keys

## SQL Unique Key

The SQL Unique key does not allow the duplicate values to be present in a column of a table.

```
alter table tablename modify column columnname datatype unique;
```

## SQL Primary Key

The SQL Primary Key is a column that uniquely identifies each record of a database table.

```
create table tablename (
    columnName datatype primary key,
);
```

## SQL Composite Key

When the primary key is created on multiple fields of a table it is known as composite key.

```
create table tablename (
    column1 datatype constraints,
    column2 datatype constraints,
    columnN datatype constraints,
    primary key (column1, column2)
);
```

## SQL Candidate Key / Alternate Key

Those keys which can act as a primary key are called as candidate key, there can be only one primary key but n number of candidate keys.

## SQL Foreign Key

The SQL Foreign key is a column in one table that matches a primary key in another table allowing the connection between the two tables.

```
create table tablename (
    column1 datatype constraints,
    column2 datatype constraints,
    columnN datatype constraints,
    primary key (column1)
);

create table foreigntable(
    column1 datatype constraints,
    column2 datatype constraints,
    constraint constraintname
    foreign key (column2)
    references tablename(column1),
    primary key (column1)
);

```

# SQL Indexes

## SQL Index

The SQL Indexes are special lookup tables that are used to speed up the process of data retrieval.

```
create index indexname on tablename (columnname);
```

## Drop Index

The Drop Index is used to drop the index from the database table.

```
drop index indexname on tablename;
```

## Show Index

The Show Index is used to display the index present in a database table.

```
show index from tablename;
```

## Unique Index

The Unique Index is used to remove duplicate value in a table column.

```
create unique index on tablename (columnname);
```

## SQL Clustered Index

The SQL Clustered Index is a type of index that define the physical order in which the data is stored in the table.

## SQL Non Clustered Index

The Non Clustered Index is a type of index that creates a special table that contains the copy of indexed column along with the pointer that point to the actual data in the table.

## SQL Wildcards

The SQL Wildcards are special characters that is used to replace the characters in a string.

( % ) and ( \_ ) are the two wildcard characters.

```
select * from tablename where columnN like ("%_a");
```

## SQL Query - Order Of Execution

The typical order of execution of sql statements is :

1. from
2. join
3. where
4. group by
5. having
6. select
7. distinct
8. order by
9. limit / offset

## SQL Query - Grant And Revoke

Grant - provides privileges to users
Revoke - removes the privileges given to users

```
grant select , insert on databasename / databasename.tablename to 'username'@'hostname';
```

```
revoke select , insert on databasename / databasename.tablename from 'username'@'hostname';
```

to show all the grants of the users

```
show grants for 'username'@'hostname';
```

to grant all the privileges given to the users

```
grant all the privileges on databasename / databasename.tablename to 'username'@'hostname';
```

to revoke all the privileges given to the users

```
revoke all the privileges on databasename / databasename.tablename from 'username'@'hostname';
```

to create a new user

```
create user 'username'@'hostname' identified by 'password';
```

to remove the user

```
drop user 'username'@'hostname';
```

to show all the users

```
select user, host from mysql.user;
```

## SQL Query - Commit, Rollback, Savepoint

Commit - saves the work done in the transaction and make the changes permanent.

Rollback - is used to revert the database to the last committed state.

Savepoint - set points within transaction so that you can rollback later.

Commit

```
start transaction;
update tablename set column_name = value where (condition);
commit;
```

Rollback

```
start transaction;
delete from tablename where (condition);
rollback;
commit;
```

Savepoint

```
start transaction;
update tablename set column_name = value where (condition);
savepoint updateid;
delete from tablename where (condition);
savepoint deleteid;
rollback to savepoint_name;
commit;
```
