**1.Query to find Second Highest Salary of Employee?(click for explaination)**

Answer:

Select distinct Salary from Employee e1 where 2=Select count(distinct Salary) from Employee e2 where e1.salary<=e2.salary;

Alternative Solution : Suggested by Ankit Srivastava

select min(salary)from(select distinct salary from emp order by salary desc)where rownum<=2;

**2.Query to find duplicate rows in table?(click here for explaination )**

Answer :

Select * from Employee a where rowid <>( select max(rowid) from Employee b where a.Employee_num=b.Employee_num);

3.How to fetch  monthly Salary of Employee if annual salary is given?(click here for Explaination) 

Answer:

   Select Employee_name,Salary/12 as ‘Monthly Salary’ from employee;

Click here to get information on ROW_ID

4.What is the Query to fetch first record from Employee table? (90% asked Complex SQL Queries Examples)

Answer:

 Select * from Employee where Rownum =1;

Select * from Employee where Rowid= select min(Rowid) from Employee;

Click here to get What is Rownum?

5.What is the Query to fetch last record from the table?

Answer:

Select * from Employee where Rowid= select max(Rowid) from Employee;

Complex SQL Queries Examples
Complex SQL Queries
Click here to get 20 interview questions on Perforance Tuning..

6.What is Query to display first 5 Records from Employee table?(90% asked Complex SQL Queries Examples)

Answer:

Select * from Employee where Rownum <= 5;

     
 
CLICK HERE TO GET INFORMATION ON NORMALIZATION

6.What is Query to display last 5 Records from Employee table?(90% asked Complex SQL Queries Examples)

Answer:

Select * from Employee e where rownum <=5

union

select * from (Select * from Employee e order by rowid desc) where rownum <=5;

Click Here to get What is Union?

7.What is Query to display Nth Record from Employee table?

Answer :

select * from ( select a.*, rownum rnum from ( YOUR_QUERY_GOES_HERE — including the order by ) a where rownum <= N_ROWS ) where rnum >= N_ROWS

 
8.How to get 3 Highest salaries records from Employee table?

Answer:

select distinct salary from employee a where 3 >= (select count(distinct salary) from employee b where a.salary <= b.salary) order by a.salary desc;

Alternative Solution: Suggested by Ankit Srivastava

select min(salary)from(select distinct salary from emp order by salary desc)where rownum<=3;

9.How to Display Odd rows in Employee table?(90% asked Complex SQL Queries Examples)

Answer:

Select * from(Select rownum as rno,E.* from Employee E) where Mod(rno,2)=1;

10.How to Display Even rows in Employee table?

Answer:

Select * from(Select rownum as rno,E.* from Employee) where Mod(rno,2)=0;

          Learn SQL Server Course here: SQL Server Training
11.How to fetch 3rd highest salary using Rank Function?

Answer:

select * from (Select Dense_Rank() over ( order by  salary desc) as Rnk,E.* from Employee E) where Rnk=3;

Click Here to Get Information on Rank and Dense_Rank

12.How Can i create table with same structure of Employee table?(90% asked Complex SQL Queries Examples)

Answer:

Create table Employee_1 as Select * from Employee where 1=2;

13.Display first 50% records from Employee table?


Answer:

select rownum, e.* from emp e where rownum<=(select count(*)/2 from emp);

14.Display last 50% records from Employee table?

Answer:

Select rownum,E.* from Employee E

minus

Select rownum,E.* from Employee E where rownum<=(Select count(*)/2) from Employee);

15.How Can i create table with same structure with data of Employee table?

Answer:

Create table Employee1 as select * from Employee;

16.How do i fetch only common records between 2 tables.

Answer:

Select * from Employee;

Intersect

Select * from Employee1;

CLICK HERE TO GET INFORMATION ABOUT INTERSECT OPERATOR

17.Find Query to get information of Employee where Employee is not assigned to the department

Answer:

