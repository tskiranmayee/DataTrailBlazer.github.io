---
layout: post
title: SQL Practice - Oracle Emp Table SQL Queires 1-50
---
```python
import sqlalchemy
```

#### Replace ***** with your MySql Password


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
    

#### Replace ***** with your MySql Password


```python
%sql "mysql+mysqldb://root:****@localhost:3306/oracle_emp"
```

### 1. Display all the information of the EMP table?


```python
%%sql
select * from emp;
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



### 2. Display unique Jobs from EMP table?



```python
%%sql
select distinct(job) from emp;
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>job</th>
    </tr>
    <tr>
        <td>CLERK</td>
    </tr>
    <tr>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>MANAGER</td>
    </tr>
    <tr>
        <td>ANALYST</td>
    </tr>
    <tr>
        <td>PRESIDENT</td>
    </tr>
</table>



### 3.List the emps in the asc order of their Salaries?


```python
%%sql
select ename,sal from emp order by sal asc 
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>sal</th>
    </tr>
    <tr>
        <td>SMITH</td>
        <td>800.00</td>
    </tr>
    <tr>
        <td>JAMES</td>
        <td>950.00</td>
    </tr>
    <tr>
        <td>ADAMS</td>
        <td>1100.00</td>
    </tr>
    <tr>
        <td>WARD</td>
        <td>1250.00</td>
    </tr>
    <tr>
        <td>MARTIN</td>
        <td>1250.00</td>
    </tr>
    <tr>
        <td>MILLER</td>
        <td>1300.00</td>
    </tr>
    <tr>
        <td>TURNER</td>
        <td>1500.00</td>
    </tr>
    <tr>
        <td>ALLEN</td>
        <td>1600.00</td>
    </tr>
    <tr>
        <td>CLARK</td>
        <td>2450.00</td>
    </tr>
    <tr>
        <td>BLAKE</td>
        <td>2850.00</td>
    </tr>
    <tr>
        <td>JONES</td>
        <td>2975.00</td>
    </tr>
    <tr>
        <td>SCOTT</td>
        <td>3000.00</td>
    </tr>
    <tr>
        <td>FORD</td>
        <td>3000.00</td>
    </tr>
    <tr>
        <td>KING</td>
        <td>5000.00</td>
    </tr>
</table>



### 4. List the details of the emps in asc order of the Dptnos and desc of Jobs?


```python
%%sql
select ename,deptno,job from emp order by deptno asc,job desc;
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>deptno</th>
        <th>job</th>
    </tr>
    <tr>
        <td>KING</td>
        <td>10</td>
        <td>PRESIDENT</td>
    </tr>
    <tr>
        <td>CLARK</td>
        <td>10</td>
        <td>MANAGER</td>
    </tr>
    <tr>
        <td>MILLER</td>
        <td>10</td>
        <td>CLERK</td>
    </tr>
    <tr>
        <td>JONES</td>
        <td>20</td>
        <td>MANAGER</td>
    </tr>
    <tr>
        <td>SMITH</td>
        <td>20</td>
        <td>CLERK</td>
    </tr>
    <tr>
        <td>ADAMS</td>
        <td>20</td>
        <td>CLERK</td>
    </tr>
    <tr>
        <td>SCOTT</td>
        <td>20</td>
        <td>ANALYST</td>
    </tr>
    <tr>
        <td>FORD</td>
        <td>20</td>
        <td>ANALYST</td>
    </tr>
    <tr>
        <td>ALLEN</td>
        <td>30</td>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>WARD</td>
        <td>30</td>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>MARTIN</td>
        <td>30</td>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>TURNER</td>
        <td>30</td>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>BLAKE</td>
        <td>30</td>
        <td>MANAGER</td>
    </tr>
    <tr>
        <td>JAMES</td>
        <td>30</td>
        <td>CLERK</td>
    </tr>
</table>



### 5.Display all the unique job groups in the descending order?


