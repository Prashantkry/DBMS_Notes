create database school;
create database if not exists school;

create database if not exists college;
drop database if exists college;

show databases;

use school;

create table student (
	id int primary key,
    name varchar(50),
    age int not null
);

insert into student values (1,"sara",26);
insert into student values (2,"Prashant",26.5);

select * from student;

show tables;

create table teacher(
	id int primary key,
    nameT varchar(50),
    sub varchar(50)
);

insert into teacher values(100,'sachin','cricket');
insert into teacher (id,nameT,sub) values (200,'arjun',19),(300,'sara',26),(400,'anjali',56);

select * from teacher;

drop table if exists teacher;

-- Q1 create a database for your company named XYZ.
	-- create a table inside this db tp store employee info (id,name and salary)
    -- Add following info in DB : 1,"adam",25000 | 2,"bob",30000  |  3,"casey",40000
    -- Select and view all your table data.

create database if not exists xyz;
use xyz;
create table employee (
	id int primary key,
    name varchar(50),
    salary int
);

insert into employee (id,name,salary) values (1,'adam',25000),
(2,"bob",30000),(3,"casey",40000);

insert into employee value (1,'adam',250000);

select * from employee;

-- unique
create table item(
	name varchar(50) primary key unique
);
insert into item value('onion');
select * from item;

-- default 
create table if not exists emp(
	id int,
    salary int default 24000
);
insert into emp (id) values(20);
select * from emp;

-- check 
create table city(
	id int primary key,
    city varchar(50),
    age int,
    constraint ageCheck check (age>=18 and city ="mumbai")
); 
insert into city value(31,"mumbai",40);
select * from city;


drop database if exists college;

create database if not exists college;
use college;
create table if not exists student(
	id int primary key ,
    name varchar(50),
    marks int not null,
    grade varchar(1),
    city varchar(50)
);
insert into student values (101,"anil",98,"C","Pune"),
(102,"bhumika",91,"D","ranchi"),
(13,"sam",31,"A","delhi"),
(104,"ram",81,"B","ranchi"),
(105,"fiza",71,"C","mumbai"),
(106,"sara",99,"A","Patna");

drop table if exists student;

insert into student value(107,"sara",100,"O","Bihar");
select * from student;
select name,grade from student;
select distinct city from student;

-- where 
select * from student where marks > 85 and city = "Patna"; 
select * from student where marks+10 > 100;
select * from student where marks+1 > 100 and name = 'sara';
select * from student where marks+10 > 100 and id <103;
select * from student where marks between 80 and 90;
select * from student where name = "sara" and city in ("patna","bihar");
select * from student where name = "sara" and city not in ("bihar");
select * from student where marks <80 limit 3;
select * from student order by city asc;
select * from student order by marks desc ;
select * from student order by marks desc limit 3;

-- Aggregate functions
-- It perform calculations on set of value & return single values
select max(marks) from student;
select min(marks) from student;
select avg(marks) from student;
select sum(marks) from student;
select count(marks) from student;


-- group by clause 
select city from student group by city;
select city,name from student group by city,name;
select city, count(marks) from student group by city;
select grade,count(name) from student group by grade order by grade desc limit 4;

-- Q. Write a query to find avg marks in each city in asc order?
select city ,avg(marks) from student group by city order by city;
select city ,avg(marks) from student group by city order by avg(marks);


-- having clause -> used when want to apply conditions on group by
select city,count(name) from student group by city having max(marks) > 80;

-- Q having and where together.
select city,count(name) from student where grade = 'A' group by city having max(marks) >80 order by city asc;
