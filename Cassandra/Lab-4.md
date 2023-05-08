bmscecse@bmscecse-HP-Elite-Tower-600-G9-Desktop-PC:~/Desktop$ cqlsh
Connected to Test Cluster at 127.0.0.1:9042
[cqlsh 6.0.0 | Cassandra 4.0.5 | CQL spec 3.4.5 | Native protocol v5]
Use HELP for help.
cqlsh> create keyspace employee with replication {'class': 'SimpleStrategy', 'replication_factor' :3  }
   ... 
cqlsh> create keyspace employee with replication ={'class': 'SimpleStrategy', 'replication_factor' :1  }; 
cqlsh> describe keyspaces

employee  system       system_distributed  system_traces  system_virtual_schema
students  system_auth  system_schema       system_views 

cqlsh> create table employee_info ( emp_id int primary key,   )
   ... 
cqlsh> create table employee_info ( emp_id int primary key, emp_name text, designation text, date_of_joining date, salary int, dept   )
   ... 
cqlsh> create table employee_info ( emp_id int primary key, emp_name text, designation text, date_of_joining date, salary int, dept_name text );
InvalidRequest: Error from server: code=2200 [Invalid query] message="No keyspace has been specified. USE a keyspace, or explicitly specify keyspace.tablename"
cqlsh> use employee
   ... 
cqlsh> use employee;
cqlsh:employee> create table employee_info ( emp_id int primary key, emp_name text, designation text, date_of_joining date, salary int, dept_name text );
cqlsh:employee> describe tables

employee_info

cqlsh:employee> begin batch INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (01, abc, SDE-3, 2012-12-30, 40000, IT) INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (02, adc, SDE-2, 2012-12-30, 40000, IT)INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (03, lmk, SDE-1, 2012-12-30, 40000, IT)INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (04, abe, analyst, 2012-11-30, 40000, business)APPLY BATCH
            ... 
cqlsh:employee> begin batch INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (01, abc, SDE-3, 2012-12-30, 40000, IT) INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (02, adc, SDE-2, 2012-12-30, 40000, IT)INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (03, lmk, SDE-1, 2012-12-30, 40000, IT)INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (04, abe, analyst, 2012-11-30, 40000, business)APPLY BATCH ;
SyntaxException: line 1:122 no viable alternative at input ',' (... dept_name) VALUES (01, [abc],...)
cqlsh:employee> begin batch INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (01, 'abc', 'SDE-3', 2012-12-30, 40000, 'IT') INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (02, 'adc', 'SDE-2', 2012-12-30, 40000, 'IT')INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (03, 'lmk', 'SDE-1', 2012-12-30, 40000, 'IT')INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (04, 'abe', 'analyst', 2012-11-30, 40000, 'business')APPLY BATCH ;
SyntaxException: line 1:139 no viable alternative at input '-12' (...01, 'abc', 'SDE-3', 2012[-12]...)
cqlsh:employee> begin batch INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (01, 'abc', 'SDE-3', '2012-12-30', 40000, 'IT') INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (02, 'adc', 'SDE-2', '2012-12-30', 40000, 'IT')INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (03, 'lmk', 'SDE-1', '2012-12-30', 40000, 'IT')INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (04, 'abe', 'analyst', '2012-11-30', 40000, 'business')APPLY BATCH ;
cqlsh:employee> select * from employee_info
            ... 
cqlsh:employee> select * from employee_info;

 emp_id | date_of_joining | dept_name | designation | emp_name | salary
--------+-----------------+-----------+-------------+----------+--------
      1 |      2012-12-30 |        IT |       SDE-3 |      abc |  40000
      2 |      2012-12-30 |        IT |       SDE-2 |      adc |  40000
      4 |      2012-11-30 |  business |     analyst |      abe |  40000
      3 |      2012-12-30 |        IT |       SDE-1 |      lmk |  40000

(4 rows)
cqlsh:employee> update employee_info set employeeename='afd' where emp_id=1;
InvalidRequest: Error from server: code=2200 [Invalid query] message="Undefined column name employeeename in table employee.employee_info"
cqlsh:employee> update employee_info set emp_name='afd' where emp_id=1;
cqlsh:employee> select * from employee_info;

 emp_id | date_of_joining | dept_name | designation | emp_name | salary
--------+-----------------+-----------+-------------+----------+--------
      1 |      2012-12-30 |        IT |       SDE-3 |      afd |  40000
      2 |      2012-12-30 |        IT |       SDE-2 |      adc |  40000
      4 |      2012-11-30 |  business |     analyst |      abe |  40000
      3 |      2012-12-30 |        IT |       SDE-1 |      lmk |  40000