```python
%%sql
select job from emp group by job order by job desc
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>job</th>
    </tr>
    <tr>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>PRESIDENT</td>
    </tr>
    <tr>
        <td>MANAGER</td>
    </tr>
    <tr>
        <td>CLERK</td>
    </tr>
    <tr>
        <td>ANALYST</td>
    </tr>
</table>



### 6. Display all the details of all ‘Mgrs’


```python
%%sql
select * from emp where job="Manager"
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



### 7.List the emps who joined before 1981.


```python
%%sql
select * from emp where hiredate<"1981-01-01"
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
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



### 8. List the Empno, Ename, Sal, Daily sal of all emps in the asc order of Annsal


```python
%%sql
select empno,ename,sal,sal/30 as dailysal,sal*12 as annualsal  from emp order by annualsal desc
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>sal</th>
        <th>dailysal</th>
        <th>annualsal</th>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>5000.00</td>
        <td>166.666667</td>
        <td>60000.00</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>3000.00</td>
        <td>100.000000</td>
        <td>36000.00</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>3000.00</td>
        <td>100.000000</td>
        <td>36000.00</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>2975.00</td>
        <td>99.166667</td>
        <td>35700.00</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>2850.00</td>
        <td>95.000000</td>
        <td>34200.00</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>2450.00</td>
        <td>81.666667</td>
        <td>29400.00</td>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>1600.00</td>
        <td>53.333333</td>
        <td>19200.00</td>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>1500.00</td>
        <td>50.000000</td>
        <td>18000.00</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>1300.00</td>
        <td>43.333333</td>
        <td>15600.00</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>1250.00</td>
        <td>41.666667</td>
        <td>15000.00</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>1250.00</td>
        <td>41.666667</td>
        <td>15000.00</td>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>1100.00</td>
        <td>36.666667</td>
        <td>13200.00</td>
    </tr>
    <tr>
        <td>7900</td>
        <td>JAMES</td>
        <td>950.00</td>
        <td>31.666667</td>
        <td>11400.00</td>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>800.00</td>
        <td>26.666667</td>
        <td>9600.00</td>
    </tr>
</table>



### 9. Display the Empno, Ename, job, Hiredate, Exp of all Mgrs


```python
%%sql
select empno,ename,job,hiredate,floor(datediff(curdate(),hiredate)/365) as exp from emp where job="Manager"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>job</th>
        <th>hiredate</th>
        <th>exp</th>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>1981-04-02</td>
        <td>40</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>1981-05-01</td>
        <td>40</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>1981-06-09</td>
        <td>40</td>
    </tr>
</table>



### 10. List the Empno, Ename, Sal, Exp of all emps working for Mgr 7698.


```python
%%sql
select empno,ename,sal,floor(datediff(curdate(),hiredate)/365) as exp,mgr from emp where mgr=7698;
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>sal</th>
        <th>exp</th>
        <th>mgr</th>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>1600.00</td>
        <td>40</td>
        <td>7698</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>1250.00</td>
        <td>40</td>
        <td>7698</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>1250.00</td>
        <td>39</td>
        <td>7698</td>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>1500.00</td>
        <td>39</td>
        <td>7698</td>
    </tr>
    <tr>
        <td>7900</td>
        <td>JAMES</td>
        <td>950.00</td>
        <td>39</td>
        <td>7698</td>
    </tr>
</table>



### 11. Display all the details of the emps whose Comm. Is more than their Sal.


```python
%%sql
select * from emp e where e.comm>e.sal
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
        <td>7654</td>
        <td>MARTIN</td>
        <td>SALESMAN</td>
        <td>7698</td>
        <td>1981-09-28</td>
        <td>1250.00</td>
        <td>1400.00</td>
        <td>30</td>
    </tr>
</table>



### 12. List the emps in the asc order of Designations of those joined after the second half of 1981.


```python
%%sql
select * from emp where hiredate between "1981-07-01"and "1981-12-31" order by job asc;
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



### 13. List the emps along with their Exp and Daily Sal is more than Rs.100.


