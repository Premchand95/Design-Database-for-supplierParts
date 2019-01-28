# Design-Database-for-supplierParts

## Queries on supplierParts data base

* Show the full information for all Parts 

SELECT * FROM P;

PNO   | PNAME          |      COLOR | WEIGHT   |   CITY
------| -------------------- |------ |-----------| ---------------
P1  |   Nut       |           Red  |  12       |   London         
P2   |  Bolt      |           Green | 17       |   Paris          
P3   |  Screw     |           Blue  | 17      |    Oslo           
P4   |  Screw     |           Red   | 14       |   London         
P5   |  Cam       |           Blue  | 12        |  Paris          
P6   |  Cog       |           Red   | 19        |  London         

(6 rows affected)


* Show the supplier name and part name for orders for QTY greater than 300 (Using WHERE clauses)

SELECT SNAME,PNAME FROM S,P,SP WHERE QTY>300 AND S.SNO=SP.SNO AND P.PNO=SP.PNO;

SNAME          |      PNAME
--------------------| --------------------
Smith            |    Screw               
Jones              |  Bolt                
Clark              |  Cam                 

(3 rows affected)


* Show the supplier name and Part name for orders for QTY greater than 300 ( using JOIN ON with only one predicate in the WHERE clause)

SELECT S.SNAME,P.PNAME FROM SP JOIN S ON S.SNO=SP.SNO JOIN P ON P.PNO=SP.PNO WHERE QTY>300;

SNAME          |      PNAME
-------------------- |--------------------
Smith             |   Screw               
Jones              |   Bolt                
Clark              |  Cam                 

(3 rows affected)





* Show cities that have red parts 

SELECT DISTINCT P.CITY FROM SP INNER JOIN P ON P.PNO=SP.PNO WHERE COLOR='Red';

CITY |
--------------- |
London          |

(1 row affected)


* How many cities were there in query 4 above ?

SELECT COUNT(DISTINCT P.CITY) AS 'Number of cities that have red parts' FROM SP JOIN P ON P.PNO=SP.PNO WHERE COLOR='Red';

Number of cities that have red parts |
------------------------------------ |
1 |

(1 row affected)

* What is the total number of red parts shipped.

SELECT COUNT(*) AS 'Total number of parts shipped' FROM SP JOIN P ON P.PNO=SP.PNO WHERE COLOR='Red';

Total number of parts shipped |
----------------------------- |
5 |

(1 row affected)



 

