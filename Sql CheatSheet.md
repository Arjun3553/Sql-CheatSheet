# SQL Database

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

## SQL Limit Clause

sql limit clause is used to restrict the number of rows returned from by a select statement.
offset clause is used to get the record that is next to the previous record

```
select * from tablename where (condition) limit value offset value;
```