```python
%%sql 
select *,sal/30 as dailysal,floor(datediff(curdate(),hiredate)/365) as exp from emp where (sal/30)>100
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
        <th>dailysal</th>
        <th>exp</th>
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
        <td>166.666667</td>
        <td>39</td>
    </tr>
</table>



### 14. List the emps who are either ‘CLERK’ or ‘ANALYST’ in the Desc order.


```python
%%sql
select * from emp where job like "clerk" or job like "analyst" order by job desc
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
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
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



### 15. List the emps who joined on 1-MAY-81,3-DEC-81,17-DEC-81,19-JAN-80 in asc order of seniority.


```python
%%sql
select * from emp where hiredate in ("1981-05-01", "1981-12-03" ,"1981-12-17" , "1980-01-19")
order by datediff(curdate(),hiredate) desc
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
</table>



### 16.List the emp who are working for the Deptno 10 or 20.


```python
%%sql
select * from emp where deptno in (10,20)
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
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
        <td>None</td>
        <td>10</td>
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



### 17.List the emps who are joined in the year 81.


```python
%%sql
select * from emp where 1981=extract(year from hiredate)
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
</table>



### 18. List the emps who are joined in the month of Sep 1981.


```python
%%sql
select * from emp where 09=extract(month from hiredate) and 1981=extract(year from hiredate)
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



### 19. List the emps Who Annual sal ranging from 22000 and 45000.


```python
%%sql
select *,sal*12 as annualsal from emp where sal*12  between 22000 and 45000 order by annualsal asc

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
        <th>annualsal</th>
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
        <td>29400.00</td>
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
        <td>34200.00</td>
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
        <td>35700.00</td>
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
        <td>36000.00</td>
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
        <td>36000.00</td>
    </tr>
</table>



### 20.List the Enames those are having five characters in their Names.

###### Answer 1


```python
%%sql
select ename from emp where ename like "_____"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    8 rows affected.
    




<table>
    <tr>
        <th>ename</th>
    </tr>
    <tr>
        <td>SMITH</td>
    </tr>
    <tr>
        <td>ALLEN</td>
    </tr>
    <tr>
        <td>JONES</td>
    </tr>
    <tr>
        <td>BLAKE</td>
    </tr>
    <tr>
        <td>CLARK</td>
    </tr>
    <tr>
        <td>SCOTT</td>
    </tr>
    <tr>
        <td>ADAMS</td>
    </tr>
    <tr>
        <td>JAMES</td>
    </tr>
</table>



###### Answer 2


```python
%%sql
select ename from emp where length(ename)=5
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    8 rows affected.
    




<table>
    <tr>
        <th>ename</th>
    </tr>
    <tr>
        <td>SMITH</td>
    </tr>
    <tr>
        <td>ALLEN</td>
    </tr>
    <tr>
        <td>JONES</td>
    </tr>
    <tr>
        <td>BLAKE</td>
    </tr>
    <tr>
        <td>CLARK</td>
    </tr>
    <tr>
        <td>SCOTT</td>
    </tr>
    <tr>
        <td>ADAMS</td>
    </tr>
    <tr>
        <td>JAMES</td>
    </tr>
</table>



### 21. List the Enames those are starting with ‘S’ and with five characters.




##### Answer 1


```python
%%sql
select ename from emp where ename like "s%" and length(ename)=5
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>ename</th>
    </tr>
    <tr>
        <td>SMITH</td>
    </tr>
    <tr>
        <td>SCOTT</td>
    </tr>
</table>



##### Answer 2


```python
%%sql
select ename from emp where ename like "s____"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>ename</th>
    </tr>
    <tr>
        <td>SMITH</td>
    </tr>
    <tr>
        <td>SCOTT</td>
    </tr>
</table>



### 22. List the emps those are having four chars and third character must be ‘r’.



```python
%%sql
select ename from emp where ename like "__r_";
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>ename</th>
    </tr>
    <tr>
        <td>WARD</td>
    </tr>
    <tr>
        <td>FORD</td>
    </tr>
