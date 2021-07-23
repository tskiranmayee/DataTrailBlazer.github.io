### Continuation .... 51-100 SQL Oracle EMP Questions

### SQLAlchemy library with jupyter notebook ide is used


```python
import sqlalchemy
```

#### Replace * with your Mysql Password


```python
sqlalchemy.create_engine("mysql+mysqldb://root:*****@localhost:3306/oracle_emp")
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

#### 51. List the Emps who are senior to their own MGRS.


```python
%%sql
select * from emp e where (datediff(curdate(),hiredate)/365)>(select (datediff(curdate(),hiredate)/365) from emp f where f.empno=e.mgr )
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    6 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-20</td>
        <td>1600.00</td>
        <td>300.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-22</td>
        <td>1250.00</td>
        <td>500.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
</table>



#### 52. List the Emps of Deptno 20 whose Jobs are same as Deptno10.


```python
%%sql
select * from emp e where e.deptno=20 and e.job in (select f.job from emp f where f.deptno=10) ;
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>CLERK</td>
        <td>7788</td>
        <td>1987-07-13</td>
        <td>1100.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



#### 53.List the Emps whose Sal is same as FORD or SMITH in desc order of Sal.


```python
%%sql
select * from emp e where e.sal in(select f.sal from emp f where f.ename like "FORD" or f.ename like "SMITH") and e.ename not like "FORD" and e.ename not like "Smith" order by sal desc
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



#### 54. List the emps Whose Jobs are same as MILLER or Sal is more than ALLEN.


```python
%%sql
select * from emp e where e.job like (select f.job from emp f where f.ename like "Miller") 
or e.sal >(select g.sal from emp g where g.ename="Allen")
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    10 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>CLERK</td>
        <td>7788</td>
        <td>1987-07-13</td>
        <td>1100.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7900</td>
        <td>JAMES</td>
        <td>CLERK</td>
        <td>7698</td>
        <td>1981-12-03</td>
        <td>950.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
</table>



#### 55. List the Emps whose Sal is > the maximum remuneration of the SALESMAN.


```python
%%sql
select * from emp e where e.sal > (select max(f.sal+f.comm)  from emp f where f.job like "salesman")
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



#### 56. List the emps who are senior to BLAKE working at CHICAGO & BOSTON.


```python
%%sql
select e.* from emp e,dept d where (datediff(curdate(),e.hiredate)/365) >(select (datediff(curdate(),f.hiredate)/365) 
                                                                    from emp f where f.ename like "Blake")

and e.deptno=d.deptno and d.loc like "chicago" 
union
select e.* from emp e,dept d where (datediff(curdate(),e.hiredate)/365) >(select (datediff(curdate(),f.hiredate)/365) 
                                                                    from emp f where f.ename like "Blake")

and e.deptno=d.deptno and d.loc like "boston"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-20</td>
        <td>1600.00</td>
        <td>300.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-22</td>
        <td>1250.00</td>
        <td>500.00</td>
        <td>30</td>
    </tr>
</table>



#### 57. List the Emps of Grade 3,4 belongs to the dept ACCOUNTING and RESEARCH whose Sal is more than ALLEN and exp more than Blake in the asc order of EXP.


```python
%%sql
select * from emp e,salgrade g,dept d where e.sal between g.losal and g.hisal and g.grade in(3,4) and e.deptno=d.deptno
and d.dname in("Accounting","Research") and e.sal>(select f.sal from emp f where f.ename="Allen") and (datediff(curdate(),e.hiredate)/365)>
(select (datediff(curdate(),f.hiredate)/365) 
                                                                    from emp f where f.ename like "Blake") order by e.hiredate
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
        <th>grade</th>
        <th>losal</th>
        <th>hisal</th>
        <th>deptno_1</th>
        <th>dname</th>
        <th>loc</th>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
        <td>4</td>
        <td>2001</td>
        <td>3000</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
    </tr>
</table>



#### 58. List the emps whose jobs same as SMITH or ALLEN.


