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


-- update 
update student set grade ="D" where grade ="A" and name = "sam";
update student set marks = 85 where marks = 99 and name ="sara";
update student set name = "saraT" where city = "Bihar";
update student set grade = "A" where marks between 80 and 90;
-- update all marks together by 1
update student set marks = marks + 1;

update student set marks =100 where name ="saraT" and city ="Bihar";
update student set name ="nayra" where name ="sara";
update student set marks = 33 where name ="anil";


set sql_safe_updates=0;

-- delete 
delete from student ; -- will delte complete data of table
delete from student where marks<=33;

select * from student;

-- Foreign key and primary key
create database university;
use university;
create table if not exists department(
	id int primary key,
    subject varchar(50)    
);
insert into department values (100,"sci"),
	(101,"math"),(102,"eng");
    
create table if not exists teacher(
	id int primary key,
    name varchar(50),
    departId int ,
    foreign key (departId) references department(id)
    on update cascade
    on delete cascade
);
insert into teacher values(201,"ram",100),(202,'sam',101),(203,'geeta',102);
drop table department;
drop table teacher;

select * from teacher;
select * from department;

update department set id = 110 where id = 105;



-- ALTER 
create table subjects(
	id int primary key,
    sub varchar(50),
    price int
);
insert into subjects values(1,'math',200),(2,'cse',299);

alter table subjects
add column quantity int not null default(0);

alter table subjects
modify column quantities varchar(2);

alter table subjects -- delete coln
drop column quantity;

update subjects quantity set quantities = 400 where sub = "math"; -- will not work as of varchar size but if it int type then got updated
update subjects price set price = 300 where sub = "cse";

alter table subjects -- change in coln name and type
change quantity quantities int;

alter table subjects -- change in coln type
modify column quantities int;
update subjects quantities set quantities=30 where sub="math";

-- change table name 
alter table subjects rename to subs;
alter table subs rename to subjects;

-- delte complete table data where drop delete the table itself.
truncate subjects;  -- or
truncate table subjects;

select * from subjects;
drop table subjects;

/*
-- Q practice questions  
1. In the groceries table change coln - name to fruitName 
2. Delete all fruits whose price is less than 200
3. Delete colm of price
*/
create database if not exists groceries;
use groceries;

create table if not exists fruits(
	id int not null primary key,
    fruitName varchar(30),
    quant int    
);
insert into fruits values (1,'mango',20),(2,'apple',30),(3,'grapesh',10);
insert into fruits value(4,'kiwi',4);

update fruits price set price = 200 where fruitName = "kiwi";
update fruits price set price = 100 where fruitName = "mango";
update fruits price set price = 350 where fruitName = "apple";
update fruits price set price = 120 where fruitName = "grapesh";

alter table fruits add column price int not null default 0;
alter table fruits change name fruitName varchar(40);
delete from fruits where price <=200;
alter table fruits drop column price;
drop table fruits;

select * from fruits;
set sql_safe_updates = 0;

create table if not exists vegetables(
	id int not null unique primary key,
    name varchar(20),
    foreign key (id) references fruits(id)
);

drop table if exists vegetables;
insert into vegetables values(2,'onion'),(4,'garlic');
insert into vegetables values(4,'chilli');
alter table vegetables add column price int;
update vegetables price set price=43 where id = 3;
select * from vegetables;


-- Joins  
select * from fruits inner join vegetables on vegetables.id = fruits.id;
select * from fruits left join vegetables on vegetables.id = fruits.id;
select * from fruits right join vegetables  on vegetables.id = fruits.id;
-- full joins 
select * from fruits left join vegetables on vegetables.id = fruits.id
union
select * from fruits right join vegetables on vegetables.id =  fruits.id;

-- Write a SQL commands to display left exclusive join
select * from fruits left join vegetables on vegetables.id = fruits.id where vegetables.id is null;
-- Write a SQL commands to display right excusive join 
select * from fruits right join vegetables on vegetables.id = fruits.id where fruits.id is null;

-- self join 
create table if not exists employee(
	id int primary key ,
    name varchar(30),
    managerId int
);
insert into employee values(101,"adam",103),(102,"sam",104),(103,"ram",null),(104,"aam",103);
select * from employee;
select * from employee as a join employee as b on a.id = b.managerId;
-- print manager name 
select a.id as a_Id, a.name as manager_Name, b.name from employee as a join employee as b on a.id =  b.managerId;

-- unions -> no dupliate  & union all -> with dupliate data
select * from employee 
union
select * from vegetables;

-- subquries  also it is dynamic 
select avg(price) from vegetables;  -- normal way 
select name , price from vegetables where price > 53.3333;
select name, price from vegetables where price > (select avg(price) from vegetables); -- subquries
select name, price from vegetables where price in (select price from vegetables where price %2=0);

/*	Q  Example from alias is must here
	Find max marks from the students of delhi
		step 1. find student of delhi
        step 2. find their max marks using sublist in step 1	
*/ 
create table if not exists student(
	id int not null primary key,
    name varchar (30),
    city varchar(40),
    rollNo int
);
alter table student add column marks int;
update student marks set marks = 30 where rollNo = 3;
insert into student values(100,'sam','delhi',1),(200,'ram','goa',2),(300,'riya','delhi',3);
select max(marks) FROM (select * from student where city = "delhi") as stu;
select * from student; 
set sql_safe_updates = 0;

-- Mysql views is a virtual table 
create view v1 AS select rollNo,name,marks from student;
drop view v1;
select * from v1;