</table>




### 23. List the Five character names starting with ‘S’ and ending with ‘H’.




```python
%%sql
select ename from emp where ename like "s___h";
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>ename</th>
    </tr>
    <tr>
        <td>SMITH</td>
    </tr>
</table>



### 24. List the emps who joined in January.




```python
%%sql
select ename,hiredate from emp where 01=extract(month from hiredate);
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>hiredate</th>
    </tr>
    <tr>
        <td>MILLER</td>
        <td>1982-01-23</td>
    </tr>
</table>



### 25. List the emps who joined in the month of which second character is ‘a’.




```python
%%sql
select *, monthname(hiredate) from emp where monthname(hiredate) like "_a%";
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
        <th>monthname(hiredate)</th>
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
        <td>May</td>
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
        <td>January</td>
    </tr>
</table>



### 26. List the emps whose Sal is four digit number ending with Zero.




```python
%%sql
select * from emp where length(floor(sal))=4 and mod(floor(sal),10)=0;
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    11 rows affected.
    




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



### 27. List the emps whose names having a character set ‘ll’ together.




```python
%%sql
select * from emp where ename like "%ll%";
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



### 28. List the emps those who joined in 80’s.




```python
%%sql
select * from emp where 
```

### 29. List the emps who does not belong to Deptno 20.




```python
%%sql
select * from emp where deptno<>20
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    9 rows affected.
    




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
        <td>7934</td>
        <td>MILLER</td>
        <td>CLERK</td>
        <td>7782</td>
        <td>1982-01-23</td>
        <td>1300.00</td>
        <td>None</td>
        <td>10</td>
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
        <td>7900</td>
        <td>JAMES</td>
        <td>CLERK</td>
        <td>7698</td>
        <td>1981-12-03</td>
        <td>950.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
</table>



### 30. List all the emps except ‘PRESIDENT’ & ‘MGR” in asc order of Salaries.


```python
%%sql
select * from emp where job not like "president" and job not like "Manager"  order by sal asc
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



### 31. List all the emps who joined before or after 1981.


```python
%%sql
select * from emp where extract(year from hiredate)>1981 or extract(year from hiredate)<1981 
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



### 32.List the emps whose Empno not starting with digit 78.


```python
%%sql
select * from emp where empno not like "78%"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    11 rows affected.
    




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



### 33. List the emps who are working under ‘MGR’.


```python
%%sql
select e.ename from emp e where e.mgr in (select empno from emp where job="Manager")
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    8 rows affected.
    




<table>
    <tr>
        <th>ename</th>
    </tr>
    <tr>
        <td>ALLEN</td>
    </tr>
    <tr>
        <td>WARD</td>
    </tr>
    <tr>
        <td>MARTIN</td>
    </tr>
    <tr>
        <td>SCOTT</td>
    </tr>
    <tr>
        <td>TURNER</td>
    </tr>
    <tr>
        <td>JAMES</td>
    </tr>
    <tr>
        <td>FORD</td>
    </tr>
    <tr>
        <td>MILLER</td>
    </tr>
</table>



### 34. List the emps who joined in any year but not belongs to the month of December.


```python
%%sql
select * from emp where monthname(hiredate) not like "December"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    11 rows affected.
    




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



### 35. List all the Clerks of Deptno 20.


```python
%%sql
select * from emp where job="clerk" and deptno=20
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



### 36.List the emps of Deptno 30 or 10 joined in the year 1981.


```python
%%sql
select * from emp where deptno=30 or deptno=10 and 1981=extract(year from hiredate)
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
        <td>7900</td>
        <td>JAMES</td>
        <td>CLERK</td>
        <td>7698</td>
        <td>1981-12-03</td>
        <td>950.00</td>
        <td>None</td>
        <td>30</td>
    </tr>
</table>



### 37. Display the details of SMITH.


```python
%%sql
select * from emp where ename like "smith"
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
        <td>7369</td>
        <td>SMITH</td>
        <td>CLERK</td>
        <td>7902</td>
        <td>1980-12-17</td>
        <td>800.00</td>
        <td>None</td>
        <td>20</td>
    </tr>