```python
%%sql
select * from emp
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-20</td>
        <td>1600.00</td>
        <td>300.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-22</td>
        <td>1250.00</td>
        <td>500.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-28</td>
        <td>1250.00</td>
        <td>1400.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-08</td>
        <td>1500.00</td>
        <td>0.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>CLERK</td>
        <td>7788</td>
        <td>1987-07-13</td>
        <td>1100.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7900</td>
        <td>JAMES</td>
        <td>CLERK</td>
        <td>7698</td>
        <td>1981-12-03</td>
        <td>950.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
</table>



#### 59. Write a Query to display the details of emps whose Sal is same as of
##### a) Employee Sal of EMP1 table.
##### b) ¾ Sal of any Mgr of EMP2 table.
##### c) The sal of any person with exp of 38 years belongs to the sales dept of emp3 table.
##### d) Any grade 2 employee of emp4 table.
##### e) Any grade 2 and 3 employee working fro sales dept or operations dept joined in 1989.

#### Answers to 59(a)-(e)
##### 59(a) Employee Sal of EMP1 table.


```python
%%sql
create table emp1 (sal int4)
```


```python
%%sql
insert into emp1 select sal from emp;
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




    []




```python
%%sql
select * from emp1

```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>sal</th>
    </tr>
    <tr>
        <td>800</td>
    </tr>
    <tr>
        <td>1600</td>
    </tr>
    <tr>
        <td>1250</td>
    </tr>
    <tr>
        <td>2975</td>
    </tr>
    <tr>
        <td>1250</td>
    </tr>
    <tr>
        <td>2850</td>
    </tr>
    <tr>
        <td>2450</td>
    </tr>
    <tr>
        <td>3000</td>
    </tr>
    <tr>
        <td>5000</td>
    </tr>
    <tr>
        <td>1500</td>
    </tr>
    <tr>
        <td>1100</td>
    </tr>
    <tr>
        <td>950</td>
    </tr>
    <tr>
        <td>3000</td>
    </tr>
    <tr>
        <td>1300</td>
    </tr>
</table>



##### 59(b) ¾ Sal of any Mgr of EMP2 table.


```python
%%sql
CREATE TABLE emp2 (sal int4)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    0 rows affected.
    




    []




```python
%%sql 
insert into emp2 select (3/4)*sal from emp e where e.job like "Manager"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




    []




```python
%%sql
select * from emp2
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>sal</th>
    </tr>
    <tr>
        <td>2231</td>
    </tr>
    <tr>
        <td>2138</td>
    </tr>
    <tr>
        <td>1838</td>
    </tr>
</table>



##### 59(c) The sal of any person with exp of  38 years belongs to the sales dept of emp3 table.


```python
%%sql
create table emp3 (sal int4)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    0 rows affected.
    




    []




```python
%%sql 
insert into emp3 select e.sal from emp e,dept d where (datediff(curdate(),e.hiredate)/365) >38 and e.deptno=d.deptno and d.dname like "Sales"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    6 rows affected.
    




    []




```python
%%sql
select * from emp3
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    6 rows affected.
    




<table>
    <tr>
        <th>sal</th>
    </tr>
    <tr>
        <td>1600</td>
    </tr>
    <tr>
        <td>1250</td>
    </tr>
    <tr>
        <td>1250</td>
    </tr>
    <tr>
        <td>2850</td>
    </tr>
    <tr>
        <td>1500</td>
    </tr>
    <tr>
        <td>950</td>
    </tr>
</table>



##### 59(d) Any grade 2 employee of emp4 table.


```python
%%sql
create table emp4(
  empno    int4,
  ename    varchar(10),
  job      varchar(9),
  mgr      int4,
  hiredate date,
  sal      decimal(7,2),
  comm     decimal(7,2),
  deptno   int2,
    constraint pk_emp primary key (empno)
)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    0 rows affected.
    




    []




```python
%%sql
insert into emp4 select e.* from emp e,salgrade g 
where e.sal between g.losal and g.hisal and g.grade=2
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




    []




