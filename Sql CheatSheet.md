# SQL Database

## Create Database
```
create database databasename;
```
## List All Databases
```
show databases;
```
## Current Database
```
select database();
```
## To Use A Database
```
use databasename;
```
## Deleting Database
```
drop database databasename;
```
## Deleting Database If It Exists
```
drop database if exists databasename;
```

# SQL Table

## Creating Table
```
create table tablename(column1 datatype , column2 datatype, column3 datatype ,primary key (column1));
```
## Verifying Table Is Created or Not
```
desc tablename
```
## Creating Tables If The Not Exist
```
create table if not exists tablename(column1 datatype, column2 datatype, primary key(column1));
```
## List All Tables
```
show tables;
```
## Rename Table
```
rename table oldtablename to newtablename;
```
## Empty The Contents Inside A Table
``` 
truncate table tablename
```