</table>



### 38. Display the location of SMITH.


```python
%%sql
select e.ename,d.deptno,d.loc from emp e,dept d where e.deptno=d.deptno and e.ename="smith"
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    1 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>deptno</th>
        <th>loc</th>
    </tr>
    <tr>
        <td>SMITH</td>
        <td>20</td>
        <td>DALLAS</td>
    </tr>
</table>



### 39. List the total information of EMP table along with DNAME and Loc of all the emps Working Under ‘ACCOUNTING’ & ‘RESEARCH’ in the asc Deptno.


```python
%%sql
select  * from emp e,dept d where e.deptno=d.deptno and d.dname in ("Accounting","research") order by e.deptno asc;
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
        <th>deptno_1</th>
        <th>dname</th>
        <th>loc</th>
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
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>NEW YORK</td>
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
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>NEW YORK</td>
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
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>NEW YORK</td>
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
        <td>20</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
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
        <td>20</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
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
        <td>20</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
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
        <td>20</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
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
        <td>20</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
    </tr>
</table>



### 40. List the Empno, Ename, Sal, Dname of all the ‘MGRS’ and ‘ANALYST’ working in New York, Dallas 
### with an exp more than 37 years without receiving the Comm asc order of Loc.


```python
%%sql
select e.hiredate,e.empno,e.ename,e.sal,e.job,floor(datediff(curdate(),e.hiredate)/365) as yearsExp,d.dname,d.loc from emp e,dept d where e.job in("Manager","Analyst") and e.deptno=d.deptno and d.loc in("New York","Dallas")
and e.comm is null and 37<floor(datediff(curdate(),e.hiredate)/365)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    3 rows affected.
    




<table>
    <tr>
        <th>hiredate</th>
        <th>empno</th>
        <th>ename</th>
        <th>sal</th>
        <th>job</th>
        <th>yearsExp</th>
        <th>dname</th>
        <th>loc</th>
    </tr>
    <tr>
        <td>1981-04-02</td>
        <td>7566</td>
        <td>JONES</td>
        <td>2975.00</td>
        <td>MANAGER</td>
        <td>40</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
    </tr>
    <tr>
        <td>1981-06-09</td>
        <td>7782</td>
        <td>CLARK</td>
        <td>2450.00</td>
        <td>MANAGER</td>
        <td>40</td>
        <td>ACCOUNTING</td>
        <td>NEW YORK</td>
    </tr>
    <tr>
        <td>1981-12-03</td>
        <td>7902</td>
        <td>FORD</td>
        <td>3000.00</td>
        <td>ANALYST</td>
        <td>39</td>
        <td>RESEARCH</td>
        <td>DALLAS</td>
    </tr>
</table>



### 41. Display the Empno, Ename, Sal, Dname, Loc, Deptno, Job of all emps working at CHICAGO or working for ACCOUNTING dept with Ann Sal>28000, but the Sal should not be=3000 or 2800 who doesn’t belongs to the Mgr and whose no is having a digit ‘7’ or ‘8’ in 3rd position in the asc order of Deptno and desc order of job.


```python
%%sql
select e.empno,e.ename,e.sal,d.dname,d.loc,e.deptno,e.job from emp e,dept d where e.deptno=d.deptno
and d.loc="chicago" or d.dname="accounting" and sal*12 >28000 and sal not in(3000,2800) and e.job not like "manager" 
and (e.empno like '__7%' or '__8%' ) order by e.deptno asc,e.job desc
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    6 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>sal</th>
        <th>dname</th>
        <th>loc</th>
        <th>deptno</th>
        <th>job</th>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>1600.00</td>
        <td>SALES</td>
        <td>CHICAGO</td>
        <td>30</td>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>1250.00</td>
        <td>SALES</td>
        <td>CHICAGO</td>
        <td>30</td>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>1250.00</td>
        <td>SALES</td>
        <td>CHICAGO</td>
        <td>30</td>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>1500.00</td>
        <td>SALES</td>
        <td>CHICAGO</td>
        <td>30</td>
        <td>SALESMAN</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>2850.00</td>
        <td>SALES</td>
        <td>CHICAGO</td>
        <td>30</td>
        <td>MANAGER</td>
    </tr>
    <tr>
        <td>7900</td>
        <td>JAMES</td>
        <td>950.00</td>
        <td>SALES</td>
        <td>CHICAGO</td>
        <td>30</td>
        <td>CLERK</td>
    </tr>
