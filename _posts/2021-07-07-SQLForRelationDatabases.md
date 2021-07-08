---
layout: post
title: SQL for Relation Databases
---

For practicing the SQL commands lets take the Boat Reservation Database from **Database Management Systems by Raghu Ramamkrishna**.
<br>
This example consists of 3 tables : **Sailors**,**Boats** and **Reserves**
<br>
**Q1) Find the names and ages of all sailors.
Q2) Find all sailors with a rating above 7.
Q3) Find the names of sailors who have reserved boat number 103.
Q4) Find the names of sailors who have reserved a Red boat.
Q5) Find the colors of boats reserved by Lubber.
Q6) Find the names of sailors who have reserved at least one boat.
Q7) Compute increments for the ratings of persons who have sailed two different boats on the same day.
Q8) Find the ages of sailors whose name begins and ends with B and has at least three characters.
Q9) Find the names of sailors who have reserved a red or a green boat.
Q10) Find the names of sailor's who have reserved both a red and a green boat.
Q11) Find the sids of all sailor's who have reserved red boats but not green
boats.
Q12) Find all sids of sailors who have a rating of 10 or reserved boat 104.
Nested Quires
Q13) Find the names of sailors who have reserved boat 103.
Q14) Find the names of sailors who have reserved a red boat.
Q15) Find the names of sailors who have not reserved a red boat.
Correlational Queries
Q16) Find the names of sailors who have reserved boat number 103.
Q17) Find sailors whose rating is better than some sailor called Horatio.
Q18) Find sailors whose rating is better than every sailor' called Horatito.
Q19) Find the sailor's with the highest rating.
More Nested
Q20) Find the names of sailors who have reserved both a red and a green boat.
Q21) Find the names of sailors who have reserved all boats.**

## AGGREGATE OPERATORS
**Q22) Find the average age of all sailors.
Q23) Find the average age of sailors with a rating of 10.
Q24) Find the name and age of the oldest sailor.
Q25) Count the number of sailor.
Q26) Count the number of different sailor names
Q27) Find the names of sailors who are older than the oldest sailor with a
rating of 10.**
The GROUP BY and HAVING Clauses
**Q28) Find the age of the youngest sailor for each rating level.
Q29) Find the age of the youngest sailor who is eligible to vote (i.e., is at least 18 years old) for each rating level with at least two such sailors.
More Examples of Aggregate Queries
Q30) For each red boat; find the number of reservations for this boat.
Q31) Find the average age of sailors for each rating level that has at least two
sailors.
Q32) a.  Find the average age of sailors who are of voting age (i.e., at least 18
years old) for each rating level that has at least two sailors
b. Find the average age of sailors who are of voting age (i.e., at least 18
years old) for each rating level that has at least two such sailors
Q33) Find those ratings for which the average age of sailors is the minimum
over all ratings.**
## COMPLEX INTEGRITY CONSTRAINTS IN SQL
**Q34) to ensure that rating must be an integer in the range 1 to 10,
Q35) a new domain using the CREATE DOMAIN statement, which
uses CHECK constraints.**
## Assertions: ICs over Several Tables
**Q36) to enforce the constraint that the number
of boats plus the number of sailors should be less than 100. (This condition
Illight be required, say, to qualify as a 'smaIl' sailing club.)**

## Examples of Triggers in SQL