```python
%%sql
select * from emp4
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-22</td>
        <td>1250.00</td>
        <td>500.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-28</td>
        <td>1250.00</td>
        <td>1400.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
</table>



##### 59 e) Any grade 2 and 3 employee working from sales dept or operations dept joined in 1989.


```python
%%sql
create table emp5 (empno    int4,
  ename    varchar(10),
  job      varchar(9),
  mgr      int4,
  hiredate date,
  sal      decimal(7,2),
  comm     decimal(7,2),
  deptno   int2,
    constraint pk_emp primary key (empno))
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    0 rows affected.
    




    []




```python
%%sql
insert into emp5 select e.* from emp e,salgrade g,dept d where 1989=extract(year from e.hiredate)
and e.sal between g.losal and g.hisal and g.grade in(2,3) and e.deptno=d.deptno and d.dname in ("Sales","Operations")
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    0 rows affected.
    




    []




```python
%%sql
select * from emp5
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    0 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
</table>



#### 60. Any jobs of deptno 10 those that are not found in deptno 20.


```python
%%sql
select distinct(e1.job) from emp e1,emp e2 where e1.deptno=10 and e2.deptno=20 and e1.job<>e2.job
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>job</th>
    </tr>
    <tr>
        <td>MANAGER</td>
    </tr>
    <tr>
        <td>PRESIDENT</td>
    </tr>
    <tr>
        <td>CLERK</td>
    </tr>
</table>



#### 61. List of emps of emp4 who are not found in emp5.


```python
%%sql
select e1.ename from emp4 e1,emp5 e2 where e1.ename<>e2.ename
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    0 rows affected.
    




<table>
    <tr>
        <th>ename</th>
    </tr>
</table>



#### 62. Find the highest sal of EMP table.


```python
%%sql 
select max(sal) from emp 
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>max(sal)</th>
    </tr>
    <tr>
        <td>5000.00</td>
    </tr>
</table>



#### 63. Find details of highest paid employee.


```python
%%sql
select * from emp where sal in(select max(e.sal) from emp e)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
</table>



#### 64. Find the highest paid employee of sales department.


```python
%%sql
select max(e.sal) from emp e,dept d where e.deptno=d.deptno and d.dname="Sales"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>max(e.sal)</th>
    </tr>
    <tr>
        <td>2850.00</td>
    </tr>
</table>



#### 65. List the most recently hired emp of grade3 belongs to location CHICAGO.


```python
%%sql
select * from emp e,salgrade g,dept d where e.sal between g.losal and g.hisal and g.grade=3 and e.deptno=d.deptno and d.loc="chicago"
order by e.hiredate desc limit 1
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
        <th>grade</th>
        <th>losal</th>
        <th>hisal</th>
        <th>deptno_1</th>
        <th>dname</th>
        <th>loc</th>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-08</td>
        <td>1500.00</td>
        <td>0.00</td>
        <td>30</td>
        <td>3</td>
        <td>1401</td>
        <td>2000</td>
        <td>30</td>
        <td>SALES</td>
        <td>CHICAGO</td>
    </tr>
</table>



#### 66. List the employees who are senior to most recently hired employee working under king.


```python
%%sql
select * from emp e1 where e1.hiredate<(select max(e.hiredate) from emp e where e.mgr in
                                        (select e2.empno from emp e2 where e2.ename="King"))
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-20</td>
        <td>1600.00</td>
        <td>300.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-22</td>
        <td>1250.00</td>
        <td>500.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
</table>



#### 67. List the details of the employee belongs to newyork with grade 3 to 5 except ‘PRESIDENT’ whose sal> the highest paid employee of Chicago in a group where there is manager and salesman not working under king


```python
%%sql
select e.* from emp e,dept d,salgrade g where e.deptno=d.deptno and d.loc="new york" 
and
e.sal between g.losal and g.hisal and g.grade between 3 and 5 and
e.job<>"President"  and e.sal >(select max(e1.sal) from emp e1,dept d1 where e1.deptno=d1.deptno and 
                                d1.loc="Chicago" and e1.mgr<>(select e3.empno from emp e3 where e3.job="President" ) group by e1.deptno )
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
</table>