</table>



### 42. Display the total information of the emps along with Grades in the asc order.


```python
%%sql
select * from emp e, salgrade s,bonus b where 
```

### 43. List all the Grade 2 and Grade 3 emps.


```python
%%sql
select e.ename,e.sal,g.grade from emp e,salgrade g where e.sal between g.losal and g.hisal and g.grade in (2,3)
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>sal</th>
        <th>grade</th>
    </tr>
    <tr>
        <td>ALLEN</td>
        <td>1600.00</td>
        <td>3</td>
    </tr>
    <tr>
        <td>WARD</td>
        <td>1250.00</td>
        <td>2</td>
    </tr>
    <tr>
        <td>MARTIN</td>
        <td>1250.00</td>
        <td>2</td>
    </tr>
    <tr>
        <td>TURNER</td>
        <td>1500.00</td>
        <td>3</td>
    </tr>
    <tr>
        <td>MILLER</td>
        <td>1300.00</td>
        <td>2</td>
    </tr>
</table>



### 44. Display all Grade 4,5 Analyst and Mgr.


```python
%%sql
select e.ename,e.job,g.grade from emp e, salgrade g where e.sal between g.losal and g.hisal and e.job in ("Analyst","Manager")
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    5 rows affected.
    




<table>
    <tr>
        <th>ename</th>
        <th>job</th>
        <th>grade</th>
    </tr>
    <tr>
        <td>FORD</td>
        <td>ANALYST</td>
        <td>4</td>
    </tr>
    <tr>
        <td>SCOTT</td>
        <td>ANALYST</td>
        <td>4</td>
    </tr>
    <tr>
        <td>CLARK</td>
        <td>MANAGER</td>
        <td>4</td>
    </tr>
    <tr>
        <td>BLAKE</td>
        <td>MANAGER</td>
        <td>4</td>
    </tr>
    <tr>
        <td>JONES</td>
        <td>MANAGER</td>
        <td>4</td>
    </tr>
</table>



### 45. List the Empno, Ename, Sal, Dname, Grade, Exp, and Ann Sal of emps working for Dept10 or20.