Select * from Employee where Dept_no Not in(Select Department_no from Department);

18.How to get distinct records from the table without using distinct keyword.

Answer:

select * from Employee a where  rowid = (select max(rowid) from Employee b where  a.Employee_no=b.Employee_no);

19.Select all records from Employee table whose name is ‘Amit’ and ‘Pradnya’

Answer:

Select * from Employee where Name in(‘Amit’,’Pradnya’);

20.Select all records from Employee table where name not in ‘Amit’ and ‘Pradnya’

Answer:

select * from Employee where name Not  in (‘Amit’,’Pradnya’);

Click Here to get  20 Interview Questions for Tech Mahindra….

21.how to write sql query for the below scenario
I/p:ORACLE

O/p:
O
R
A
C
L
E
i.e, splitting into multiple columns a string using sql.

Answer:

Select Substr(‘ORACLE’,Level,1) From Dual
Connect By Level<= Length(‘ORACLE’);

22.How to fetch all the records from Employee whose joining year is  2017?

Answer:

Oracle:

select * from Employee where To_char(Joining_date,’YYYY’)=’2017′;

MS SQL:

select * from Employee where substr(convert(varchar,Joining_date,103),7,4)=’2017′;

23.What is SQL Query to find maximum salary of each department?

Answer:

Select Dept_id,max(salary) from Employee group by Dept_id;

24.How Do you find all Employees with its managers?(Consider there is manager id also in Employee table)

Answer:

Select e.employee_name,m.employee name from Employee e,Employee m where e.Employee_id=m.Manager_id;

25.Display the name of employees who have joined in 2016 and salary is greater than 10000?

Answer:

Select name from Employee where Hire_Date like ‘2016%’ and salary>10000;

26.How to display following using query?

*

**

***

Answer:

We cannot use dual table to display output given above. To display output use any table. I am using Student table.

SELECT lpad (‘*’, ROWNUM,’*’) FROM Student WHERE ROWNUM <4;

27.How to add the email validation using only one query?

Answer :

User needs to use REGEXP_LIKE function for email validation.

 SELECT
Email
FROM
Employee
where NOT REGEXP_LIKE(Email, ‘[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}’, ‘i’);

28.How to display 1 to 100 Numbers with query?

Answer:

Select level from dual connect by level <=100;

Tip: User needs to know the concept of Hierarchical queries. Click here to get concept of hierarchical queries

29.How to remove duplicate rows from table?(100% asked in Complex SQL Queries for Interviews)

Answer:

First Step: Selecting Duplicate rows from table

Tip: Use concept of max (rowid) of table. Click here to get concept of rowid.

Select rollno FROM Student WHERE ROWID <>

(Select max (rowid) from Student b where rollno=b.rollno);

Step 2:  Delete duplicate rows

Delete FROM Student WHERE ROWID <>

(Select max (rowid) from Student b where rollno=b.rollno);

30.How to find count of duplicate rows? (95% asked in SQL queries for Interviews )

Answer:

Select rollno, count (rollno) from Student

Group by rollno

Having count (rollno)>1

Order by count (rollno) desc;

31.How to Find the Joining date of Employee in YYYY-DAY-Date format.

Select FIRST_NAME, to_char(joining_date,’YYYY’) JoinYear , to_char(joining_date,’Mon’), to_char(joining_date,’dd’) from EMPLOYEES;

Hope This article named Complex SQL queries examples is useful to all the programmers. This article gives you the idea about Complex SQL Queries examples and will be useful to all the programmers.

Question 32 : How to convert the System time in to seconds in oracle?

Answer :

To_char function is used to convert time to character and ssss will used to convert the time in to seconds.

Following query is useful.

SQL> select
  2    to_char(sysdate,'hh24:mi:ss') As "SystemTime",
  3    to_char(sysdate,'sssss') "Seconds"
  4  from dual;

SystemTime     Seconds
--------       -----
11:34:50       41750