#### 68. List the details of the senior employee belongs to 1981.


```python
%%sql
select * from emp e where 1981=extract( year from e.hiredate) order by e.hiredate asc limit 1
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-20</td>
        <td>1600.00</td>
        <td>300.00</td>
        <td>30</td>
    </tr>
</table>



#### 69. List the employees who joined in 1981 with the job same as the most senior person of the year 1981.


```python
%%sql
select * from emp e where 1981=extract(year from e.hiredate) and e.job = (select e1.job from emp e1 where 1981=extract( year from e1.hiredate) order by e1.hiredate asc limit 1)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    4 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-20</td>
        <td>1600.00</td>
        <td>300.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-22</td>
        <td>1250.00</td>
        <td>500.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-28</td>
        <td>1250.00</td>
        <td>1400.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-08</td>
        <td>1500.00</td>
        <td>0.00</td>
        <td>30</td>
    </tr>
</table>



#### 70. List the most senior employee working under the king and grade is more than 3.


```python
%%sql 
select * from emp e where e.hiredate =(select min(e1.hiredate) from emp e1,salgrade g1 where 
                                       e1.sal between g1.losal and g1.hisal and g1.grade > 3 
                                       and e1.mgr =(select e2.empno from emp e2 where e2.ename="King"))
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



#### 71. Find the cumulative sal given to the MGR.


```python
%%sql
select sum(e.sal) from emp e where e.job="Manager"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>sum(e.sal)</th>
    </tr>
    <tr>
        <td>8275.00</td>
    </tr>
</table>



#### 72. Find the total annual sal to distribute job wise in the year 81.


```python
%%sql
select e.job,sum(e.sal)*12 as AnnualSal from emp e where 1981=extract(year from e.hiredate) group by e.job
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>job</th>
        <th>AnnualSal</th>
    </tr>
    <tr>
        <td>SALESMAN</td>
        <td>67200.00</td>
    </tr>
    <tr>
        <td>MANAGER</td>
        <td>99300.00</td>
    </tr>
    <tr>
        <td>PRESIDENT</td>
        <td>60000.00</td>
    </tr>
    <tr>
        <td>CLERK</td>
        <td>11400.00</td>
    </tr>
    <tr>
        <td>ANALYST</td>
        <td>36000.00</td>
    </tr>
</table>



#### 73. Display total sal employee belonging to grade 3.


```python
%%sql
select sum(e.sal) from emp e,salgrade g where e.sal between g.losal and g.hisal and g.grade=3
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>sum(e.sal)</th>
    </tr>
    <tr>
        <td>3100.00</td>
    </tr>
</table>



#### 74. Display the average salaries of all the clerks.


```python
%%sql
select avg(e.sal) from emp e where e.job="clerk"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>avg(e.sal)</th>
    </tr>
    <tr>
        <td>1037.500000</td>
    </tr>
</table>



#### 75. List the employee in dept 20 whose sal is >the average sal 0f dept 10 emps.


```python
%%sql
select * from emp e where e.deptno=20 and e.sal>(select avg(e1.sal) from emp e1 where e1.deptno=10)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



#### 76. Display the number of employee for each job group deptno wise.


```python
%%sql
select e.deptno,e.job,count(*) from emp e  group by e.job,e.deptno 
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    9 rows affected.
    




<table>
    <tr>
        <th>deptno</th>
        <th>job</th>
        <th>count(*)</th>
    </tr>
    <tr>
        <td>20</td>
        <td>CLERK</td>
        <td>2</td>
    </tr>
    <tr>
        <td>30</td>
        <td>SALESMAN</td>
        <td>4</td>
    </tr>
    <tr>
        <td>20</td>
        <td>MANAGER</td>
        <td>1</td>
    </tr>
    <tr>
        <td>30</td>
        <td>MANAGER</td>
        <td>1</td>
    </tr>
    <tr>
        <td>10</td>
        <td>MANAGER</td>
        <td>1</td>
    </tr>
    <tr>
        <td>20</td>
        <td>ANALYST</td>
        <td>2</td>
    </tr>
    <tr>
        <td>10</td>
        <td>PRESIDENT</td>
        <td>1</td>
    </tr>
    <tr>
        <td>30</td>
        <td>CLERK</td>
        <td>1</td>
    </tr>
    <tr>
        <td>10</td>
        <td>CLERK</td>
        <td>1</td>
    </tr>
</table>



#### 77. List the manager's deptno and the number of employees working for those managers in the ascending deptno.


```python
%%sql
select e.deptno,e.ename,e.job,count(*)  from emp e ,emp e1
       where  e.job="Manager" and e.empno=e1.mgr group by e.deptno