```python
%%sql
select e.empno,e.ename,e.sal,d.deptno,d.dname,g.grade,floor((datediff(curdate(),e.hiredate))/365) as exp,sal*12 as annulaSal 
from emp e,dept d,salgrade g where e.deptno in(10,20) and e.deptno=d.deptno and e.sal between g.losal and g.hisal 
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    8 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>sal</th>
        <th>deptno</th>
        <th>dname</th>
        <th>grade</th>
        <th>exp</th>
        <th>annulaSal</th>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>1100.00</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>1</td>
        <td>34</td>
        <td>13200.00</td>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>800.00</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>1</td>
        <td>40</td>
        <td>9600.00</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>1300.00</td>
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>2</td>
        <td>39</td>
        <td>15600.00</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>3000.00</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>4</td>
        <td>39</td>
        <td>36000.00</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>3000.00</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>4</td>
        <td>34</td>
        <td>36000.00</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>2975.00</td>
        <td>20</td>
        <td>RESEARCH</td>
        <td>4</td>
        <td>40</td>
        <td>35700.00</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>2450.00</td>
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>4</td>
        <td>40</td>
        <td>29400.00</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>5000.00</td>
        <td>10</td>
        <td>ACCOUNTING</td>
        <td>5</td>
        <td>39</td>
        <td>60000.00</td>
    </tr>
</table>



### 46. List all the information of emp with Loc  and the Grade of all the emps belong to the Grade range from 2 to 4 working at the Dept those are not starting with char set ‘OP’ and not ending with ‘S’ with the designation having a char ‘a’ any where joined in the year 1981 but not in the month of Mar or Sep and Sal not end with ‘00’ in the asc order of Grades


```python
%%sql
select e.empno,d.loc,g.grade,d.dname,e.hiredate,e.sal from emp e,dept d,salgrade g where e.sal between g.losal and g.hisal and g.grade between 2 and 4 and e.deptno=d.deptno
and d.dname not like "op%" and d.dname not like "%s" and e.job like "%a%" and 1981=extract(year from e.hiredate) and monthname(e.hiredate)<>"March" and monthname(e.hiredate)<>"September"
and e.sal%100<>00 order by g.grade asc
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    2 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>loc</th>
        <th>grade</th>
        <th>dname</th>
        <th>hiredate</th>
        <th>sal</th>
    </tr>
    <tr>
        <td>7566</td>
        <td>DALLAS</td>
        <td>4</td>
        <td>RESEARCH</td>
        <td>1981-04-02</td>
        <td>2975.00</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>NEW YORK</td>
        <td>4</td>
        <td>ACCOUNTING</td>
        <td>1981-06-09</td>
        <td>2450.00</td>
    </tr>
</table>



### 47. List the details of the Depts along with Empno, Ename without using joins


```python
%%sql
SELECT e.empno,e.ename, (SELECT dname FROM dept d WHERE d.deptno=e.deptno)dname
FROM emp e
```

     * mysql+mysqldb://root:***@localhost:3306/oracle_emp
    14 rows affected.
    




<table>
    <tr>
        <th>empno</th>
        <th>ename</th>
        <th>dname</th>
    </tr>
    <tr>
        <td>7369</td>
        <td>SMITH</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7499</td>
        <td>ALLEN</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7521</td>
        <td>WARD</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7566</td>
        <td>JONES</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7654</td>
        <td>MARTIN</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7698</td>
        <td>BLAKE</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7782</td>
        <td>CLARK</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>7788</td>
        <td>SCOTT</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7839</td>
        <td>KING</td>
        <td>ACCOUNTING</td>
    </tr>
    <tr>
        <td>7844</td>
        <td>TURNER</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7876</td>
        <td>ADAMS</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7900</td>
        <td>JAMES</td>
        <td>SALES</td>
    </tr>
    <tr>
        <td>7902</td>
        <td>FORD</td>
        <td>RESEARCH</td>
    </tr>
    <tr>
        <td>7934</td>
        <td>MILLER</td>
        <td>ACCOUNTING</td>
    </tr>
</table>



### 48. List the details of the emps whose Salaries more than the employee BLAKE.


```python
%%sql
select * from emp e where e.sal>(select b.sal from emp b where b.ename="blake")

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



### 49. List the emps whose Jobs are same as ALLEN and donot display ALLEN details.


```python
%%sql
select * from emp e where e.job=(select a.job from emp a where a.ename="Allen") and e.ename not like "Allen"
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



### 50.List the emps who are senior to King.


```python
%%sql
select *,(datediff(curdate(),hiredate)/365) as exp from emp e where (datediff(curdate(),hiredate)/365)>(select (datediff(curdate(),hiredate)/365) from emp k where k.ename like "King")
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
        <th>exp</th>
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
        <td>40.6192</td>
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
        <td>40.4411</td>
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
        <td>40.4356</td>
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
        <td>40.3288</td>
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
        <td>39.8384</td>
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
        <td>40.2493</td>
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
        <td>40.1425</td>
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
        <td>39.8932</td>
    </tr>
</table>




```python

```