(4 rows)
cqlsh:employee> INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (05, 'tyu', 'SDE-3', '2012-12-30', 70000, 'IT');
cqlsh:employee> alter table employee_info update salary (primary key);
SyntaxException: line 1:26 no viable alternative at input 'update' (alter table [employee_info] update...)
cqlsh:employee> alter table employee_info alter salary (primary key);
SyntaxException: line 1:39 mismatched input '(' expecting K_TYPE (alter table employee_info alter salary [(]...)
cqlsh:employee> alter table employee_info alter salary text (primary key);
SyntaxException: line 1:39 mismatched input 'text' expecting K_TYPE (alter table employee_info alter salary [text]...)
cqlsh:employee> alter table employee_info alter salary text primary key;
SyntaxException: line 1:39 mismatched input 'text' expecting K_TYPE (alter table employee_info alter salary [text]...)
cqlsh:employee> alter table employee_info drop salary
            ... 
cqlsh:employee> alter table employee_info drop salary;
cqlsh:employee> alter table employee_info add salary int primary key;
SyntaxException: line 1:41 mismatched input 'primary' expecting EOF (...table employee_info add salary int [primary] key...)
cqlsh:employee> drop eomployee_info
            ... ;
SyntaxException: line 1:5 no viable alternative at input 'eomployee_info' ([drop] eomployee_info...)
cqlsh:employee> drop eomployee_info;
SyntaxException: line 1:5 no viable alternative at input 'eomployee_info' ([drop] eomployee_info...)
cqlsh:employee> drop employee_info;
SyntaxException: line 1:5 no viable alternative at input 'employee_info' ([drop] employee_info...)
cqlsh:employee> drop employee_info;
SyntaxException: line 1:5 no viable alternative at input 'employee_info' ([drop] employee_info...)
cqlsh:employee> drop table  employee_info;
cqlsh:employee> use employee;
cqlsh:employee> create table employee_info ( emp_id int, emp_name text, designation text, date_of_joining date, salary int, dept_name text, primary key(emp_id, salary));
cqlsh:employee> describe tables

employee_info

cqlsh:employee> begin batch INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (01, 'abc', 'SDE-3', 2012-12-30, 40000, 'IT') INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (02, 'adc', 'SDE-2', 2012-12-30, 40000, 'IT')INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (03, 'lmk', 'SDE-1', 2012-12-30, 40000, 'IT')INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (04, 'abe', 'analyst', 2012-11-30, 40000, 'business')APPLY BATCH ;
SyntaxException: line 1:139 no viable alternative at input '-12' (...01, 'abc', 'SDE-3', 2012[-12]...)
cqlsh:employee> begin batch INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (01, 'abc', 'SDE-3', '2012-12-30', 40000, 'IT') INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (02, 'adc', 'SDE-2', '2012-12-30', 40000, 'IT')INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (03, 'lmk', 'SDE-1', '2012-12-30', 40000, 'IT')INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (04, 'abe', 'analyst', '2012-11-30', 40000, 'business')APPLY BATCH ;
cqlsh:employee> select * from employee_info;

 emp_id | salary | date_of_joining | dept_name | designation | emp_name
--------+--------+-----------------+-----------+-------------+----------
      1 |  40000 |      2012-12-30 |        IT |       SDE-3 |      abc
      2 |  40000 |      2012-12-30 |        IT |       SDE-2 |      adc
      4 |  40000 |      2012-11-30 |  business |     analyst |      abe
      3 |  40000 |      2012-12-30 |        IT |       SDE-1 |      lmk

(4 rows)
cqlsh:employee> INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (05, 'tyu', 'SDE-3', '2012-12-30', 70000, 'IT');
cqlsh:employee> select * from employee_info;

 emp_id | salary | date_of_joining | dept_name | designation | emp_name
--------+--------+-----------------+-----------+-------------+----------
      5 |  70000 |      2012-12-30 |        IT |       SDE-3 |      tyu
      1 |  40000 |      2012-12-30 |        IT |       SDE-3 |      abc
      2 |  40000 |      2012-12-30 |        IT |       SDE-2 |      adc
      4 |  40000 |      2012-11-30 |  business |     analyst |      abe
      3 |  40000 |      2012-12-30 |        IT |       SDE-1 |      lmk

(5 rows)
cqlsh:employee> alter table add projects set{text};
SyntaxException: line 1:12 no viable alternative at input 'add' (alter table [add]...)
cqlsh:employee> alter table employee_info add projects set< text>;
cqlsh:employee> update employee_info set projects= projects+ {'sql'} where emp_id=1;
InvalidRequest: Error from server: code=2200 [Invalid query] message="Some clustering keys are missing: salary"
cqlsh:employee> update employee_info set projects= projects+ {'sql'} where emp_id=1 and salary=40000;
cqlsh:employee> select * from employee_info;

 emp_id | salary | date_of_joining | dept_name | designation | emp_name | projects
--------+--------+-----------------+-----------+-------------+----------+----------
      5 |  70000 |      2012-12-30 |        IT |       SDE-3 |      tyu |     null
      1 |  40000 |      2012-12-30 |        IT |       SDE-3 |      abc |  {'sql'}
      2 |  40000 |      2012-12-30 |        IT |       SDE-2 |      adc |     null
      4 |  40000 |      2012-11-30 |  business |     analyst |      abe |     null
      3 |  40000 |      2012-12-30 |        IT |       SDE-1 |      lmk |     null

(5 rows)
cqlsh:employee> update employee_info set projects= projects+ {'cql'} where emp_id=2 and salary=40000;
cqlsh:employee> update employee_info set projects= projects+ {'cql'} where emp_id=2 and salary=40000;
cqlsh:employee> update employee_info set projects= projects+ {'nlp'} where emp_id=5 and salary=70000;
cqlsh:employee> update employee_info set projects= projects+ {'nlp'} where emp_id=3 and salary=40000;
cqlsh:employee> update employee_info set projects= projects+ {'nlp'} where emp_id=4 and salary=40000;
cqlsh:employee> select * from employee_info;

 emp_id | salary | date_of_joining | dept_name | designation | emp_name | projects
--------+--------+-----------------+-----------+-------------+----------+----------
      5 |  70000 |      2012-12-30 |        IT |       SDE-3 |      tyu |  {'nlp'}
      1 |  40000 |      2012-12-30 |        IT |       SDE-3 |      abc |  {'sql'}
      2 |  40000 |      2012-12-30 |        IT |       SDE-2 |      adc |  {'cql'}
      4 |  40000 |      2012-11-30 |  business |     analyst |      abe |  {'nlp'}
      3 |  40000 |      2012-12-30 |        IT |       SDE-1 |      lmk |  {'nlp'}

(5 rows)
cqlsh:employee> select * from employee_info order by column_name [ASC] , salary *
            ... 
cqlsh:employee> select * from employee_info order by column_name [ASC] , salary *;
SyntaxException: line 1:49 mismatched input '[' expecting EOF (...from employee_info order by column_name [[]...)
cqlsh:employee> select * from employee_info order by salary asc;
InvalidRequest: Error from server: code=2200 [Invalid query] message="ORDER BY is only supported when the partition key is restricted by an EQ or an IN."
cqlsh:employee> select * from employee_info order by salary;
InvalidRequest: Error from server: code=2200 [Invalid query] message="ORDER BY is only supported when the partition key is restricted by an EQ or an IN."
cqlsh:employee> select * from employee_info order by designation;
InvalidRequest: Error from server: code=2200 [Invalid query] message="ORDER BY is only supported when the partition key is restricted by an EQ or an IN."
cqlsh:employee> select * from employee_info order by emp_id;
InvalidRequest: Error from server: code=2200 [Invalid query] message="ORDER BY is only supported when the partition key is restricted by an EQ or an IN."
cqlsh:employee> INSERT INTO employee_info ( emp_id, emp_name, designation, date_of_joining, salary, dept_name) VALUES (06, 'tpu', 'SDE-3', '2012-12-30', 75000, 'IT') using ttl 30 ;
cqlsh:employee> select ttl(*) from employee_info where emp_id=6 and salary=75000
            ... 
cqlsh:employee> select ttl(*) from employee_info where emp_id=6 and salary=75000;
SyntaxException: line 1:11 no viable alternative at input '*' (select ttl([*]...)
cqlsh:employee> select ttl(emp_name) from employee_info where emp_id=6 and salary=75000;

 ttl(emp_name)
---------------

(0 rows)
cqlsh:employee> select * from employee_info order by salary;
InvalidRequest: Error from server: code=2200 [Invalid query] message="ORDER BY is only supported when the partition key is restricted by an EQ or an IN."
cqlsh:employee> create keyspace library 
            ... ;
SyntaxException: line 2:0 mismatched input ';' expecting K_WITH (create keyspace library [;])
cqlsh:employee> create keyspace library;
SyntaxException: line 1:23 mismatched input ';' expecting K_WITH (create keyspace library[;])
cqlsh:employee> create keyspace library with replication={'class': 'SimpleStrategy', 'replication_factor':1 };
cqlsh:employee> describe keyspaces

employee  students  system_auth         system_schema  system_views         
library   system    system_distributed  system_traces  system_virtual_schema

cqlsh:employee> use library
            ... ;
cqlsh:library> use library;