```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>deptno</th>
        <th>ename</th>
        <th>job</th>
        <th>count(*)</th>
    </tr>
    <tr>
        <td>30</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>5</td>
    </tr>
    <tr>
        <td>20</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>2</td>
    </tr>
    <tr>
        <td>10</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>1</td>
    </tr>
</table>



#### 78. List the department details where at least two emps are working


```python
%%sql
select d.*,count(*) as CountOfEmployees from emp e,dept d where d.deptno=e.deptno and 1<(select count(*) from emp e1) group by d.deptno
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>deptno</th>
        <th>dname</th>
        <th>loc</th>
        <th>CountOfEmployees</th>
    </tr>
    <tr>
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>NEW YORK</td>
        <td>3</td>
    </tr>
    <tr>
        <td>20</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
        <td>5</td>
    </tr>
    <tr>
        <td>30</td>
        <td>SALES</td>
        <td>CHICAGO</td>
        <td>6</td>
    </tr>
</table>



#### 79. Display the Grade, Number of emps, and max sal of each grade.


```python
%%sql
select g.grade,max(e.sal),count(*) from salgrade g ,emp e 
where e.sal between g.losal and g.hisal group by g.grade order by g.grade
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>grade</th>
        <th>max(e.sal)</th>
        <th>count(*)</th>
    </tr>
    <tr>
        <td>1</td>
        <td>1100.00</td>
        <td>3</td>
    </tr>
    <tr>
        <td>2</td>
        <td>1300.00</td>
        <td>3</td>
    </tr>
    <tr>
        <td>3</td>
        <td>1600.00</td>
        <td>2</td>
    </tr>
    <tr>
        <td>4</td>
        <td>3000.00</td>
        <td>5</td>
    </tr>
    <tr>
        <td>5</td>
        <td>5000.00</td>
        <td>1</td>
    </tr>
</table>



#### 80. Display dname, grade, No. of emps where at least two emps are clerks.


```python
%%sql
select d.deptno,d.dname,g.grade,count(*) as EmpCountInDept from emp e,dept d,salgrade g where 
e.sal between g.losal and g.hisal and e.deptno=d.deptno group by e.deptno
having e.deptno=(select e2.deptno from emp e2 where e2.job="clerk" group by e2.deptno having 1< count(*)) order by d.deptno
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>deptno</th>
        <th>dname</th>
        <th>grade</th>
        <th>EmpCountInDept</th>
    </tr>
    <tr>
        <td>20</td>
        <td>RESEARCH</td>
        <td>1</td>
        <td>5</td>
    </tr>
</table>



#### 81. List the details of the department where maximum number of emps are working.


```python
%%sql
select d.*,count(*)  from dept d,emp e where d.deptno=e.deptno group by e.deptno order by count(*) desc limit 1
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>deptno</th>
        <th>dname</th>
        <th>loc</th>
        <th>count(*)</th>
    </tr>
    <tr>
        <td>30</td>
        <td>SALES</td>
        <td>CHICAGO</td>
        <td>6</td>
    </tr>
</table>



#### 82.Display the emps whose manager name is jones.


```python
%%sql
select * from emp e where e.mgr=(select e1.empno from emp e1 where e1.ename="jones")
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



#### 83. List the employees whose salary is more than 3000 after giving 20% increment.


