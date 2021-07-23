```python
import sqlalchemy
```

#### Replace * with your Mysql Password


```python
sqlalchemy.create_engine("mysql+mysqldb://root:****@localhost:3306/oracle_emp")
```




    Engine(mysql+mysqldb://root:***@localhost:3306/oracle_emp)




```python
%load_ext sql
```

    C:\Users\tskir\Anaconda3\lib\site-packages\numpy\_distributor_init.py:32: UserWarning: loaded more than 1 DLL from .libs:
    C:\Users\tskir\Anaconda3\lib\site-packages\numpy\.libs\libopenblas.PYQHXLVVQ7VESDPUVUADXEVJOBGHJPAY.gfortran-win_amd64.dll
    C:\Users\tskir\Anaconda3\lib\site-packages\numpy\.libs\libopenblas.QVLO2T66WEPI7JZ63PS3HMOHFEY472BC.gfortran-win_amd64.dll
      stacklevel=1)
    

#### Replace * with your Mysql Password


```python
%sql "mysql+mysqldb://root:*****@localhost:3306/oracle_emp"
```


```python
%%sql
use oracle_emp;
create table dept(
  deptno int2,
  dname  varchar(14),
  loc    varchar(13),
  constraint pk_dept primary key (deptno)
);
 
create table emp(
  empno    int4,
  ename    varchar(10),
  job      varchar(9),
  mgr      int4,
  hiredate date,
  sal      decimal(7,2),
  comm     decimal(7,2),
  deptno   int2,
  constraint pk_emp primary key (empno),
  constraint fk_deptno foreign key (deptno) references dept (deptno)
);
 

create table bonus(
  ename varchar(10),
  job   varchar(9),
  sal   int4,
  comm  int4
);
 
create table salgrade(
  grade integer,
  losal integer,
  hisal integer
);

```


```python

insert into dept
values(10, 'ACCOUNTING', 'NEW YORK');
insert into dept
values(20, 'RESEARCH', 'DALLAS');
insert into dept
values(30, 'SALES', 'CHICAGO');
insert into dept
values(40, 'OPERATIONS', 'BOSTON');
INSERT INTO EMP VALUES (7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20); 
INSERT INTO EMP VALUES (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30);
INSERT INTO EMP VALUES (7521,'WARD','SALESMAN',7698,'1981-02-22',1250,500,30); 
INSERT INTO EMP VALUES (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20); 
INSERT INTO EMP VALUES (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30); 
INSERT INTO EMP VALUES (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30); 
INSERT INTO EMP VALUES (7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,10); 
INSERT INTO EMP VALUES (7788,'SCOTT','ANALYST',7566,'1987-07-13',3000,NULL,20); 
INSERT INTO EMP VALUES (7839,'KING','PRESIDENT',NULL,'1981-11-07',5000,NULL,10); 
INSERT INTO EMP VALUES (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30); 
INSERT INTO EMP VALUES (7876,'ADAMS','CLERK',7788,'1987-07-13',1100,NULL,20); 
INSERT INTO EMP VALUES (7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30); 
INSERT INTO EMP VALUES (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20); 
INSERT INTO EMP VALUES (7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
 

insert into salgrade
values (1, 700, 1200);
insert into salgrade
values (2, 1201, 1400);
insert into salgrade
values (3, 1401, 2000);
insert into salgrade
values (4, 2001, 3000);
insert into salgrade
values (5, 3001, 9999);
 
commit;
```