```python
%%sql
select * from emp e where e.sal+(e.sal*20/100)>3000 
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



#### 84. List the emps with dept names.


```python
%%sql
select e.*,d.dname from emp e,dept d where e.deptno=d.deptno  
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
        <th>dname</th>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
        <td>None</td>
        <td>10</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
        <td>None</td>
        <td>10</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>CLERK</td>
        <td>7788</td>
        <td>1987-07-13</td>
        <td>1100.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-20</td>
        <td>1600.00</td>
        <td>300.00</td>
        <td>30</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-22</td>
        <td>1250.00</td>
        <td>500.00</td>
        <td>30</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-28</td>
        <td>1250.00</td>
        <td>1400.00</td>
        <td>30</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-08</td>
        <td>1500.00</td>
        <td>0.00</td>
        <td>30</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7900</td>
        <td>JAMES</td>
        <td>CLERK</td>
        <td>7698</td>
        <td>1981-12-03</td>
        <td>950.00</td>
        <td>None</td>
        <td>30</td>
        <td>SALES</td>
    </tr>
</table>



#### 85. List the emps who are not working in sales dept.


```python
%%sql
select e.*,d.dname from emp e,dept d where e.deptno=d.deptno and d.dname<>"Sales"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    8 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
        <th>dname</th>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
        <td>None</td>
        <td>10</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
        <td>None</td>
        <td>10</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>CLERK</td>
        <td>7788</td>
        <td>1987-07-13</td>
        <td>1100.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
        <td>RESEARCH</td>
    </tr>
</table>



#### 86. List the emps name ,dept, sal and comm. For those whose salary is between 2000 and 5000 while loc is Chicago.


```python
%%sql
select e.ename,e.deptno,e.sal,e.comm,d.loc from emp e,dept d where e.sal between 2000 and 5000 and e.deptno=d.deptno and d.loc="Chicago"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>deptno</th>
        <th>sal</th>
        <th>comm</th>
        <th>loc</th>
    </tr>
    <tr>
        <td>BLAKE</td>
        <td>30</td>
        <td>2850.00</td>
        <td>None</td>
        <td>CHICAGO</td>
    </tr>
</table>



#### 87. List the emps whose sal is greater than his managers salary


```python
%%sql
select * from emp e where e.sal>(select e2.sal from emp e2,emp e1 where e2.mgr=e1.empno and e2.job="Manager" group by e2.mgr ) 
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



#### 88. List the grade, EMP name for the deptno 10 or deptno 30 but sal grade is not 4 while they joined the company before ’31-dec-82’.


```python

%%sql
select e.ename,g.grade,e.hiredate from emp e,salgrade g,dept d where e.deptno=d.deptno and d.deptno in (10,30) 
and e.sal between g.losal and g.hisal and g.grade not in (4)
and e.hiredate>1982-12-31
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    7 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>grade</th>
        <th>hiredate</th>
    </tr>
    <tr>
        <td>JAMES</td>
        <td>1</td>
        <td>1981-12-03</td>
    </tr>
    <tr>
        <td>MARTIN</td>
        <td>2</td>
        <td>1981-09-28</td>
    </tr>
    <tr>
        <td>WARD</td>
        <td>2</td>
        <td>1981-02-22</td>
    </tr>
    <tr>
        <td>MILLER</td>
        <td>2</td>
        <td>1982-01-23</td>
    </tr>
    <tr>
        <td>TURNER</td>
        <td>3</td>
        <td>1981-09-08</td>
    </tr>
    <tr>
        <td>ALLEN</td>
        <td>3</td>
        <td>1981-02-20</td>
    </tr>
    <tr>
        <td>KING</td>
        <td>5</td>
        <td>1981-11-07</td>
    </tr>
</table>



#### 89. List the name ,job, dname, location for those who are working as MGRS.


```python
%%sql
select e.ename,e.job,d.dname,d.loc from emp e,dept d where e.job="Manager" and e.deptno=d.deptno
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>job</th>
        <th>dname</th>
        <th>loc</th>
    </tr>
    <tr>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
    </tr>
    <tr>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>SALES</td>
        <td>CHICAGO</td>
    </tr>
    <tr>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>ACCOUNTING</td>
        <td>NEW YORK</td>
    </tr>
</table>



#### 90. List the emps whose mgr name is jones and also list their manager name.


```python
%%sql
select e.ename,e2.ename as MgrName from emp e, emp e2 where 
e.mgr=(select e1.empno from emp e1 where e1.ename="Jones") 
and e.mgr=e2.empno and e2.ename="jones"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>MgrName</th>
    </tr>
    <tr>
        <td>SCOTT</td>
        <td>JONES</td>
    </tr>
    <tr>
        <td>FORD</td>
        <td>JONES</td>
    </tr>
</table>



#### 91. List the name and salary of ford if his salary is equal to hisal of his grade.


```python
%%sql
select * from emp
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-20</td>
        <td>1600.00</td>
        <td>300.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-02-22</td>
        <td>1250.00</td>
        <td>500.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-28</td>
        <td>1250.00</td>
        <td>1400.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1987-07-13</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-08</td>
        <td>1500.00</td>
        <td>0.00</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>CLERK</td>
        <td>7788</td>
        <td>1987-07-13</td>
        <td>1100.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7900</td>
        <td>JAMES</td>
        <td>CLERK</td>
        <td>7698</td>
        <td>1981-12-03</td>
        <td>950.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>7566</td>
        <td>1981-12-03</td>
        <td>3000.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
</table>



#### 92. List the name, job, dname ,sal, grade dept wise


```python
%%sql
select e.ename,d.deptno,d.dname,e.sal,g.grade from emp e,dept d,salgrade g 
where e.sal between g.losal and g.hisal and e.deptno=d.deptno order by e.deptno
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>deptno</th>
        <th>dname</th>
        <th>sal</th>
        <th>grade</th>
    </tr>
    <tr>
        <td>CLARK</td>
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>2450.00</td>
        <td>4</td>
    </tr>
    <tr>
        <td>KING</td>
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>5000.00</td>
        <td>5</td>
    </tr>
    <tr>
        <td>MILLER</td>
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>1300.00</td>
        <td>2</td>
    </tr>
    <tr>
        <td>SMITH</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>800.00</td>
        <td>1</td>
    </tr>
    <tr>
        <td>JONES</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>2975.00</td>
        <td>4</td>
    </tr>
    <tr>
        <td>SCOTT</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>3000.00</td>
        <td>4</td>
    </tr>
    <tr>
        <td>ADAMS</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>1100.00</td>
        <td>1</td>
    </tr>
    <tr>
        <td>FORD</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>3000.00</td>
        <td>4</td>
    </tr>
    <tr>
        <td>ALLEN</td>
        <td>30</td>
        <td>SALES</td>
        <td>1600.00</td>
        <td>3</td>
    </tr>
    <tr>
        <td>WARD</td>
        <td>30</td>
        <td>SALES</td>
        <td>1250.00</td>
        <td>2</td>
    </tr>
    <tr>
        <td>MARTIN</td>
        <td>30</td>
        <td>SALES</td>
        <td>1250.00</td>
        <td>2</td>
    </tr>
    <tr>
        <td>BLAKE</td>
        <td>30</td>
        <td>SALES</td>
        <td>2850.00</td>
        <td>4</td>
    </tr>
    <tr>
        <td>TURNER</td>
        <td>30</td>
        <td>SALES</td>
        <td>1500.00</td>
        <td>3</td>
    </tr>
    <tr>
        <td>JAMES</td>
        <td>30</td>
        <td>SALES</td>
        <td>950.00</td>
        <td>1</td>
    </tr>
</table>



#### 93. List the emp name, job, sal, grade and dname except clerks and sort on the basis of highest sal.


```python
%%sql
select e.ename,e.job,e.sal,g.grade,d.dname from emp e,dept d,salgrade g where e.deptno=d.deptno and  e.sal between g.losal and g.hisal
and e.job not in ("clerk") order by e.sal desc
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    10 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>job</th>
        <th>sal</th>
        <th>grade</th>
        <th>dname</th>
    </tr>
    <tr>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>5000.00</td>
        <td>5</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>3000.00</td>
        <td>4</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>3000.00</td>
        <td>4</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>2975.00</td>
        <td>4</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>2850.00</td>
        <td>4</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>2450.00</td>
        <td>4</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>ALLEN</td>
        <td>SALESMAN</td>
        <td>1600.00</td>
        <td>3</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>TURNER</td>
        <td>SALESMAN</td>
        <td>1500.00</td>
        <td>3</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>WARD</td>
        <td>SALESMAN</td>
        <td>1250.00</td>
        <td>2</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>MARTIN</td>
        <td>SALESMAN</td>
        <td>1250.00</td>
        <td>2</td>
        <td>SALES</td>
    </tr>
</table>



#### 94. List the emps name, job who are with out manager.


```python
%%sql
select * from emp e where e.mgr is null
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>PRESIDENT</td>
        <td>None</td>
        <td>1981-11-07</td>
        <td>5000.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
</table>



#### 95. List the names of the emps who are getting the highest sal dept wise.


```python
%%sql
select e1.ename,e1.deptno,max(e1.sal)as MaxSal from emp e1 group by e1.deptno
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>deptno</th>
        <th>MaxSal</th>
    </tr>
    <tr>
        <td>CLARK</td>
        <td>10</td>
        <td>5000.00</td>
    </tr>
    <tr>
        <td>SMITH</td>
        <td>20</td>
        <td>3000.00</td>
    </tr>
    <tr>
        <td>ALLEN</td>
        <td>30</td>
        <td>2850.00</td>
    </tr>
</table>



#### 96. List the emps whose sal is equal to the average of max and minimum


```python
%%sql
select * from emp e where e.sal=(select (max(e.sal)+min(e.sal))/2 from emp e)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    0 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
</table>



#### 97. List the no. of emps in each department where the no. is more than 3.


```python
%%sql
select e.deptno,count(*) from emp e group by e.deptno having 3<(count(*))
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>deptno</th>
        <th>count(*)</th>
    </tr>
    <tr>
        <td>20</td>
        <td>5</td>
    </tr>
    <tr>
        <td>30</td>
        <td>6</td>
    </tr>
</table>



#### 98. List the names of depts. Where atleast 3 are working in that department.


```python
%%sql
select d.dname,count(*) from dept d,emp e where d.deptno=e.deptno group by e.deptno having 3<=(select count(*) from emp e)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>dname</th>
        <th>count(*)</th>
    </tr>
    <tr>
        <td>ACCOUNTING</td>
        <td>3</td>
    </tr>
    <tr>
        <td>RESEARCH</td>
        <td>5</td>
    </tr>
    <tr>
        <td>SALES</td>
        <td>6</td>
    </tr>
</table>



#### 99. List the managers whose sal is more than his employess avg salary.


```python
%%sql
select * from emp e where e.job="manager" and e.sal > (select avg( e1.sal) from emp e1 where e1.mgr=e.empno)group by e.deptno
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>mgr</th>
        <th>hiredate</th>
        <th>sal</th>
        <th>comm</th>
        <th>deptno</th>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
        <td>None</td>
        <td>10</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>7839</td>
        <td>1981-05-01</td>
        <td>2850.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
</table>



#### 100. List the name,salary,comm. For those employees whose net pay is greater than or equal to any other employee salary of the company.


```python
%%sql
select e.ename,e.sal,e.comm from emp e where (e.sal+e.comm)>=any(select e1.sal from emp e1)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    4 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>sal</th>
        <th>comm</th>
    </tr>
    <tr>
        <td>ALLEN</td>
        <td>1600.00</td>
        <td>300.00</td>
    </tr>
    <tr>
        <td>WARD</td>
        <td>1250.00</td>
        <td>500.00</td>
    </tr>
    <tr>
        <td>MARTIN</td>
        <td>1250.00</td>
        <td>1400.00</td>
    </tr>
    <tr>
        <td>TURNER</td>
        <td>1500.00</td>
        <td>0.00</td>
    </tr>
</table>




```python

```
